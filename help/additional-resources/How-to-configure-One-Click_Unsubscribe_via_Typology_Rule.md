---
source-git-commit: 25a1d799589268ab3108267670a3212bc9c47f7d
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 8%

---
### Création d’une règle de typologie pour la prise en charge du désabonnement à la liste en un clic :
###

**1. Créez la nouvelle règle de typologie :**
* Dans l’arborescence de navigation, cliquez sur &quot;Nouveau&quot; pour créer une typologie.

![Image.](/help/assets/CreatingTypologyRules1.png)

**2. Procédez à la configuration de la règle de typologie :**
* Type de règle : Contrôle
* Phase : au début du ciblage
* Canal : Email
* Niveau : votre choix
* Actif


![Image.](/help/assets/CreatingTypologyRules2.png)


**Code le javascript de la règle de typologie :**


>[!NOTE]
>
>Le code décrit ci-dessous doit être référencé à titre d’exemple uniquement.
>Cet exemple illustre comment :
>* Configurez une URL List-Unsubscribe et ajoutez les en-têtes ou ajoutez les paramètres mailto existants : et remplacez-le par : &lt;mailto..>>, https://...
>* Ajouter dans l’en-tête List-Unsubscribe-Post
>L’exemple d’URL de publication utilise var headerUnsubUrl = &quot;https://campmomentumv7-mkt-prod3.campaign.adobe.com/webApp/unsubNoClick?id=&lt;%= recipient.cryptedId %>&quot;÷
>* Vous pouvez ajouter d’autres paramètres (comme &amp;service = ...)
>


```
// Function to add or replace a header in the provided headers 
function addHeader(headers, header, value)  { 
    
  // Create the new header line 
  var headerLine = header + ": " + value; 
    
  // Create a regular expression to find the specified header 
  var regExp = new RegExp(header + ":(.*)$", "i") 
    
  // Split the headers into individual lines 
  var headerLines = headers.split("\n"); 
    
  // Loop through each line 
  for (var i=0; i < headerLines.length; i++) { 
      
    // Check if the specified header exists 
    var match = headerLines[i].match(regExp) 
      
    // If it exists 
    if ( match != null ) { 
        
      // Replace the existing header line 
      headerLines[i] = headerLine; 
        
      // Return the modified headers 
      return headerLines.join("\n"); 
    } 
  } 
    
  // If the header does not exist, add the new header line 
  headerLines.push(headerLine); 
    
  // Return the modified headers 
  return headerLines.join("\n"); 
} 
  
// Function to get the value of a specified header from the provided headers 
function getHeader(headers, header) { 
    
  // Create a regular expression to find the specified header 
  var regExp = new RegExp(header + ":(.*)$", "i") 
    
  // Split the headers into individual lines 
  var headerLines = headers.split("\n"); 
    
  // Loop each line 
  for each (line in headerLines) { 
      
    // Check if the specified header exists 
    var match = line.match(regExp); 
      
    // If it exists 
    if ( match != null ) { 
        
      // Return the header value, removing leading whitespace 
      return match[1].replace(/^\s*/, ""); 
    } 
  } 
    
  // If the header does not exist, return an empty string 
  return ""; 
} 
  
  
// Define the unsubscribe URL 
var headerUnsubUrl = "https://campmomentumv7-mkt-prod3.campaign.adobe.com/webApp/unsubNoClick?id=<%= recipient.cryptedId %>"; 
  
// Get the value of the List-Unsubscribe header 
var headerUnsub = getHeader(delivery.mailParameters.headers, "List-Unsubscribe"); 
  
// If the List-Unsubscribe header does not exist 
if ( headerUnsub === "" ) { 
  // Add the List-Unsubscribe header 
  delivery.mailParameters.headers = addHeader(delivery.mailParameters.headers, "List-Unsubscribe", "<"+headerUnsubUrl+">"); 
} 
// If the List-Unsubscribe header exists and contains 'mailto' 
else if(headerUnsub.search('mailto')){ 
  // Replace the existing List-Unsubscribe header 
  delivery.mailParameters.headers = addHeader(delivery.mailParameters.headers, "List-Unsubscribe", "<"+headerUnsubUrl+">"); 
} 
  
// Get the value of the List-Unsubscribe-Post header 
var headerUnsubPost = getHeader(delivery.mailParameters.headers, "List-Unsubscribe-Post"); 
  
// If the List-Unsubscribe-Post header does not exist 
if ( headerUnsubPost === "" ) { 
  // Add the List-Unsubscribe-Post header 
  delivery.mailParameters.headers = addHeader(delivery.mailParameters.headers, "List-Unsubscribe-Post", "List-Unsubscribe=One-Click"); 
} 
  
// Return true to indicate success 
return true; 
```


![Image.](/help/assets/CreatingTypologyRules3.png)

**3. Ajoutez votre nouvelle règle à une typologie à un email (la typologie par défaut est correcte) :**

![Image.](/help/assets/CreatingTypologyRules4.png)

**4. Préparer une nouvelle diffusion (vérifiez que les en-têtes SMTP supplémentaires dans la propriété de diffusion sont vides)**

![Image.](/help/assets/CreatingTypologyRules5.png)

**5. Vérifiez, lors de la préparation de la diffusion, que votre nouvelle règle de typologie est appliquée.**

![Image.](/help/assets/CreatingTypologyRules6.png)



**6. Vérifiez que le List-Unsubscribe est présent.**

![Image.](/help/assets/CreatingTypologyRules7.png)
