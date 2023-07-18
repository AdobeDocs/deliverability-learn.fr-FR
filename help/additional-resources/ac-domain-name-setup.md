---
title: Configuration du nom de domaine
description: Découvrez comment déléguer un sous-domaine à Adobe Campaign.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 4d52d197-d20e-450c-bfcf-e4541c474be4
source-git-commit: 82f7254a9027f79d2af59aece81f032105c192d5
workflow-type: tm+mt
source-wordcount: '2061'
ht-degree: 100%

---

# Configuration du nom de domaine

Ce document décrit les exigences commerciales et techniques de la configuration et de la délégation des noms de domaine. Vous devez sélectionner un sous-domaine d&#39;envoi d&#39;e-mail et, éventuellement, un sous-domaine associé à l&#39;extérieur pour héberger les composants web (pages de destination, page d&#39;opt-out) pour la plateforme Adobe que vous utilisez.

>[!NOTE]
>
>Vous pouvez également configurer de nouveaux sous-domaines à l&#39;aide du Panneau de contrôle (disponible en version bêta). En savoir plus dans [cette section](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html?lang=fr#must-read).

## Sous-domaines

Grâce à Adobe, le marketing numérique peut véritablement devenir le moteur contextuel qui alimente le programme marketing d&#39;engagement de la clientèle de votre marque.  L&#39;email reste la base des programmes de marketing numérique. Cependant, l&#39;accès à la boîte de réception est devenu plus difficile que jamais.

La création d’un sous-domaine pour les campagnes par e-mail permet aux marques d’isoler différents types de trafic (marketing par rapport à entreprise, par exemple) dans des pools d’adresses IP spécifiques et avec des domaines particuliers, ce qui accélère le [processus de réchauffement des adresses IP](../../help/additional-resources/increase-reputation-with-ip-warming.md) et améliore la délivrabilité globale. Si vous partagez un domaine et qu&#39;il est bloqué ou ajouté à la liste bloquée, il peut y avoir un impact sur la diffusion des emails de votre entreprise. Les problèmes de réputation ou les blocages d&#39;un domaine particulier de vos communications marketing par email auront un impact spécifique sur ce flux de messagerie.  L&#39;utilisation de votre domaine principal comme adresse d&#39;expéditeur pour différents flux d&#39;email peut également interrompre l&#39;authentification par email, ce qui bloque ou place vos messages dans le dossier des courriers indésirables.

### Délégation

La délégation de noms de domaine est une méthode qui permet au propriétaire d&#39;un nom de domaine (techniquement : une zone DNS) de déléguer une sous-division (techniquement : une zone DNS située au-dessous, qui peut être appelée sous-zone) à une autre entité. En fait, si un client traite la zone &quot;exemple.com&quot;, il peut déléguer la sous-zone &quot;marketing.exemple.com&quot; à Adobe Campaign.

En d&#39;autres termes, les serveurs DNS d&#39;Adobe Campaign disposent d&#39;une autorité totale spécifiquement sur cette zone et non sur le domaine de niveau supérieur. Les serveurs DNS d&#39;Adobe Campaign fourniront des réponses faisant autorité aux requêtes concernant les noms de domaines de cette zone, comme &quot;t.marketing.exemple.com&quot; lui-même, mais pas &quot;www.example.com&quot;.

En déléguant un sous-domaine à utiliser avec Adobe Campaign, les clients peuvent compter sur Adobe pour gérer l&#39;infrastructure DNS requise afin de répondre aux exigences de délivrabilité standard de leurs domaines de marketing par email, tout en continuant à gérer et à contrôler le DNS de leurs domaines de messagerie internes.  La délégation de sous-domaines permet :

Pour les clients : de conserver l&#39;image de leur marque en utilisant un alias DNS avec ses noms de domaine.
Pour Adobe : de mettre en œuvre de manière autonome les bonnes pratiques techniques afin d&#39;optimiser pleinement la délivrabilité lors de l&#39;envoi d&#39;emails.

## Options de configuration DNS

Pour fournir un service géré en mode cloud, Adobe encourage fortement les clients à utiliser la délégation de sous-domaines lors du déploiement d&#39;Adobe Campaign.  Toutefois, Adobe propose aux clients une autre option, la configuration CNAME, pour configurer le DNS.

| Option | Description | Responsabilités d&#39;Adobe | Responsabilités du client |
|--- |------- |--- |--- |
| Délégation de sous-domaine à Adobe Campaign | Le client délègue un sous-domaine (email.example.com) à Adobe. Dans ce scénario, Adobe est en mesure de fournir une campagne sous la forme d’un service géré en contrôlant et en conservant tous les aspects du DNS nécessaires à la diffusion, au rendu et au suivi des campagnes par e-mail. | Gestion complète du sous-domaine et de tous les enregistrements DNS requis pour Adobe Campaign. | Délégation appropriée du sous-domaine à Adobe |
| Utilisation des CNAME | Le client crée un sous-domaine et utilise des CNAME pour pointer vers des enregistrements spécifiques à Adobe.  Grâce à cette configuration, Adobe et le client partagent la responsabilité de la maintenance du DNS. | Gestion des enregistrements DNS requis pour Adobe Campaign. | Création et contrôle du sous-domaine et création/gestion des enregistrements CNAME requis pour Adobe Campaign. |

## Enregistrements DNS requis

| Type d&#39;enregistrement | Rôle | Exemples d&#39;enregistrement/de contenu |
|--- |--- |--- |
| MX | Spécification des serveurs de messagerie pour les messages entrants | <i>email.example.com</i></br><i>10 inbound.email.example.com</i> |
| SPF (TXT) | Cadre de la politique de l&#39;expéditeur | <i>email.example.com</i></br>&quot;v=spf1 redirect=__spf.campaign.adobe.com&quot; |
| DKIM (TXT) | Message identifié DomainKeys | <i>client._domainkey.email.example.com</i></br>&quot;v=DKIM1; k=rsa;&quot; &quot;DKIMPUBLICKEY ICI&quot; |
| Enregistrements hôtes (A) | Pages miroir, hébergement d&#39;images et liens de suivi, tous les domaines d&#39;envoi | m.email.example.com DANS A 123.111.100.99</br>t.email.example.com DANS A 123.111.100.98</br>email.example.com DANS A 123.111.100.97 |
| DNS inversé (PTR) | Mappe les adresses IP du client avec un nom d&#39;hôte de marque client. | 18.101.100.192.in-addr.arpa pointeur de nom de domaine r18.email.example.com |
| CNAME | Fournit un alias à un autre nom de domaine | t1.email.example.com est un alias pour t1.email.example.campaign.adobe.com |


DMARC (Domain-based Message Authentication, Reporting, and Conformance) est recommandé pour authentifier les expéditeurs d’emails et faire en sorte que les systèmes de messagerie de destination acceptent les messages envoyés depuis votre domaine comme fiables.

Exemple d’un enregistrement TXT DMARC :

```
_dmarc.email.example.com

“v=DMARC1; p=none; rua=mailto:mailauth-reports@myemail.com” 
```

Vous pouvez mettre en œuvre DMARC manuellement ou contacter Adobe pour vous aider à configurer DMARC pour votre marque.

## Configuration requise

### Délégation de sous-domaine

Pour ce faire, le client doit créer un sous-domaine dans ses serveurs DNS et définir les serveurs de noms pour ce sous-domaine comme étant ceux gérés par Adobe.  Par exemple, un client dont le nom de domaine principal est &quot;exemple.com&quot; et qui souhaite déléguer la gestion de &quot;marketing.exemple.com&quot; à Adobe pour ses diffusions par email devra matérialiser cette délégation pour ajouter les enregistrements de type suivants à son DNS :

```
marketing.example.com. NS a.ns.campaign.adobe.com.
marketing.example.com. NS b.ns.campaign.adobe.com.
marketing.example.com. NS c.ns.campaign.adobe.com.
marketing.example.com. NS d.ns.campaign.adobe.com.
```

La délégation d&#39;un nom de domaine implique que ce domaine sera dédié à la diffusion d&#39;emails via la plateforme Adobe Campaign et ne peut donc pas être utilisé pour d&#39;autres moyens (par exemple, l&#39;envoi d&#39;emails à partir d&#39;une autre infrastructure de messagerie).

Au cours du processus de configuration, Adobe s&#39;assure que le domaine est attaché à l&#39;infrastructure d&#39;email entrant d&#39;Adobe afin de gérer et de traiter les emails rebonds revenant à ces domaines (configuration d&#39;enregistrement DNS de type MX).

### Utilisation des CNAME

Si le client choisit d&#39;utiliser des CNAME plutôt que de déléguer un sous-domaine à Adobe, au cours de la phase de configuration, Adobe fournit les enregistrements à placer dans les serveurs DNS client et configure les valeurs correspondantes dans les serveurs DNS Adobe Campaign.

## Exigences générales relatives au déploiement

Lors de la mise en œuvre d&#39;une nouvelle solution de marketing d&#39;entreprise, des composants externes sont requis.  Il s&#39;agit notamment de l&#39;hébergement de pages de destination et de formulaires Web, de la configuration de liens et de pages web à suivre, de l&#39;affichage des pages miroir et de la configuration d&#39;une page d&#39;opt-out.

Bien que ces exigences soient gérées au moyen de composants hébergés à la fois par Adobe et le client, elles incluent des URL visibles par les destinataires des emails.  Afin d&#39;éviter que des URL indiquant la solution technique sous-jacente ou le fournisseur d&#39;hébergement ne soient installées, il est possible de configurer des sous-domaines pour rendre cette opération transparente pour les destinataires des emails.  Par exemple, lorsque vous consultez une URL telle que http://www.customer.com/, le domaine est &quot;www.customer.com&quot;.  Le sous-domaine de ce site serait &quot;www&quot;.

### Exigences relatives aux sous-domaines

Déterminez le ou les sous-domaine(s) à utiliser pour les URL de marque (pages miroir et URL de suivi) à partir de l&#39;application Adobe Campaign.  Décidez également de l&#39;adresse d&#39;origine, du nom de l&#39;expéditeur et de l&#39;adresse de réponse pour chaque sous-domaine des diffusions par email.

Complétez le tableau ci-dessous, la première ligne n&#39;étant qu&#39;un exemple.

| Sous-domaine | Adresse d&#39;origine | Nom de l&#39;expéditeur | Adresse de réponse |
|--- |--- |--- |--- |
| emails.customer.com | news@emails.customer.com | Client | customercare@customer.com |
| </br> | </br> | </br> | </br> |

>[!NOTE]
>
>* Le champ &quot;Adresse de réponse&quot; a pour objet de demander au destinataire de répondre à une adresse différente de celle de l&#39;adresse d&#39;origine.  Bien qu&#39;il ne s&#39;agisse pas d&#39;un champ obligatoire, Adobe recommande vivement que l&#39;&quot;adresse de réponse&quot; soit valide et liée à une boîte de réception surveillée.  Cette boîte de réception doit être hébergée par le client.  Il peut s&#39;agir d&#39;une boîte de réception d&#39;assistance, par exemple, customercare@customer.com, où les emails sont lus et où on leur répond.
>* Si aucune &quot;adresse de réponse&quot; n&#39;est choisie par le client, l&#39;adresse par défaut est toujours `<tenant>-<type>-<env>@<subdomain>`.
>* Lorsque l&#39;adresse de réponse est configurée de cette façon, les réponses sont envoyées à une boîte de réception non contrôlée.
>* Lors de l&#39;envoi d&#39;emails à partir d&#39;Adobe Campaign, la boîte de réception &quot;Adresse d&#39;origine&quot; n&#39;est pas surveillée et les utilisateurs marketing ne peuvent pas accéder à cette boîte de réception. Adobe Campaign n&#39;offre pas non plus la possibilité de répondre automatiquement ou de transférer automatiquement les messages reçus dans cette boîte de réception.
>* L&#39;adresse de l&#39;expéditeur Campaign et l&#39;adresse d&#39;erreur ne peuvent pas être &quot;abus&quot; ou &quot;maître de poste&quot;.

## Délégation de sous-domaines

Le ou les sous-domaine(s) choisi(s) pour la plateforme Adobe Campaign doivent être délégués à travers la création de quatre enregistrements de serveur de noms.  Cela permet de déléguer correctement le sous-domaine à Adobe.  Vous trouverez ci-dessous un exemple de délégation de sous-domaines et les instructions DNS correspondantes.  Veuillez remplacer &quot;emails.customer.com&quot; par le sous-domaine que vous souhaitez déléguer.  Veuillez noter que le sous-domaine doit être unique et ne peut pas être déjà utilisé par une autre partie (par exemple, un fournisseur de services internet - FAI ou un fournisseur de services gérés - MSP).

| Sous-domaine délégué | Instructions DNS |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.cacampaign.adobe.com. </br> `<subdomain>` NS b.ns.cacampaign.adobe.com. </br> `<subdomain>` NS c.ns.cacampaign.adobe.com. </br> `<subdomain>` NS d.ns.cacampaign.adobe.com. |

## Suivi, pages miroir, ressources

Une fois que le ou les sous-domaine(s) d&#39;envoi d&#39;email sont correctement délégués à Adobe Campaign, l&#39;équipe TechOps d&#39;Adobe crée deux domaines de niveau inférieur, ou plus, pour gérer le suivi et les pages miroir de manière indépendante.

| Type | Domaine |
|--- |--- |
| Pages miroir | m.`<subdomain>` |
| Tracking | t.`<subdomain>` |
| Ressources | res.`<subdomain>` |

## Déploiement dans le cloud (facultatif)

Cela ne s&#39;applique que si Adobe Campaign Classic est entièrement hébergé dans le cloud par Adobe.  Il s&#39;agit d&#39;une configuration facultative.

Tous les questionnaires, formulaires web et pages de destination à développer sont gérés via Adobe Campaign entièrement hébergé dans le cloud.  Si nécessaire, un sous-domaine supplémentaire peut être délégué à Adobe (par exemple, web.customer.com) afin de l&#39;utiliser pour tous les composants Web de l&#39;outil.  Veuillez noter que le sous-domaine doit être unique et ne peut pas être utilisé par une autre partie (par exemple, un fournisseur de services internet -FAI ou un fournisseur de services gérés - MSP).

| Sous-domaine délégué | Instructions DNS |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.cacampaign.adobe.com.</br>`<subdomain>` NS b.ns.cacampaign.adobe.com.</br>`<subdomain>` NS c.ns.cacampaign.adobe.com.</br>`<subdomain>` NS d.ns.cacampaign.adobe.com. |

>[!NOTE]
>
>Par défaut, tout composant Web de l&#39;outil utilise le sous-domaine initial délégué à utiliser pour l&#39;email.

## Déploiement de la messagerie Cloud (facultatif)

Dans le cas où l&#39;instance de marketing Adobe Campaign Classic est hébergée sur site au niveau du client, des configurations techniques supplémentaires devront être apportées par le client.

Tous les questionnaires, formulaires web et pages de destination à développer sont gérés par l&#39;instance de marketing Adobe Campaign, où se trouvent les enregistrements destinataires.

Une configuration DNS CNAME supplémentaire est requise pour déployer des composants Web externes hébergés par l&#39;instance de marketing Adobe Campaign.  Cela permet aux composants Web (par exemple, web.customer.com) d&#39;être accessibles au public sur Internet et d&#39;être marqués avec le domaine du client.

Les pare-feu devront également être configurés pour autoriser l&#39;accès à l&#39;instance de marketing Adobe Campaign qui héberge ces composants Web (sur le port 80 ou 443).

**Recommendations concernant les bonnes pratiques :**

Le sous-domaine qui héberge les composants Web sera visible pour les clients.Veillez donc à ce que la marque y soit explicite et simple à mémoriser, car il peut être nécessaire de saisir manuellement ce sous-domaine, par exemple : https://web.customer.com.
S&#39;il est nécessaire d&#39;héberger des formulaires sur des pages sécurisées (HTTPS), une configuration technique supplémentaire est requise, comme décrit ci-dessous.

| Sous-domaine délégué | Instructions DNS |
|--- |--- |
| `<subdomain>` | `<subdomain>` CNAME `<internal customer server>` |

## Services rendus

À la suite de ces délégations, l&#39;infrastructure mise en place par Adobe garantit que les services suivants sont mis en œuvre pour chaque domaine d&#39;envoi délégué ou en alias CNAME :

* Création de boîtes de réception &quot;maître de poste&quot; et &quot;abus&quot;
* Configuration de boucles de commentaires pour le domaine délégué
* Sur demande, Adobe configure également un enregistrement DMARC tel que spécifié. Votre conseiller en délivrabilité peut vous aider à concevoir une politique DMARC à long terme et à planifier vos domaines d&#39;envoi.
Les paramètres établis par Adobe ne sont valables qu&#39;à partir du moment où la délégation a été effectuée puis vérifiée par Adobe, et restent fonctionnels.  Toutes les offres Adobe Campaign Cloud incluent la délégation de noms de domaine en standard.

## Conditions de facturation et de mise en œuvre

* Selon le contrat initial et le type de package choisi, il est possible d&#39;inclure d&#39;autres délégations en plus de celles proposées en standard, au-delà de cette délégation initiale.
* En plus de ces délégations ajoutées, d&#39;autres seront facturées.
* La méthode de facturation de ces délégations supplémentaires est calculée sous la forme d&#39;un coût mensuel supplémentaire, comme indiqué dans le contrat initial.

Elles sont acceptées à condition que le CLIENT choisisse les noms de domaine associés dédiés aux diffusions via l&#39;outil Adobe Campaign et que les conditions préalables à la délégation décrites dans le document approprié soient correctement mises en œuvre.

## Interruption des services

À tout moment, le CLIENT peut faire une demande écrite pour ne plus bénéficier des services de délégation et pour assumer les configurations DNS nécessaires elles-mêmes.

Si cela se produit, Adobe fournit au CLIENT une estimation détaillant le nombre de jours de service nécessaires pour revenir au mode de délégation hors domaine.

Adobe sera déchargé de toute responsabilité pour l&#39;engagement du taux de délivrabilité susmentionné si le Client ne respecte pas les engagements énoncés ci-dessus.

La résiliation du service Marketing Cloud entraînera automatiquement la fin des délégations de domaines et la maintenance DNS de ces domaines par Adobe.

## Surveillance des sous-domaines à l&#39;aide du Panneau de contrôle

Une fois les sous-domaines configurés pour votre instance, vous pouvez les surveiller à l&#39;aide du Panneau de contrôle.

Vous pouvez ainsi afficher tous les sous-domaines délégués à Adobe Campaign, mais aussi demander le renouvellement de leurs certificats SSL.

Consultez à ce sujet la [documentation dédiée](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/monitoring-subdomains.html?lang=fr#subdomains-and-certificates).

>[!NOTE]
>
>[Le Panneau de contrôle](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=fr) est disponible uniquement pour les clients qui utilisent Adobe Managed Services.
