---
title: Processus de demande de certificat SSL
description: Découvrez comment installer des certificats SSL sur les sous-domaines délégués à Adobe.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 8a78abd3-afba-49a7-a2ae-8b2c75326749
source-git-commit: 0be68f5674904aa105985a6e5fc4771c41f7fe48
workflow-type: tm+mt
source-wordcount: '2124'
ht-degree: 1%

---

# Processus de demande de certificat SSL

Une fois que vous avez délégué un domaine à Adobe pour l’envoi d’e-mails (voir [Configuration du nom de domaine](/help/additional-resources/ac-domain-name-setup.md)), Adobe crée et utilise certains sous-domaines pour des fonctions spécifiques.

Par exemple, si vous avez délégué *email.example.com* à Adobe pour l&#39;envoi d&#39;emails, Adobe crée des sous-domaines tels que :
* *t.email.example.com* - pour les liens de tracking
* *m.email.example.com* - pour les pages miroir
* *res.email.example.com* - pour les ressources hébergées (telles que les images)

Il est recommandé de **sécuriser ces domaines via SSL (HTTPS)**. En effet, les liens non sécurisés (HTTP) sont vulnérables à l&#39;interception et signaleront les avertissements sur les navigateurs modernes.

Pour installer des certificats SSL sur ces sous-domaines, le processus implique de demander un fichier CSR et d’acheter ensuite des certificats SSL à Adobe pour installation ou renouvellement.

>[!CAUTION]
>
>Avant d’installer un certificat SSL, vous devez connaître les conditions préalables répertoriées sur [cette page](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renewing-subdomain-certificate.html?lang=fr#installing-ssl-certificate).
>
>Adobe ne prend en charge que les certificats 2 048 bits maximum. Les certificats 4 096 bits ne sont pas encore pris en charge.

## Glossaire

| Terme | Description |
|--- |--- |
| Autorité de certification (CA) | Fournisseur de certificats SSL qui émet des certificats numériques à des organisations ou à des individus après avoir vérifié leur identité, tel que DigiCert, Symantec, etc.<ul><li>Une autorité de certification approuvée est généralement considérée comme une autorité de certification tierce qui émet un certificat racine.</li><li>Si le certificat est signé par la même organisation/société qui utilise le certificat, il est classé comme autorité de certification non approuvée même s’il s’agit de certificats SSL, tels que des certificats auto-signés.</li></ul> |
| Certificat de chaîne | Un certificat qui comprend un certificat racine et un ou plusieurs certificats intermédiaires est appelé certificat en chaîne (ou chaîné). |
| CSR (Certificate Signing Request) | Bloc de texte codé fourni à une autorité de certification lors de la demande d’un certificat SSL. Il est généralement généré sur le serveur sur lequel le certificat est installé. |
| DER (règles d’encodage distinctes) | Un type d’extension de certificat. L’extension .der est utilisée pour les certificats codés DER binaires. Ces fichiers peuvent également prendre en charge l’extension .cer ou .crt. |
| Certificat EV (validation étendue) | Un certificat EV est un nouveau type de certificat conçu pour empêcher les attaques par phishing. Elle nécessite une validation étendue de votre entreprise et de la personne qui commande le certificat. |
| Certificat de haute assurance | Les certificats de haute assurance sont délivrés par l&#39;autorité de certification après vérification de la propriété du nom de domaine et de l&#39;enregistrement valide de l&#39;entreprise. |
| Autorité de certification intermédiaire | Autorité de certification des certificats intermédiaires inclus dans un certificat de chaîne. |
| Certificat intermédiaire | Une autorité de certification émet des certificats sous la forme d’une arborescence. Le certificat racine est le certificat le plus élevé de l’arborescence. Tout certificat entre votre certificat et le certificat racine est appelé certificat de chaîne ou intermédiaire. |
| Certificat de faible assurance | Un certificat de faible assurance, également appelé certificat validé par le domaine, inclut uniquement le nom de domaine dans le certificat (et non le nom de l’entreprise ou de l’organisation). |
| PEM (Privacy Enhanced Mail) | Un certificat avec une extension .pem contenant des données ASCII (Base64). Ces certificats commencent par une ligne « - - - - - COMMENCER LE CERTIFICAT - - - - ». |
| Certificat racine | Une autorité de certification émet des certificats sous la forme d’une arborescence. Le certificat racine est le certificat le plus élevé de l’arborescence. |
| SAN (autre nom du sujet) | Les autres noms de sujet sont des noms d’hôte supplémentaires (sites, adresses IP, noms communs, etc.) qui doivent être signés dans le cadre d’un certificat SSL unique. |
| Certificat auto-signé | Certificat signé par la personne qui le crée plutôt que par une autorité de certification approuvée. Les certificats auto-signés peuvent permettre le même niveau de chiffrement qu’un certificat signé par une autorité de certification, mais il existe deux inconvénients majeurs :<ul><li>La connexion d’un visiteur peut être piratée, ce qui permet à un attaquant de visualiser toutes les données envoyées (ce qui va à l’encontre de l’objectif de chiffrement de la connexion)</li><li> Le certificat ne peut pas être révoqué comme un certificat approuvé le peut.</li></ul> |
| SSL (couche de socket sécurisée) | Technologie de sécurité standard permettant d’établir un lien chiffré entre un serveur web et un navigateur. |
| Certificat de caractère générique | Un certificat avec caractère générique peut sécuriser un nombre illimité de sous-domaines de premier niveau sur un seul nom de domaine, tel que *.adobe.com. |

## Principales étapes

1. Demandez un fichier de demande de signature de certificat (CSR) et fournissez les informations requises (pays, état, ville, nom de l’organisation, nom de l’entité organisationnelle, etc.) à Adobe.
1. Validez le fichier de CSR généré par Adobe et vérifiez que toutes les informations fournies sont correctes.
1. Utilisez les détails de la CSR pour générer un certificat signé par une autorité de certification approuvée<!--taking care of asking for using the subjectAltName SSL extension (SAN) if it is for several domain names, and get/purchase the resulting certificate (ideally) in PEM format for Apache server-->.
1. Validez le certificat SSL et vérifiez qu’il correspond à la demande de signature de certificat.
1. Fournissez le certificat SSL à Adobe, qui l’installera.
1. Vérifiez que le certificat SSL est correctement installé pour chaque sous-domaine sécurisé.
1. Surveillez la période de validité du certificat SSL.
1. Mettez à jour toute configuration spécifique dans Adobe Campaign.

## Processus détaillé

### Conditions préalables

Vous devez identifier les noms de domaine et les fonctions (tracking, pages miroir, webapps, etc.) à sécuriser.
>[!NOTE]
>
>Adobe peut vous aider à définir les noms de domaine et les fonctions à impliquer. Pour plus d’informations, contactez l’équipe chargée de votre compte Adobe.

### Étape 1 - Obtenir un fichier CSR

Pour obtenir un fichier CSR (Certificate Signing Request), procédez comme suit.

* Si vous avez accès au Panneau de Contrôle [&#128279;](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=fr), suivez les instructions de [cette page](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renewing-subdomain-certificate.html?lang=fr#subdomains-and-certificates) pour générer et télécharger un fichier CSR à partir du Panneau de Contrôle.

* Sinon, créez un ticket d’assistance via https://adminconsole.adobe.com/ pour obtenir un fichier CSR de l’assistance clientèle d’Adobe pour le ou les sous-domaines requis.

Voici quelques bonnes pratiques à suivre :

* Déclenchez une requête par sous-domaine délégué.
* Il est possible de combiner plusieurs sous-domaines en une seule demande de signature de certificat (CSR), mais uniquement dans le même environnement. Par exemple, dans Campaign Classic, le serveur marketing, le [serveur de mid-sourcing](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/install-campaign-on-prem/mid-sourcing-server.html) et l’[instance d’exécution](https://experienceleague.adobe.com/docs/campaign-classic/using/transactional-messaging/configure-transactional-messaging/configuring-instances.html#execution-instance) sont trois environnements distincts.
* Vous devez obtenir une nouvelle demande de signature de certificat avant tout renouvellement de certificat SSL. N’utilisez pas un ancien fichier de CSR datant d’un an ou plus.

Vous devrez fournir les informations suivantes.

>[!CAUTION]
>
>Tous les champs indiqués dans les tableaux ci-dessous doivent être renseignés. Dans le cas contraire, la demande de signature de certificat ne peut pas être traitée.

**Informations à fournir avec l’aide de l’équipe d’Adobe :**

| Informations à fournir | Exemple de valeur | Remarque |
|--- |--- |--- |
| Nom du client ou de la cliente | My Company Inc. (en anglais) | Nom de votre organisation. Ce champ est utilisé par Adobe pour effectuer le suivi de votre demande (il ne fait pas partie du certificat CSR/SSL). |
| URL de l’environnement Adobe Campaign | https://client-mid-prod1.campaign.adobe.com | URL de l’instance Adobe Campaign. |
| Nom courant [CN] | t.subdomain.customer.com | Il peut s’agir de l’un des domaines pertinents, mais généralement du domaine de suivi. |
| Autre nom du sujet [SAN] | t.subdomain.customer.com | Veillez à inclure le sous-domaine de suivi en tant que SAN. |
| Autre nom du sujet [SAN] | m.subdomain.customer.com | |
| Autre nom du sujet [SAN] | res.subdomain.customer.com | |

**Informations à fournir par votre équipe interne IT/SSL :**

| Informations à fournir | Exemple de valeur | Remarque |
|--- |--- |--- |
| Pays [C] | US | Il doit s&#39;agir d&#39;un code à deux lettres. Accédez à la liste complète des pays [ici](https://www.ssl.com/csrs/country_codes/).</br>*Remarque : pour le Royaume-Uni, utilisez GB (pas UK).* |
| État (ou nom de province) [ST] | Illinois | Le cas échéant. La valeur doit être un nom complet, et non une abréviation. |
| Nom de la ville/localité [L] | Chicago | |
| Nom de l’organisation [O] | ACME | |
| Nom de l&#39;entité organisationnelle [UO] | IT | |

>[!NOTE]
>
>Remplacez « subdomain.customer.com » par votre sous-domaine délégué et les autres exemples de valeurs par les valeurs appropriées.

### Étape 2 - Valider le fichier CSR

Après avoir envoyé votre demande avec les informations pertinentes, Adobe génère et vous fournit un fichier de demande de signature de certificat (CSR).

Le texte du fichier CSR obtenu doit commencer par **« -----COMMENCER LA DEMANDE DE CERTIFICAT----- »**.

Une fois que vous avez reçu le fichier CSR d’Adobe, procédez comme suit :

1. Copiez et collez le texte du fichier CSR dans un décodeur en ligne tel que https://www.sslshopper.com/csr-decoder.html, <!--https://www.certlogik.com/decoder/,--> ou https://www.entrust.net/ssl-technical/csr-viewer.cfm.
Vous pouvez également utiliser la commande *OpenSSL* localement sur une machine Linux.
1. Vérifiez que toutes les vérifications ont réussi.
1. Vérifiez que les paramètres et noms de domaine appropriés sont inclus.
1. Vérifiez que toutes les autres données correspondent aux détails que vous avez fournis lors de la soumission de votre demande.

### Étape 3 : générer le certificat SSL

Une fois le fichier CSR fourni, vous devez acheter et générer un certificat SSL pour les domaines appropriés à l’aide du fichier CSR.

* Le certificat SSL :
   * doit être au format Apache PEM ;
   * ne doit pas dépasser 2 048 bits ;
   * doit être signé par une autorité de certification valide;
   * doit inclure tous les SAN (noms alternatifs du sujet) comme indiqué dans le fichier CSR.
* S’il existe un ou plusieurs certificats intermédiaires, vous devez fournir le certificat racine et tous les certificats intermédiaires à Adobe.
* Vous pouvez définir n’importe quelle période de validité de certificat, mais Adobe recommande de la choisir suffisamment longtemps (deux ans par exemple).

>[!NOTE]
>
>Si vous utilisez vos propres outils internes ou un portail fourni par une autorité de certification pour demander le certificat, veillez à utiliser les mêmes détails que ceux fournis dans la demande de signature de certificat afin d’éviter tout retard ou incohérence dans le processus de génération du certificat.

### Étape 4 : validation du certificat SSL

Une fois le certificat SSL généré, vous devez le valider avant de l’envoyer à Adobe. Procédez comme suit :

1. Assurez-vous que le certificat possède l’extension .pem. Si ce n’est pas le cas, convertissez-le au format PEM. Vous pouvez effectuer la conversion à l’aide de *OpenSSL*.
1. Vérifiez que le certificat commence par **»-----BEGIN CERTIFICATE----- »**.
1. Copiez le texte du certificat dans un décodeur en ligne, tel que https://www.sslshopper.com/certificate-decoder.html ou https://www.entrust.net/ssl-technical/csr-viewer.cfm.
Vous pouvez également utiliser la commande *OpenSSL* localement sur une machine Linux. Pour plus d&#39;informations, consultez [cette page externe](https://www.shellhacks.com/decode-ssl-certificate/).
1. Assurez-vous que le certificat est résolu correctement, y compris le nom commun, le SAN, l’émetteur et la période de validité.
1. Si la vérification du certificat SSL réussit, vérifiez que le certificat correspond à la demande de signature de certificat à l’aide de [ce site web](https://www.sslshopper.com/certificate-key-matcher.html) : sélectionnez **Vérifier si une demande de signature de certificat et un certificat correspondent**, et saisissez votre certificat et votre demande de signature de certificat dans les champs correspondants. Ils devraient correspondre.

### Étape 5 : demander l’installation du certificat SSL

* Si vous avez accès au Panneau de Contrôle [&#128279;](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=fr), suivez les instructions de [cette page](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renewing-subdomain-certificate.html?lang=fr#installing-ssl-certificate) pour charger le certificat vers le Panneau de Contrôle.

* Sinon, créez un autre ticket d’assistance via https://adminconsole.adobe.com/ pour demander à Adobe d’installer le certificat sur le ou les serveurs Adobe.

Vous devez fournir les éléments suivants :

* Le fichier de certificat, le certificat racine et les certificats intermédiaires (joints au ticket), de préférence au format Apache PEM.
* Numéro du ticket d’assistance précédent levé pour la demande de signature de certificat.
* Les mêmes données que celles fournies pour le ticket de la CSR (notamment le nom commun, l’URL de l’instance, l’état, la ville/localité, le nom de l’organisation, le nom de l’unité d’organisation, etc.).

### Étape 6 : test de l’installation du certificat SSL

Une fois le certificat SSL installé et confirmé par l’assistance clientèle d’Adobe, assurez-vous qu’il a été correctement installé pour toutes les URL.

Effectuez les tests ci-dessous avant de fermer le ticket d’installation SSL. Veillez également à mettre à jour toute configuration spécifique comme indiqué dans [cette section](#update-configuration).

Accédez aux URL suivantes dans votre navigateur (remplacez « subdomain.customer.com » par votre sous-domaine) :

* https://subdomain.customer.com/r/test (pour les [applications web](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-applications/about-web-applications.html?lang=fr) sous-domaines uniquement - ne s’applique pas aux sous-domaines d’e-mail)
* https://t.subdomain.customer.com/r/test
* https://m.subdomain.customer.com/r/test
* https://res.subdomain.customer.com/r/test

Un résultat réussi fournit des informations sur l’environnement et la barre d’adresse dans l’URL indique que la connexion est sécurisée. Par exemple, le message suivant s’affiche dans Google Chrome :

![](../../help/assets/ssl-google-successful-result.png)

Si le certificat SSL n’est pas installé correctement, l’avertissement suivant s’affiche :

![](../../help/assets/ssl-google-unsuccessful-result.png)

### Étape 7 - Vérifier la période de validité du certificat

Vous pouvez vérifier la période de validité du certificat dans votre navigateur. Par exemple, dans Google Chrome, cliquez sur **Sécuriser** > **Certificat**.

Il est de votre responsabilité de vérifier la période de validité. Adobe vous recommande de mettre en œuvre un processus pour surveiller l’expiration des certificats. Pour en savoir plus sur ce qui se passe lorsque votre certificat SSL expire, consultez [cet article](https://www.thesslstore.com/blog/what-happens-when-your-ssl-certificate-expires/).

* Créez un ticket d’assistance pour demander un certificat mis à jour au moins deux semaines avant la date d’expiration du certificat. Vous n’avez pas besoin de demander une demande de signature de certificat supplémentaire, sauf si les détails de la demande ont changé.

* Si vous avez accès au Panneau de Contrôle [&#128279;](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=fr) et si votre environnement est hébergé par Adobe dans un environnement AWS, vous pouvez utiliser le Panneau de Contrôle pour renouveler le certificat avant son expiration. En savoir plus dans [cette section](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/monitoring-ssl-certificates.html#monitoring-certificates).

### Étape 8 - Mettre à jour toute configuration spécifique {#update-configuration}

Une fois que vous êtes certain que les certificats SSL demandés sont correctement installés, vous pouvez mettre à jour toutes les références dans Adobe Campaign de HTTP vers HTTPS.

>[!NOTE]
>
>Pour Campaign Classic, les URL à mettre à jour se trouvent principalement dans l’[assistant de déploiement](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/initial-configuration/deploying-an-instance.html#deployment-wizard) et dans l’[Comptes externes](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/accessing-external-database/external-accounts.html?lang=fr) (suivi, page miroir et domaines des ressources publiques). Pour Campaign Standard, voir [Configuration du branding](https://experienceleague.adobe.com/docs/campaign-standard/using/administrating/application-settings/branding.html#about-brand-identity).

Une fois les configurations mises à jour, les nouveaux e-mails seront envoyés avec des URL HTTPS plutôt que HTTP. Pour vérifier que les URL sont désormais sécurisées, vous pouvez rapidement effectuer les tests suivants :

* Chargez une image à partir d’Adobe Campaign. Une fois l’image téléchargée, l’URL renvoyée doit être HTTPS.
* Créez une diffusion e-mail test comprenant un lien de page miroir, des images, du texte et un lien de désinscription. Envoyez l’e-mail à un ID d’e-mail externe (tel que votre adresse Gmail). Une fois reçu, ouvrez l’e-mail et assurez-vous que tous les liens qu’il contient s’ouvrent correctement dans leur formulaire HTTPS (et non HTTP), sans avertissements ni erreurs de certificat SSL.

## Ressources spécifiques au produit

**Campaign Classic**

* [Panneau de Contrôle : Ajout de certificats SSL (tutoriel)](https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/adding-ssl-certificates.html) - Découvrez comment ajouter des certificats SSL pour sécuriser vos sous-domaines.

**Campaign Standard**

* [Panneau de Contrôle : Ajout de certificats SSL (tutoriel)](https://experienceleague.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/adding-ssl-certificates.html) - Découvrez comment ajouter des certificats SSL pour sécuriser vos sous-domaines.
