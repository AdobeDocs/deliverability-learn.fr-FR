---
title: 'Campaign Classic : recommandations techniques'
description: Découvrez les techniques, les configurations et les outils que vous pouvez utiliser pour améliorer votre taux de délivrabilité avec Adobe Campaign Classic.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 39ed3773-18bf-4653-93b6-ffc64546406b
source-git-commit: 4796bfb222f6d4418a67763be767d982aef08a94
workflow-type: tm+mt
source-wordcount: '1753'
ht-degree: 51%

---

# Campaign Classic : recommandations techniques {#technical-recommendations}

Vous trouverez ci-dessous plusieurs techniques, configurations et outils que vous pouvez utiliser pour améliorer votre taux de délivrabilité lors de l’utilisation de Adobe Campaign Classic.

## Configuration {#configuration}

### Reverse DNS {#reverse-dns}

Adobe Campaign vérifie qu’un reverse DNS est bien renseigné pour une adresse IP et que celui-ci reboucle bien sur l’IP.

Un point indispensable de la configuration réseau est d&#39;avoir établi un reverse DNS correct pour chacune des adresses IP d&#39;envoi. Cela signifie que pour une adresse IP donnée, il existe un enregistrement reverse DNS (enregistrement PTR) dont la correspondance DNS (enregistrement A) reboucle sur l&#39;adresse IP initiale.

Le choix du domaine pour un reverse DNS a une incidence lorsque vous traitez avec certains FAI. AOL, en particulier, n’accepte que les feedback loops dont l’adresse appartient au même domaine que le reverse DNS (voir la section [Feedback loop](#feedback-loop)).

>[!NOTE]
>
>Vous pouvez utiliser [cet outil externe](https://mxtoolbox.com/SuperTool.aspx) pour vérifier la configuration d’un domaine.

### Règles MX {#mx-rules}

Les règles MX (Mail eXchanger) correspondent aux règles de gestion de communication entre un serveur expéditeur et un serveur destinataire.

Plus précisément, elles servent à contrôler la vitesse à laquelle le MTA (Message Transfer Agent) Adobe Campaign envoie les emails à chaque domaine d’email ou FAI (par exemple, hotmail.com, comcast.net). Ces règles sont généralement basées sur les limites publiées par les FAI (par exemple, ne pas inclure plus de 20 messages par connexion SMTP).

>[!NOTE]
>
>Pour plus d&#39;informations sur la gestion des MX dans Adobe Campaign Classic, reportez-vous à la section [cette section](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/email-deliverability.html#mx-configuration).

### TLS {#tls}


(Transport Layer Security) est un protocole de cryptage qui peut être utilisé pour sécuriser la connexion entre deux serveurs de messagerie et empêcher la lecture du contenu d’un email par une autre personne que le destinataire prévu.

### Domaine de l’expéditeur {#sender-domain}

Pour définir le domaine utilisé pour la commande HELO, éditez le fichier de configuration de l&#39;instance (conf/config-instance.xml) et définissez un attribut &quot;localDomain&quot; comme suit :

```
<serverConf>
  <shared>
    <dnsConfig localDomain="mydomain.net"/>
  </shared>
</serverConf>
```

Le domaine MAIL FROM est le domaine utilisé dans les messages techniques rebonds. Cette adresse est définie dans l&#39;assistant de déploiement ou via l&#39;option NmsEmail_DefaultErrorAddr .

### Enregistrement SPF {#dns-configuration}

Un enregistrement SPF peut actuellement être défini sur un serveur DNS comme un enregistrement de type TXT (code 16) ou un enregistrement de type SPF (code 99). Un enregistrement SPF prend la forme d’une chaîne de caractères. Par exemple :

```
v=spf1 ip4:12.34.56.78/32 ip4:12.34.56.79/32 ~all
```

définit les deux adresses IP, 12.34.56.78 et 12.34.56.79, comme autorisées à envoyer des emails pour le domaine. **~all** signifie que toute autre adresse doit être interprétée comme un SoftFail.

Recommendations pour définir un enregistrement SPF :

* Ajouter **~all** (SoftFail) ou **-all** (Échec) à la fin pour rejeter tous les serveurs autres que ceux définis. Sans cela, les serveurs seront en mesure de forger ce domaine (avec une évaluation Neutre).
* Ne pas ajouter **ptr** (openspf.org recommande de ne pas le considérer comme coûteux et peu fiable).

>[!NOTE]
>
>En savoir plus sur SPF dans [cette section](/help/additional-resources/authentication.md#spf).

## Authentification

>[!NOTE]
>
>En savoir plus sur les différentes formes d’authentification des emails dans [cette section](/help/additional-resources/authentication.md).

### DKIM {#dkim-acc}

>[!NOTE]
>
>Pour les installations hébergées ou hybrides, si vous avez effectué une mise à niveau vers le [MTA amélioré](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-emails/sending-an-email/sending-with-enhanced-mta.html#sending-messages), la signature de l’authentification des emails DKIM est effectuée par celui-ci pour tous les messages et domaines.

Utilisation [DKIM](/help/additional-resources/authentication.md#dkim) avec Adobe Campaign Classic, les conditions préalables suivantes sont requises :

**Déclaration des options Adobe Campaign**: dans Adobe Campaign, la clé privée DKIM est basée sur un sélecteur DKIM et un domaine. Il n’est actuellement pas possible de créer plusieurs clés privées pour le même domaine/sous-domaine avec des sélecteurs différents. Il n&#39;est pas possible de définir quel domaine/sous-domaine de sélecteur doit être utilisé pour l&#39;authentification, ni dans la plateforme, ni dans l&#39;email. La plateforme sélectionnera également l’une des clés privées, ce qui signifie que l’authentification a de grandes chances d’échouer.

* Si vous avez configuré DomainKeys pour votre instance Adobe Campaign, vous devez simplement sélectionner **dkim** dans les [règles de gestion des domaines](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html#email-management-rules). Dans le cas contraire, suivez les mêmes étapes de configuration (clé privée/clé publique) que pour DomainKeys (qui a remplacé DKIM).
* Il est inutile d&#39;activer DomainKeys et DKIM pour un même domaine, DKIM étant une version améliorée de DomainKeys.
* Les domaines validant actuellement DKIM sont les suivants : AOL, Gmail.

## Feedback loop {#feedback-loop-acc}

Une boucle de rétroaction fonctionne en déclarant au niveau du FAI une adresse e-mail donnée pour une plage d’adresses IP utilisées pour l’envoi de messages. Le FAI enverra à cette boîte de réception, de la même manière que pour les messages de rebond, ces messages qui sont signalés par les destinataires comme spam. La plateforme doit être configurée pour bloquer les futures diffusions aux utilisateurs qui se sont plaints. Il est important de ne plus les contacter même s’ils n’ont pas utilisé le lien d’opt-out approprié. C’est sur la base de ces plaintes qu’un FAI ajoutera une adresse IP à sa liste bloquée. Selon le FAI, un taux de plainte d’environ 1 % entraînera lle blocage d’une adresse IP.

Un standard est en cours d’établissement pour définir le format des messages de feedback loop : l’[ARF (Abuse Feedback Reporting Format)](https://tools.ietf.org/html/rfc6650).

La mise en place d&#39;une feedback loop pour une instance suppose d&#39;avoir :

* une boîte mail dédiée à l&#39;instance, qui peut éventuellement être la boîte de mails rebonds,
* des adresses IP d&#39;envoi dédiées à l&#39;instance.

La mise en œuvre d’une feedback loop simple dans Adobe Campaign fait appel à la fonctionnalité de messages rebonds. La boîte email de feedback loop est utilisée comme boîte de rebond et une règle est définie pour détecter ces messages. Les adresses email des destinataires qui ont signalé le message comme indésirable seront ajoutées à la liste des adresses en quarantaine.

* Créez ou adaptez une règle de mails rebonds **Feedback_loop** dans **[!UICONTROL Administration>Gestion de campagne>Gestion des NP@I>Jeux de règles mail]** avec la raison **Refusé** et le type **Hard**.
* Si une boîte a été définie spécialement pour la feedback loop, définissez les paramètres pour relever son contenu en créant un nouveau compte externe de type Mails rebonds dans **[!UICONTROL Administration>Plateforme>Comptes externes]**.

Le mécanisme est immédiatement opérationnel pour traiter les notifications de plaintes. Pour vérifier le bon fonctionnement de la règle, vous pouvez temporairement désactiver les comptes afin qu&#39;ils ne relèvent pas ces messages, puis vérifier le contenu de la boîte de feedback loop manuellement. Sur le serveur, exécutez les commandes suivantes :

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

### À propos de List-Unsubscribe {#about-list-unsubscribe}

Ajouter un en-tête SMTP appelé **List-Unsubscribe** est obligatoire pour garantir une gestion optimale de la délivrabilité. À compter du 1er juin 2024, Yahoo et Gmail exigeront que les expéditeurs se conforment aux règles du Unsubscribe de liste en un clic. Pour comprendre comment configurer le désabonnement à la liste en un clic, voir ci-dessous.


Cet en-tête peut être utilisé comme alternative à l’icône &quot;Signaler comme SPAM&quot;. Il s’affichera sous forme de lien de désabonnement dans l’interface de messagerie.

L’utilisation de cette fonctionnalité vous aide à protéger votre réputation et les commentaires seront exécutés comme un désabonnement.

Pour utiliser List-Unsubscribe, vous devez entrer une ligne de commande similaire à celle-ci :

```
List-Unsubscribe: <mailto: client@newsletter.example.com?subject=unsubscribe?body=unsubscribe>
```

>[!CAUTION]
>
>L&#39;exemple ci-dessus est basé sur la table des destinataires. Si l&#39;implémentation de la base de données est faite à partir d&#39;une autre table, pensez à reformuler la ligne de commande avec l&#39;information correcte.

La ligne de commande suivante peut-être utilisée pour créer un **List-Unsubscribe** dynamique :

```
List-Unsubscribe: <mailto: %=errorAddress%?subject=unsubscribe%=message.mimeMessageId%>
```

Gmail, Outlook.com et Microsoft Outlook prennent en charge cette méthode et un bouton de désabonnement est disponible directement dans leur interface. Cette technique réduit le taux de plaintes.

Vous pouvez mettre en oeuvre le **List-Unsubscribe** par :

* Directement [l&#39;ajout de la ligne de commande dans le modèle de diffusion](#adding-a-command-line-in-a-delivery-template)
* [Créer une règle de typologie](#creating-a-typology-rule)

### Ajouter une ligne de commande dans un modèle de diffusion {#adding-a-command-line-in-a-delivery-template}

La ligne de commande doit être ajoutée dans la section additionnelle de l&#39;en-tête SMTP de l&#39;email.

Cet ajout peut se faire dans chaque email, ou dans les modèles de diffusion existants. Vous pouvez aussi créer un nouveau modèle de diffusion qui inclue cette fonctionnalité.

1. List-Unsubscribe: <mailto:unsubscribe@domain.com>
Cliquez sur le lien de désabonnement pour ouvrir le client de messagerie par défaut de l’utilisateur. Cette règle de typologie doit être ajoutée dans une typologie utilisée pour créer un email.

2. List-Unsubscribe: <https://domain.com/unsubscribe.jsp>
Un clic sur le lien unsubscribe redirige l’utilisateur vers votre formulaire de désabonnement.
   ![Image.](https://git.corp.adobe.com/storage/user/38257/files/3b46450f-2502-48ed-87b9-f537e1850963)


### Créer une règle de typologie {#creating-a-typology-rule}

La règle de typologie doit contenir le script qui génère la ligne de commande et être inclue dans l&#39;en-tête de l&#39;email.

>[!NOTE]
>
>La création d&#39;une règle de typologie est recommandée : la fonctionnalité List-Unsubscribe sera automatiquement ajoutée à chaque email.

>[!NOTE]
>
>Découvrez comment créer des règles de typologie dans Adobe Campaign Classic dans [cette section](https://experienceleague.adobe.com/docs/campaign-classic/using/orchestrating-campaigns/campaign-optimization/about-campaign-typologies.html#typology-rules).

### Désabonnement à la liste en un clic

À compter du 1er juin 2024, Yahoo et Gmail exigeront que les expéditeurs se conforment au List-Unsubscribe en un clic. Pour se conformer à l’exigence du Unsubscribe de liste en un clic, les expéditeurs doivent :

1. Ajoutez dans un &quot;List-Unsubscribe-Post : List-Unsubscribe=One-Click&quot;.
2. Inclure un lien de désabonnement d’URI
3. Prise en charge de la réception de la réponse du POST HTTP par le récepteur, prise en charge par Adobe Campaign.

Pour configurer le désabonnement à la liste en un clic directement :

・ Ajoutez dans l&#39;application web &quot;Désabonner les destinataires sans clic&quot; suivante : 
1. Accédez à Ressources -> On-line -> Applications Web .
2. Télécharger le fichier XML &quot;No-click&quot; &quot;Désabonner les destinataires&quot; ・ Configurer List-Unsubscribe et List-Unsubscribe-Post
1. Accédez à la section SMTP des Propriétés de la diffusion.
2. Sous En-têtes SMTP supplémentaires, saisissez les lignes de commande (chaque en-tête doit se trouver sur une ligne distincte) :

List-Unsubscribe-Post : List-Unsubscribe=One-Click List-Unsubscribe : &lt;https: domain.com=&quot;&quot; webapp=&quot;&quot; unsubnoclick=&quot;&quot; id=&quot;&lt;%=&quot; recipient.cryptidcamp=&quot;&quot;>>, &lt;mailto: erroraddress=&quot;&quot; subject=&quot;unsubscribe%=message.mimeMessageId%&quot;>

L’exemple ci-dessus permettra l’activation du Unsubscribe de liste en un clic pour les FAI qui prennent en charge l’option Un clic, tout en s’assurant que les destinataires qui ne prennent pas en charge le désabonnement de liste d’URL peuvent toujours demander un désabonnement par courrier électronique.

Cliquez ici pour découvrir comment configurer le désabonnement à la liste en un clic via la règle de typologie.

## Optimisation des emails {#email-optimization}

### SMTP {#smtp}

SMTP (Simple mail transfer protocol) est une norme Internet pour la transmission des emails.

Les erreurs SMTP qui ne sont pas vérifiées par une règle sont répertoriées dans le **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Gestion des échecs]** > **[!UICONTROL Qualification des logs de diffusion]** dossier. Ces messages d’erreur sont interprétés par défaut comme des erreurs soft inatteignables.

Les erreurs les plus courantes doivent être identifiées et une règle correspondante doit être ajoutée dans **[!UICONTROL Administration]** > **[!UICONTROL Campaign Management]** > **[!UICONTROL Gestion des échecs]** > **[!UICONTROL Jeux de règles de messagerie]** si vous souhaitez qualifier correctement les commentaires des serveurs SMTP. Sans cela, la plateforme effectuera des reprises inutiles (en cas d&#39;utilisateurs inconnus) ou mettra incorrectement certains destinataires en quarantaine après un nombre donné de tests.

### Adresses IP dédiées {#dedicated-ips}

Adobe fournit une stratégie IP dédiée pour chaque client avec une adresse IP en phase de montée (ramp-up) afin d&#39;établir une réputation et optimiser les performances de diffusion.
