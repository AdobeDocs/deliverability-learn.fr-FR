---
title: 'Campaign Classic : recommandations techniques'
description: Découvrez les techniques, les configurations et les outils que vous pouvez utiliser pour améliorer votre taux de délivrabilité avec Adobe Campaign Classic.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 39ed3773-18bf-4653-93b6-ffc64546406b
TQID: https://experienceleague.adobe.com/Y58eIzSpKUV-B-MiQ-6KNkk31tg1M6Bg27ZqGv-DESc
product_v2: id: b27e5950-9033-45ac-9f86-eb22e567f615id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: b0bb9048-d951-48d8-8232-45cf248a7e27id: b3b8a63f-51fc-40f6-a7d2-a31c5d49fb45id: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: c5f60233-d5ea-4453-a799-0ad258b4d399id: d1d0a9cd-295d-4976-8c39-ddae266f240eid: e2290edd-b061-4880-9d79-dee306cf5aa9id: ea90ebee-5c84-42d9-8b21-006bdabc95a3id: f71e690b-4480-4b67-9ef5-88f42f9cdfdbid: f82558ea-6af5-44eb-a424-5b3389abb0a3id: fdbb8fc9-ffa3-4b86-88fe-aa4c5a3e1bc6
subfeature_v2: id: b75843fa-0a67-4a44-a6b1-cc627b0481dcid: e656c701-3899-4db3-989c-de0980ddfffaid: eff19c99-440a-4318-b319-444edc4d8d8f
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: cdd65e7e-8839-44a2-bc21-0e03623b5dd1id: d095671a-1355-40aa-8b5f-06c33c68080bid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 2232
ht-degree: 29%

---

# Campaign Classic : recommandations techniques {#technical-recommendations}

Vous trouverez ci-dessous plusieurs techniques, configurations et outils que vous pouvez utiliser pour améliorer votre taux de délivrabilité lors de l’utilisation de Adobe Campaign Classic.

## Configuration {#configuration}

### Reverse DNS {#reverse-dns}

Adobe Campaign vérifie qu’un reverse DNS est bien renseigné pour une adresse IP et que celui-ci reboucle bien sur l’IP.

Un point important de la configuration réseau est de s’assurer qu’un reverse DNS correct est défini pour chacune des adresses IP des messages sortants. Cela signifie que pour une adresse IP donnée, il existe un enregistrement DNS inversé (enregistrement PTR) avec un DNS correspondant (enregistrement A) qui reboucle sur l’adresse IP initiale.

Le choix du domaine pour un reverse DNS a une incidence lorsque vous traitez avec certains FAI. AOL, en particulier, n’accepte que les feedback loops dont l’adresse appartient au même domaine que le reverse DNS (voir la section [Feedback loop](#feedback-loop)).

>[!NOTE]
>
>Vous pouvez utiliser [cet outil externe](https://mxtoolbox.com/SuperTool.aspx) pour vérifier la configuration d’un domaine.

### Règles MX {#mx-rules}

Les règles MX (Mail eXchanger) correspondent aux règles de gestion de communication entre un serveur expéditeur et un serveur destinataire.

Plus précisément, ils sont utilisés pour contrôler la vitesse à laquelle le MTA (Message Transfer Agent) d&#39;Adobe Campaign envoie des e-mails à chaque domaine de messagerie ou FAI individuel (par exemple, hotmail.com, comcast.net). Ces règles sont généralement basées sur les limites publiées par les FAI (par exemple, n’incluez pas plus de 20 messages par connexion SMTP).

>[!NOTE]
>
>Pour plus d’informations sur la gestion des MX dans Adobe Campaign Classic, consultez [cette section](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/email-deliverability.html#mx-configuration).

### TLS {#tls}

(Transport Layer Security) est un protocole de cryptage qui peut être utilisé pour sécuriser la connexion entre deux serveurs de messagerie et empêcher la lecture du contenu d’un email par une autre personne que le destinataire prévu.

### Domaine de l&#39;expéditeur {#sender-domain}

Pour définir le domaine utilisé pour la commande HELO, modifiez le fichier de configuration de l’instance (conf/config-instance.xml) et définissez un attribut « localDomain » comme suit :

```
<serverConf>
  <shared>
    <dnsConfig localDomain="mydomain.net"/>
  </shared>
</serverConf>
```

Le domaine MAIL FROM est le domaine utilisé dans les messages de rebond techniques. Cette adresse est définie dans l&#39;assistant de déploiement ou via l&#39;option NmsEmail_DefaultErrorAddr .

### Enregistrement SPF {#dns-configuration}

Un enregistrement SPF peut actuellement être défini sur un serveur DNS comme un enregistrement de type TXT (code 16) ou un enregistrement de type SPF (code 99). Un enregistrement SPF se présente sous la forme d&#39;une chaîne de caractères. Par exemple :

```
v=spf1 ip4:12.34.56.78/32 ip4:12.34.56.79/32 ~all
```

définit les deux adresses IP, 12.34.56.78 et 12.34.56.79, comme autorisées à envoyer des e-mails pour le domaine. **~all** signifie que toute autre adresse doit être interprétée comme un SoftFail.

Recommandations pour définir un enregistrement SPF :

* Ajoutez **~all** (SoftFail) ou **-all** (Fail) à la fin pour rejeter tous les serveurs autres que ceux définis. Sans cela, les serveurs pourront forger ce domaine (avec une évaluation neutre).
* N’ajoutez pas le **ptr** (openspf.org recommande de ne pas l’ajouter car cela serait coûteux et peu fiable).

>[!NOTE]
>
>En savoir plus sur SPF dans [cette section](/help/additional-resources/authentication.md#spf).

## Authentification

>[!NOTE]
>
>Pour en savoir plus sur les différentes formes d’authentification des e-mails, consultez [cette section](/help/additional-resources/authentication.md).

### DKIM {#dkim-acc}

>[!NOTE]
>
>Pour les installations hébergées ou hybrides, si vous avez effectué une mise à niveau vers le [MTA amélioré](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/sending-an-email/sending-with-enhanced-mta.html#sending-messages), la signature de l’authentification des e-mails DKIM est effectuée par celui-ci pour tous les messages et domaines.

L&#39;utilisation de [](/help/additional-resources/authentication.md#dkim) avec Adobe Campaign Classic requiert la condition préalable suivante :

**déclaration d&#39;option Adobe Campaign** : dans Adobe Campaign, la clé privée DKIM repose sur un sélecteur DKIM et un domaine. Il n’est actuellement pas possible de créer plusieurs clés privées pour le même domaine/sous-domaine avec différents sélecteurs. Il n’est pas possible de définir quel domaine/sous-domaine de sélecteur doit être utilisé pour l’authentification dans la plateforme ou l’e-mail. La plateforme choisira également l’une des clés privées, ce qui signifie que l’authentification a un risque élevé d’échec.

* Si vous avez configuré DomainKeys pour votre instance Adobe Campaign, vous devez simplement sélectionner **dkim** dans les [règles de gestion des domaines](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html#email-management-rules). Dans le cas contraire, suivez les mêmes étapes de configuration (clé privée/publique) que pour DomainKeys (qui a remplacé DKIM).
* Il est inutile d&#39;activer DomainKeys et DKIM pour un même domaine, DKIM étant une version améliorée de DomainKeys.
* Les domaines validant actuellement DKIM sont les suivants : AOL, Gmail.

## Feedback loop {#feedback-loop-acc}

Une boucle de rétroaction fonctionne en déclarant au niveau du FAI une adresse e-mail donnée pour une plage d’adresses IP utilisées pour l’envoi des messages. Le FAI enverra à cette boîte aux lettres, de la même manière que pour les messages de rebond, les messages signalés par les destinataires comme spam. La plateforme doit être configurée de manière à bloquer les prochaines diffusions aux utilisateurs qui se sont plaints. Il est important de ne plus les contacter même s&#39;ils n&#39;ont pas utilisé le lien d&#39;opt-out approprié. C&#39;est en fonction de ces plaintes qu&#39;un FAI ajoutera une adresse IP à sa place sur la liste bloquée. Selon le FAI, un taux de plainte d’environ 1 % entraînera lle blocage d’une adresse IP.

Un standard est en cours d’établissement pour définir le format des messages de feedback loop : l’[ARF (Abuse Feedback Reporting Format)](https://tools.ietf.org/html/rfc6650).

La mise en place d&#39;une feedback loop pour une instance suppose d&#39;avoir :

* une boîte mail dédiée à l&#39;instance, qui peut éventuellement être la boîte de mails rebonds,
* des adresses IP d&#39;envoi dédiées à l&#39;instance.

La mise en œuvre d’une feedback loop simple dans Adobe Campaign fait appel à la fonctionnalité de messages rebonds. La boîte email de feedback loop est utilisée comme boîte de rebond et une règle est définie pour détecter ces messages. Les adresses email des destinataires qui ont signalé le message comme indésirable seront ajoutées à la liste des adresses en quarantaine.

* Créez ou adaptez une règle de mails rebonds **Feedback_loop** dans **[!UICONTROL Administration>Gestion de campagne>Gestion des NP@I>Jeux de règles mail]** avec la raison **Refusé** et le type **Hard**.
* Si une boîte a été définie spécialement pour la feedback loop, définissez les paramètres pour relever son contenu en créant un nouveau compte externe de type Mails rebonds dans **[!UICONTROL Administration>Plateforme>Comptes externes]**.

Le mécanisme est immédiatement opérationnel pour traiter les notifications de plaintes. Pour vous assurer que cette règle fonctionne correctement, vous pouvez temporairement désactiver les comptes afin qu&#39;ils ne collectent pas ces messages, puis vérifier manuellement le contenu de la boîte de feedback loop. Sur le serveur, exécutez les commandes suivantes :

```
nlserver stop inMail@instance,
nlserver inMail -instance:instance -verbose.
```

Si vous êtes contraint d&#39;utiliser une seule adresse de feedback loop pour plusieurs instances, il faudra :

* répliquer les messages reçus sur autant de boîtes qu&#39;il existe d&#39;instances,
* faire relever chaque boîte par une seule instance,
* Configurez les instances pour qu’elles ne traitent que les messages qui les concernent : les informations d’instance se trouvent dans l’en-tête Message-ID des messages envoyés par Adobe Campaign et figurent donc également dans les messages de feedback loop. Il vous suffit de spécifier le paramètre **checkInstanceName** dans le fichier de configuration de l’instance (par défaut, l’instance n’est pas vérifiée, ce qui peut entraîner une mise en quarantaine abusive de certaines adresses) :

  ```
  <serverConf>
    <inMail checkInstanceName="true"/>
  </serverConf>
  ```

Le service Délivrabilité d&#39;Adobe Campaign gère votre inscription aux services de feedback loop pour les FAI suivants : AOL, BlueTie, Comcast, Cox, EarthLink, FastMail, Gmail, Hotmail, HostedEmail, Libero, Mail.ru, MailTrust, OpenSRS, QQ, RoadRunner, Synacor, Telenor, Terra, UnitedOnline, USA, XS4ALL, Yahoo, Yandex, Zoho.

## List-Unsubscribe {#list-unsubscribe}

L&#39;ajout d&#39;un en-tête SMTP appelé **List-Unsubscribe** est obligatoire pour une gestion optimale de la délivrabilité.

Cet en-tête peut être utilisé comme alternative à l&#39;icône « Signaler comme SPAM ». Il s’affiche sous la forme d’un lien « Se désabonner » dans les interfaces de messagerie des FAI.

L’utilisation de cette fonctionnalité réduit les taux de plainte et contribue à protéger votre réputation. Les commentaires seront exécutés sous forme de désabonnement.

Gmail, Outlook.com, Yahoo ! et Microsoft Outlook prennent en charge cette méthode. Un lien « Se désabonner » est disponible directement dans leur interface. Par exemple :

![Image](../assets/List-Unsubscribe-example-Gmail.png)

>[!NOTE]
>
>Le lien « Se désabonner » ne s’affiche pas toujours. En effet, cela peut dépendre des critères et de la politique spécifiques de chaque FAI. Par conséquent, assurez-vous que vos messages sont envoyés par un expéditeur :
>
>* Avec une bonne réputation
>* Sous le seuil de plainte contre le spam des FAI
>* Entièrement authentifié

Il existe deux versions de la fonctionnalité d&#39;en-tête List-Unsubscribe :

* **« mailto » List-Unsubscribe** - Avec cette méthode, le fait de cliquer sur le lien **Unsubscribe** envoie un e-mail prérempli à l’adresse de désabonnement spécifiée dans l’en-tête de l’e-mail. [En savoir plus](#mailto-list-unsubscribe)

* **List-Unsubscribe « en un clic »** : cette méthode permet de désabonner directement l’utilisateur en cliquant sur le lien **Unsubscribe**. [En savoir plus](#one-click-list-unsubscribe)

>[!NOTE]
>
>À compter du 1er juin 2024, les principaux FAI exigeront des expéditeurs qu&#39;ils se conforment à la **List-Unsubscribe en un clic**.

### List-Unsubscribe « mailto » {#mailto-list-unsubscribe}

Avec cette méthode, cliquer sur le lien **Se désabonner** envoie un e-mail prérempli à l’adresse de désabonnement spécifiée dans l’en-tête de l’e-mail.

Pour utiliser List-Unsubscribe « mailto », vous devez saisir une ligne de commande dans laquelle vous spécifiez une adresse e-mail, telle que : `List-Unsubscribe: <mailto:client@newsletter.example.com?subject=unsubscribe?body=unsubscribe>`

>[!CAUTION]
>
>L’exemple ci-dessus est basé sur la table des destinataires. Si l’implémentation de la base de données est effectuée à partir d’une autre table, veillez à reformuler la ligne de commande avec les informations correctes.

Vous pouvez également créer un List-Unsubscribe dynamique « mailto » à l’aide d’une ligne de commande telle que : `List-Unsubscribe: <mailto:<%=errorAddress%>?subject=unsubscribe%=message.mimeMessageId%>`

Pour implémenter **List-Unsubscribe « mailto »** dans Campaign, vous pouvez effectuer l’une des opérations suivantes :

* Ajouter directement la ligne de commande dans la diffusion ou le modèle de diffusion - [Découvrez comment](#adding-a-command-line-in-a-delivery-template)

* Créer une règle de typologie - [Découvrez comment](#creating-a-typology-rule)

#### Ajouter une ligne de commande dans une diffusion ou un modèle {#adding-a-command-line-in-a-delivery-template}

La ligne de commande doit être ajoutée dans la section **[!UICONTROL En-têtes SMTP supplémentaires]** de l’en-tête SMTP de l’e-mail.

Cet ajout peut être effectué dans chaque e-mail ou dans les modèles de diffusion existants. Vous pouvez également créer un modèle de diffusion intégrant cette fonctionnalité.

Par exemple, saisissez le script suivant dans le champ **[!UICONTROL En-têtes SMTP supplémentaires]** : `List-Unsubscribe: mailto:unsubscribe@domain.com`. Cliquez sur le lien **se désabonner** pour envoyer un e-mail à l’adresse unsubscribe@domain.com.

Vous pouvez également utiliser une adresse dynamique. Par exemple, pour envoyer un email à l&#39;adresse d&#39;erreur définie pour la plateforme, vous pouvez utiliser le script suivant : `List-Unsubscribe: <mailto:<%=errorAddress%>?subject=unsubscribe%=message.mimeMessageId%>`

![Image](../assets/List-Unsubscribe-template-SMTP.png)

#### Créer une règle de typologie {#creating-a-typology-rule}

La règle de typologie doit contenir le script qui génère la ligne de commande et être inclue dans l&#39;en-tête de l&#39;email.

Découvrez comment créer des règles de typologie dans Adobe Campaign v7/v8 dans [cette section](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/campaign-optimization/about-campaign-typologies.html#typology-rules).

>[!NOTE]
>
>Nous vous recommandons de créer une règle de typologie : la fonctionnalité List-Unsubscribe sera automatiquement ajoutée à chaque e-mail à l&#39;aide de cette règle de typologie.

### List-Unsubscribe En Un Clic {#one-click-list-unsubscribe}

Avec cette méthode, cliquer sur le lien **Se désabonner** désabonne directement l’utilisateur ou l’utilisatrice, ne nécessitant qu’une seule action pour se désabonner.

À compter du 1er juin 2024, les principaux FAI exigeront des expéditeurs qu&#39;ils se conforment à la **List-Unsubscribe en un clic**.

Pour se conformer à cette exigence, les expéditeurs doivent :

* Ajoutez la ligne de commande suivante : `List-Unsubscribe-Post: List-Unsubscribe=One-Click`.
* Incluez un lien de désabonnement URI.
* Prise en charge de la réception de la réponse HTTP POST du destinataire, prise en charge par Adobe Campaign. Vous pouvez également utiliser un service externe.

Pour prendre en charge la réponse POST de désabonnement en un clic List-Unsubscribe directement dans Adobe Campaign v7/v8, vous devez ajouter dans l’application web « Pas de clic pour les destinataires du désabonnement ». Pour ce faire, procédez comme suit :

1. Accédez à **[!UICONTROL Ressources]** > **[!UICONTROL En ligne]** > **[!UICONTROL Applications Web]**.

1. Chargez le fichier [XML](/help/assets/WebAppUnsubNoClick.xml.zip) « Ne cliquez pas sur les destinataires désabonnés ».

Pour configurer **List-Unsubscribe en un clic** dans Campaign, vous pouvez effectuer l’une des opérations suivantes :

* Ajouter la ligne de commande dans la diffusion ou le modèle de diffusion - [Découvrez comment](#one-click-delivery-template)
* Créer une règle de typologie - [Découvrez comment](#one-click-typology-rule)

#### Configuration du désabonnement de la liste en un clic dans la diffusion ou le modèle {#one-click-delivery-template}

Pour configurer List-Unsubscribe en un clic dans la diffusion ou le modèle de diffusion, procédez comme suit.

1. Accédez à la section **[!UICONTROL SMTP]** des propriétés de la diffusion.

1. Sous **[!UICONTROL En-têtes SMTP supplémentaires]**, saisissez les lignes de commande comme dans l’exemple ci-dessous. Chaque en-tête doit se trouver sur une ligne distincte.

Par exemple :

```
List-Unsubscribe-Post: List-Unsubscribe=One-Click
List-Unsubscribe: <https://domain.com/webApp/unsubNoClick?id=<%= recipient.cryptedId %> >, < mailto:<%@ include option='NmsEmail_DefaultErrorAddr' %>?subject=unsubscribe<%=escape(message.mimeMessageId) %> >
```

![Image](../assets/List-Unsubscribe-1-click-template-SMTP.png)

L’exemple ci-dessus active le désabonnement de liste en un clic pour les FAI qui prennent en charge le clic en un seul clic, tout en s’assurant que les destinataires qui ne prennent pas en charge « mailto » peuvent toujours demander un désabonnement par e-mail.

#### Création d’une règle de typologie pour la prise en charge du désabonnement de listes en un clic {#one-click-typology-rule}

Pour configurer List-Unsubscribe en un clic à l’aide d’une règle de typologie, procédez comme suit.

1. Dans l’arborescence de navigation, accédez à **[!UICONTROL Règles de typologie]** et cliquez sur **[!UICONTROL Nouveau]**.

   ![Image](../assets/CreatingTypologyRules1.png)


1. Configurez la nouvelle règle de typologie, telle que :

   * **[!UICONTROL Type de règle]** : **[!UICONTROL Contrôle]**
   * **[!UICONTROL Phase]** : **[!UICONTROL Au début du ciblage]**
   * **[!UICONTROL Canal]** : **[!UICONTROL E-mail]**
   * **[!UICONTROL Level]** : votre choix
   * **[!UICONTROL Actif]**


   ![Image](../assets/CreatingTypologyRules2.png)

1. Codez le javascript de la règle de typologie comme dans l’exemple ci-dessous.

   >[!NOTE]
   >
   >Le code décrit ci-dessous doit être référencé à titre d’exemple uniquement.

   Cet exemple illustre comment :
   * Configurez un List-Unsubscribe « mailto ». Elle ajoute les en-têtes ou ajoute les paramètres « mailto: » existants et les remplace par : &lt;mailto..>, https://...
   * Ajoutez dans l’en-tête List-Unsubscribe en un clic . Il utilise `var headerUnsubUrl = "https://campmomentumv7-mkt-prod3.campaign.adobe.com/webApp/unsubNoClick?id=<%= recipient.cryptedId %>"÷`

   >[!NOTE]
   >
   >Vous pouvez ajouter d’autres paramètres (tels que &amp;service =...).

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


   ![Image](../assets/CreatingTypologyRules3.png)

1. Ajoutez votre nouvelle règle à une typologie s’appliquant aux e-mails.

   >[!NOTE]
   >
   >Vous pouvez l’ajouter à la typologie par défaut.

   ![Image](../assets/CreatingTypologyRules4.png)

1. Préparez une nouvelle diffusion.

   >[!CAUTION]
   >
   >Vérifiez que le champ **[!UICONTROL En-têtes SMTP supplémentaires]** dans les propriétés de la diffusion est vide.

   ![Image](../assets/CreatingTypologyRules5.png)

1. Vérifiez lors de la préparation de la diffusion que votre nouvelle règle de typologie est appliquée.

   ![Image](../assets/CreatingTypologyRules6.png)

1. Vérifiez que le lien de désabonnement est présent.

   ![Image](../assets/CreatingTypologyRules7.png)

## Optimisation des e-mails {#email-optimization}

### SMTP {#smtp}

SMTP (Simple mail transfer protocol) est une norme Internet pour la transmission des emails.

Les erreurs SMTP qui ne sont pas vérifiées par une règle sont répertoriées dans le dossier **[!UICONTROL Administration]** > **[!UICONTROL Gestion de campagne]** > **[!UICONTROL Gestion des échecs]** > **[!UICONTROL Qualification des logs de diffusion]**. Ces messages d’erreur sont par défaut interprétés comme des erreurs soft inatteignables.

Les erreurs les plus courantes doivent être identifiées et une règle correspondante doit être ajoutée dans **[!UICONTROL Administration]** > **[!UICONTROL Gestion de campagne]** > **[!UICONTROL Gestion des échecs]** > **[!UICONTROL Jeux de règles Mail]** si vous souhaitez qualifier correctement les retours des serveurs SMTP. Sans cela, la plateforme effectuera des reprises inutiles (cas d&#39;utilisateurs inconnus) ou placera par erreur certains destinataires en quarantaine après un nombre donné de tests.

### Adresses IP dédiées {#dedicated-ips}

Adobe fournit une stratégie IP dédiée pour chaque client avec une adresse IP en phase de montée (ramp-up) afin d&#39;établir une réputation et optimiser les performances de diffusion.
