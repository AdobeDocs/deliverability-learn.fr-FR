---
title: Configuration du nom de domaine
description: Découvrez comment déléguer un sous-domaine à Adobe Campaign.
feature: Mise en pratique
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 1e539b5df54250a5927701009e7a9c84e5d73fae
workflow-type: tm+mt
source-wordcount: '2032'
ht-degree: 2%

---


# Configuration du nom de domaine

Ce document décrit les exigences commerciales et techniques de la configuration et de la délégation des noms de domaine. Vous devez sélectionner un sous-domaine d’envoi de courrier électronique et, éventuellement, un sous-domaine faisant face à l’extérieur pour héberger les composants Web (landings page, page d’exclusion) pour la plateforme d’Adobe que vous utilisez.

>[!NOTE]
>
>Vous pouvez également configurer de nouveaux sous-domaines à l’aide du Panneau de Contrôle (disponible en version bêta). En savoir plus dans [cette section](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/setting-up-new-subdomain.html#must-read).

## Sous-domaines

Grâce à l’Adobe, le marketing numérique peut véritablement devenir le moteur contextuel qui alimente le programme marketing d’engagement de la clientèle de votre marque.  Le courrier électronique reste la base des programmes marketing numériques. Cependant, l&#39;accès à la boîte de réception est devenu plus difficile que jamais.

La création d’un sous-domaine pour les campagnes par courriel permet aux marques d’isoler différents types de trafic (marketing par rapport à entreprise, par exemple) dans des pools d’adresses IP spécifiques et avec des domaines spécifiques, ce qui accélère le [processus de réchauffement de l’IP](../../help/additional-resources/increase-reputation-with-ip-warming.md) et améliore la délivrabilité globale. Si vous partagez un domaine et qu’il est bloqué ou ajouté à la liste bloquée, cela peut avoir un impact sur votre diffusion de messagerie d’entreprise. Cependant, les problèmes de réputation ou les blocages d&#39;un domaine spécifique à vos communications marketing par courrier électronique auront un impact sur ce flux de courrier électronique.  L’utilisation de votre domaine principal comme adresse d’expéditeur ou d’expéditeur pour plusieurs flux de courrier électronique peut également interrompre l’authentification par courrier électronique, ce qui bloque ou place vos messages dans le dossier de messages indésirables.

### Délégation

La délégation de noms de domaine est une méthode qui permet au propriétaire d’un nom de domaine (techniquement : une zone DNS) pour déléguer une subdivision (techniquement : une zone DNS en dessous, qui peut être appelée sous-zone) vers une autre entité. En gros, si un client traite la zone &quot;exemple.com&quot;, il peut déléguer la sous-zone &quot;marketing.exemple.com&quot; à Adobe Campaign.

Cela signifie que les serveurs DNS d’Adobe Campaign disposent d’une autorité totale sur cette zone seulement et non sur le domaine de niveau supérieur. Les serveurs DNS d’Adobe Campaign fourniront des réponses faisant autorité aux requêtes sur les noms de domaine dans cette zone, comme &quot;t.marketing.exemple.com&quot; lui-même, mais pas &quot;www.example.com&quot;.

En déléguant un sous-domaine à utiliser avec Adobe Campaign, les clients peuvent compter sur l’Adobe pour gérer l’infrastructure DNS requise pour répondre aux exigences de délivrabilité standard de leurs domaines d’envoi de marketing par courrier électronique, tout en continuant à gérer et à contrôler le DNS de leurs domaines de messagerie internes.  La délégation de sous-domaines permet :

Clients qui conservent l’image de leur marque en utilisant un alias DNS avec ses noms de domaine
Adobe de mettre en oeuvre de manière autonome toutes les meilleures pratiques techniques afin d&#39;optimiser pleinement la délivrabilité lors de l&#39;envoi par courriel

## Options de configuration DNS

Afin de fournir un service géré en mode cloud, l’Adobe encourage fortement les clients à utiliser la délégation de sous-domaines lors du déploiement de Adobe Campaign.  Toutefois, l’Adobe propose aux clients offre une autre option - configuration CNAME - pour configurer le DNS.

| Option | Description | Responsabilités de l&#39;Adobe | Responsabilités du client |
|--- |------- |--- |--- |
| Délégation de sous-domaine en Adobe Campaign | Le client délègue un sous-domaine (email.example.com) à l’Adobe. Dans ce scénario, l’Adobe peut fournir le Campaign en tant que service géré en contrôlant et en conservant tous les aspects du DNS requis pour la diffusion, le rendu et le suivi des campagnes par courrier électronique. | Gestion complète du sous-domaine et de tous les enregistrements DNS requis pour Adobe Campaign. | Délégation appropriée du sous-domaine à l&#39;Adobe |
| Utilisation des CNAME | Le client crée un sous-domaine et utilise des CNAME pour pointer vers des enregistrements spécifiques à un Adobe.  Grâce à cette configuration, Adobe et le client partagent la responsabilité de la maintenance du DNS. | Gestion des enregistrements DNS requis pour Adobe Campaign. | Création et contrôle du sous-domaine et création/gestion des enregistrements CNAME requis pour Adobe Campaign. |

## Enregistrements DNS requis

| Type d&#39;enregistrement | Rôle | Exemples d&#39;enregistrement/de contenu |
|--- |--- |--- |
| MX | Spécification des serveurs de messagerie pour les messages entrants | <i>email.example.com</i></br><i>10 inbound.email.example.com</i> |
| SPF (TXT) | Cadre de la stratégie de l&#39;expéditeur | <i>email.example.com</i></br>&quot;v=spf1 redirect=__spf.campaign.adobe.com&quot; |
| DKIM (TXT) | Message d&#39;identification des clés de domaine | <i>client._domainkey.email.example.com</i></br>&quot;v=DKIM1; k=rsa;&quot; &quot;DKIMPUBLICKEY ICI&quot; |
| DMARC (TXT) | Authentification des messages basée sur un domaine | Rapports et conformité | _dmarc.email.example.com</br>&quot;v=DMARC1; p=none; rua=mailto:mailauth-reports@myemail.com&quot; |
| Hôtes Enregistrements (A) | Pages miroir, hébergement d’images et liens de suivi, tous les domaines d’envoi | m.email.example.com DANS A 123.111.100.99</br>t.email.example.com DANS A 123.111.100.98</br>email.example.com DANS A 123.111.100.97 |
| DNS inversé (PTR) | Mappe les adresses IP du client à un nom d’hôte de marque client. | 18.101.100.192.in-addr.arpa pointeur de nom de domaine r18.email.example.com |
| CNAME | Fournit un alias à un autre nom de domaine | t1.email.example.com est un alias pour | t1.email.example.campaign.adobe.com |

## Configuration requise

### Délégation de sous-domaine

Pour ce faire, le client doit créer un sous-domaine dans ses serveurs DNS et définir les serveurs de noms pour ce sous-domaine comme étant ceux gérés par Adobe.  Par exemple, un client dont le nom de domaine principal est &quot;exemple.com&quot; et qui souhaite déléguer la gestion de &quot;marketing.exemple.com&quot; à l’Adobe pour ses diffusions électroniques devra matérialiser cette délégation pour ajouter les enregistrements de type suivants à son DNS :

```
marketing.example.com. NS a.ns.campaign.adobe.com.
marketing.example.com. NS b.ns.campaign.adobe.com.
marketing.example.com. NS c.ns.campaign.adobe.com.
marketing.example.com. NS d.ns.campaign.adobe.com.
```

La délégation d’un nom de domaine implique que ce domaine sera dédié à la diffusion de messages électroniques via la plate-forme Adobe Campaign et ne peut donc pas être utilisé pour d’autres moyens (par exemple, l’envoi de messages électroniques à partir d’une autre infrastructure de messagerie).

Au cours du processus de configuration, l&#39;Adobe s&#39;assurera que le domaine est attaché à l&#39;infrastructure de courrier électronique entrant de l&#39;Adobe afin de gérer et de traiter les courriers électroniques rebonds revenant à ces domaines (configuration d&#39;enregistrement DNS de type MX).

### Utilisation des CNAME

Si le client choisit d’utiliser des CNAME plutôt que de déléguer un sous-domaine à l’Adobe, au cours de la phase de configuration, l’Adobe fournira les enregistrements à placer dans les serveurs DNS client et configurera les valeurs correspondantes dans les serveurs DNS Adobe Campaign.

## Exigences générales relatives au déploiement

Lors de la mise en oeuvre d’une nouvelle solution de marketing d’entreprise, des composants externes sont requis.  Il s’agit notamment de l’hébergement de landings page et de formulaires Web, de la configuration de liens et de pages Web à suivre, de l’affichage des pages miroir et de la configuration d’une page d’exclusion.

Bien que ces exigences soient gérées au moyen de composants hébergés à la fois par l’Adobe et le client, elles incluent des URL visibles par les destinataires des courriels.  Afin d’éviter que des URL indiquant la solution technique sous-jacente ou le fournisseur d’hébergement ne soient installées, il est possible de configurer des sous-domaines pour rendre cette opération transparente pour les destinataires des courriels.  Par exemple, lorsque vous consultez une URL telle que http://www.customer.com/, le domaine est &quot;www.customer.com&quot;.  Le sous-domaine de ce site serait &quot;www&quot;.

### Exigences relatives aux sous-domaines

Déterminez le ou les sous-domaines à utiliser pour les URL de marque (pages miroir et URL de suivi) à partir de l’application Adobe Campaign.  Décidez également de l’adresse &quot;De&quot;, &quot;De&quot; et &quot;Adresse de réponse&quot; pour chaque sous-domaine des diffusions de messagerie.

Remplissez le tableau ci-dessous, la première ligne n&#39;est qu&#39;un exemple.

| Subdomain | Adresse de départ | Nom du formulaire | Adresse de réponse |
|--- |--- |--- |--- |
| emails.customer.com | news@emails.customer.com | Informations      | customercare@customer.com |
| </br> | </br> | </br> | </br> |

>[!NOTE]
>
>* Le champ &quot;Adresse de réponse&quot; a pour objet de demander au destinataire de répondre à une adresse différente de celle de l’adresse de départ.  Bien qu&#39;il ne s&#39;agisse pas d&#39;un champ obligatoire, l&#39;Adobe recommande vivement que l&#39;&quot;adresse de réponse&quot; soit valide et liée à une boîte aux lettres surveillée.  Cette boîte aux lettres doit être hébergée par le client.  Il peut s’agir d’une boîte aux lettres d’assistance, par exemple, customercare@customer.com, où les courriels sont lus et auxquels on répond.
>* Si aucune &quot;adresse de réponse&quot; n&#39;est choisie par le client, l&#39;adresse par défaut est toujours `<tenant>-<type>-<env>@<subdomain>`.
>* Lorsque l&#39;adresse de réponse est configurée de cette façon, les réponses sont envoyées à une boîte aux lettres non contrôlée.
>* Lors de l’envoi de courriers électroniques à partir d’Adobe Campaign, la boîte aux lettres &quot;De l’adresse&quot; n’est pas surveillée et les utilisateurs marketing ne peuvent pas accéder à cette boîte aux lettres. Adobe Campaign n&#39;offre pas non plus la possibilité de répondre automatiquement ou de transférer automatiquement les messages reçus dans cette boîte aux lettres.
>* L&#39;adresse de l&#39;expéditeur/expéditeur Campaign et l&#39;adresse d&#39;erreur ne peuvent pas être &quot;abus&quot; ou &quot;maître de poste&quot;.


## Délégation de sous-domaines

Le ou les sous-domaines choisis pour la plate-forme Adobe Campaign doivent être délégués en créant quatre enregistrements de serveur de noms (NS).  Cela permet de déléguer correctement le sous-domaine à l’Adobe.  Vous trouverez ci-dessous un exemple de délégation de sous-domaines et les instructions DNS correspondantes.  Veuillez remplacer &quot;emails.customer.com&quot; par le sous-domaine que vous souhaitez déléguer.  Veuillez noter que le sous-domaine doit être unique et ne peut pas être déjà utilisé par une autre partie (par exemple, un fournisseur de services Internet (ESP) ou un fournisseur de services multiservices).

| Sous-domaine délégué | Instructions DNS |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.cacampaign.adobe.com.  </br> `<subdomain>` NS b.ns.cacampaign.adobe.com.  </br> `<subdomain>` NS c.ns.cacampaign.adobe.com.  </br> `<subdomain>` NS d.ns.cacampaign.adobe.com. |

## Suivi, Pages miroir, ressources

Une fois que le ou les sous-domaines d&#39;envoi de courrier électronique sont correctement délégués à Adobe Campaign, l&#39;équipe TechOps Adobe crée deux domaines de niveau inférieur ou plus pour gérer le suivi et les pages miroir de manière indépendante.

| Type | Domain |
|--- |--- |
| Pages miroir | m.`<subdomain>` |
| Tracking | t.`<subdomain>` |
| Ressources | res.`<subdomain>` |

## Déploiement dans le cloud (facultatif)

Cela ne s’applique que si le Adobe Campaign Classic est entièrement hébergé dans le cloud par Adobe.  Il s’agit d’une configuration facultative.

Tous les questionnaires, formulaires Web et landings page à développer sont gérés via Adobe Campaign entièrement hébergés dans le cloud.  Si nécessaire, un sous-domaine supplémentaire peut être délégué à l’Adobe (par exemple, web.customer.com) pour l’utiliser pour tous les composants Web de l’outil.  Veuillez noter que le sous-domaine doit être unique et ne peut pas être utilisé par une autre partie (par exemple, un fournisseur de services Internet (ESP) ou un fournisseur de services multiservices).

| Sous-domaine délégué | Instructions DNS |
|--- |--- |
| `<subdomain>` | `<subdomain>` NS a.ns.cacampaign.adobe.com.</br>`<subdomain>` NS b.ns.cacampaign.adobe.com.</br>`<subdomain>` NS c.ns.cacampaign.adobe.com.</br>`<subdomain>` NS d.ns.cacampaign.adobe.com. |

>[!NOTE]
>
>Par défaut, tout composant Web de l&#39;outil utilise le sous-domaine initial délégué à utiliser pour le courrier électronique.

## Déploiement de la messagerie Cloud (facultatif)

Dans le cas où l’instance de marketing Adobe Campaign Classic est hébergée sur site au niveau du client, des configurations techniques supplémentaires devront être apportées par le client.

Tous les questionnaires, formulaires Web et landings page à développer sont gérés par l’instance de marketing Adobe Campaign, où se trouvent les enregistrements destinataires.

Une configuration DNS CNAME supplémentaire est requise pour déployer des composants Web externes hébergés par l’instance de marketing Adobe Campaign.  Cela permet aux composants Web (par exemple, web.customer.com) d’être accessibles au public sur Internet et d’être marqués avec le domaine du client.

Les pare-feu devront également être configurés pour autoriser l’accès à l’instance de marketing Adobe Campaign qui héberge ces composants Web (sur le port 80 ou 443).

**Recommendations des meilleures pratiques :**

Le sous-domaine où héberger les composants Web sera visible pour les clients. Veillez donc à le rendre correctement marqué et simple à mémoriser, car il peut être nécessaire de le saisir manuellement, par exemple : https://web.customer.com.
Si des formulaires doivent être hébergés sur des pages sécurisées (HTTPS), une configuration technique supplémentaire sera requise, comme décrit ci-dessous.

| Sous-domaine délégué | Instructions DNS |
|--- |--- |
| `<subdomain>` | `<subdomain>` CNAME `<internal customer server>` |

## Services rendus

À la suite de ces délégations, l&#39;infrastructure mise en place par l&#39;Adobe garantit que les services suivants sont effectués pour chaque domaine d&#39;envoi délégué ou en alias CNAME :

* Création de boîtes de réception &quot;maître de poste&quot; et &quot;abus&quot;
* Configuration de boucles de commentaires pour le domaine délégué
* Sur demande, l’Adobe configurera également un enregistrement DMARC tel que spécifié. Votre conseiller en livrabilité peut vous aider à concevoir une stratégie DMARC à long terme et à planifier vos domaines d’envoi.
Les paramètres établis par l&#39;Adobe ne sont valables qu&#39;à partir du moment où la délégation a été terminée puis vérifiée par l&#39;Adobe, et restent fonctionnels.  Toutes les offres Adobe Campaign Cloud incluent la délégation de noms de domaine en standard.

## Conditions de facturation et de mise en oeuvre

* Selon le contrat initial et le type de colis choisi, d&#39;autres délégations peuvent être incluses en plus de celles incluses comme standard au-delà de cette délégation initiale,
* Au-delà de ces délégations, d&#39;autres délégations seront facturées,
* La méthode de facturation de ces délégations supplémentaires est calculée à un coût mensuel supplémentaire, comme indiqué dans le contrat initial.

Ces délégations seront acceptées à condition que le CLIENT choisisse les noms de domaine associés qui sont dédiés aux diffusions via l&#39;outil Adobe Campaign et que les conditions préalables à la délégation décrites dans le document pertinent soient correctement mises en oeuvre.

## Interruption des services

À tout moment, le CLIENT pourra faire une demande écrite pour ne plus bénéficier des services de délégation et pour prendre les configurations DNS nécessaires elles-mêmes.

Si cela se produit, l&#39;Adobe fournira au CLIENT une estimation détaillant le nombre de jours de service nécessaires pour revenir au mode de délégation hors domaine.

L&#39;Adobe sera déchargé de toute responsabilité pour l&#39;engagement du taux de livrabilité susmentionné si le Client ne respecte pas les engagements énoncés ci-dessus.

La résiliation du service de Marketing Cloud entraînera automatiquement la fin des délégations de domaines et la maintenance DNS de ces domaines par Adobe.

## Surveillance des sous-domaines à l’aide du Panneau de Contrôle

Une fois les sous-domaines configurés pour votre instance, vous pouvez les surveiller à l’aide du Panneau de Contrôle.

Cela vous permet de vue tous les sous-domaines que vous avez délégués à Adobe Campaign, ainsi que de demander le renouvellement de leurs certificats SSL.

Consultez à ce sujet la [documentation dédiée](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/monitoring-subdomains.html#subdomains-and-certificates).

>[!NOTE]
>
>[Contrôlez ](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=fr) les Panelis disponibles uniquement pour les clients utilisant Adobe Managed Services.