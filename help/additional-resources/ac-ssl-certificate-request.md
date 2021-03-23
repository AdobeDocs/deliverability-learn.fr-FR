---
title: Processus de demande de certificat SSL
description: Découvrez comment installer des certificats SSL sur les sous-domaines que vous avez délégués à l’Adobe.
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
source-wordcount: '2269'
ht-degree: 2%

---


# Processus de demande de certificat SSL

Une fois que vous avez délégué un domaine à l&#39;Adobe pour l&#39;envoi de courriers électroniques (voir [Configuration du nom de domaine](/help/additional-resources/ac-domain-name-setup.md)), l&#39;Adobe crée et utilise certains sous-domaines pour des fonctions spécifiques.

Par exemple, si vous avez délégué *email.example.com* à l’Adobe pour l’envoi de courriels, l’Adobe crée des sous-domaines tels que :
* *t.email.example.com* - pour le suivi des liens
* *m.email.example.com* - pour les pages miroir
* *res.email.example.com* - pour les ressources hébergées (telles que les images)

Il est recommandé de **sécuriser ces domaines via SSL (HTTPS)**. En effet, les liens non sécurisés (HTTP) sont vulnérables à l’interception et signalent des avertissements sur les navigateurs modernes.

Pour installer des certificats SSL sur ces sous-domaines, le processus implique de demander un fichier CSR et d’acheter ensuite des certificats SSL pour que l’Adobe les installe ou les renouvelle.

>[!CAUTION]
>
>Avant d’installer un certificat SSL, assurez-vous que vous connaissez les conditions préalables répertoriées dans [cette page](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renewing-subdomain-certificate.html#installing-ssl-certificate).
>
>Adobe ne prend en charge que les certificats jusqu’à 2 048 bits. Les certificats 4096 bits ne sont pas encore pris en charge.

## Glossaire 

| Terme | Description |
|--- |--- |
| Autorité de certification (Certificate Authority) | Fournisseur de certificats SSL qui délivre des certificats numériques à des organisations ou à des individus après vérification de leur identité, tels que DigiCert, Symantec, etc.<ul><li>Une autorité de certification approuvée est généralement considérée comme une autorité de certification tierce qui émet un certificat racine.</li><li>Si le certificat est signé par la même organisation/société qui utilise le certificat, il est classé comme autorité de certification non approuvée même s’il s’agit de certificats SSL, tels que des certificats auto-signés.</li></ul> |
| Certificat de chaîne | Un certificat qui comprend un certificat racine et un ou plusieurs certificats intermédiaires est appelé certificat de chaîne (ou chaîné). |
| CSR (Demande de signature de certificat) | Bloc de texte codé remis à une autorité de certification lors de la demande d’un certificat SSL. Il est généralement généré sur le serveur sur lequel le certificat est installé. |
| DER (Règles de codage distinctes) | Type d’extension de certificat. L’extension .der est utilisée pour les certificats codés DER binaires. Ces fichiers peuvent également prendre en charge l’extension .cer ou .crt. |
| Certificat EV (validation étendue) | Un certificat EV est un nouveau type de certificat conçu pour prévenir les attaques par hameçonnage. Il nécessite une validation étendue de votre entreprise et de la personne qui commande le certificat. |
| Certificat de haute assurance | Les certificats à haute assurance sont émis par l’AC après vérification de la propriété du nom de domaine et de l’enregistrement professionnel valide. |
| Autorité de certification intermédiaire | Autorité de certification des certificats intermédiaires inclus dans un certificat de chaîne. |
| Certificat intermédiaire | Une autorité de certification émet des certificats sous la forme d’une arborescence. Le certificat racine est le certificat le plus élevé de l&#39;arborescence. Tout certificat entre votre certificat et le certificat racine est appelé certificat de chaîne ou certificat intermédiaire. |
| Certificat de faible assurance | Un certificat à faible assurance, également appelé certificat validé par un domaine, inclut uniquement le nom de domaine dans le certificat (et non le nom de l’entreprise/de l’organisation). |
| PEM (Privacy Enhanced Mail) | Certificat avec une extension .pem contenant des données ASCII (Base64). Ces certificats sont débuts avec une ligne &quot; - - - - - CERTIFICAT DE DÉBUT - - -&quot;. |
| Certificat racine | Une autorité de certification émet des certificats sous la forme d’une arborescence. Le certificat racine est le certificat le plus élevé de l&#39;arborescence. |
| SAN (Autre nom du sujet) | Les noms alternatifs en question sont d&#39;autres noms d&#39;hôtes (sites, adresses IP, noms communs, etc.) qui doit être signé dans le cadre d’un certificat SSL unique. |
| Certificat auto-signé | Certificat signé par la personne qui le crée plutôt qu’une autorité de certification approuvée. Les certificats auto-signés peuvent permettre le même niveau de chiffrement qu’un certificat signé par une autorité de certification, mais il existe deux inconvénients majeurs :<ul><li>Un visiteur peut être piraté, ce qui permet à un attaquant de vue de toutes les données envoyées (ce qui va à l&#39;encontre de l&#39;objectif de cryptage de la connexion).</li><li> Le certificat ne peut pas être révoqué comme un certificat approuvé le peut.</li></ul> |
| SSL (Secure Sockets Layer) | Technologie de sécurité standard permettant d’établir un lien chiffré entre un serveur Web et un navigateur. |
| Certificat générique | Un certificat générique peut sécuriser un nombre illimité de sous-domaines de premier niveau sur un seul nom de domaine, tel que *.adobe.com. |

## Principales étapes

1. Demandez un fichier de demande de signature de certificat (CSR) et fournissez les informations requises (pays, état, ville, nom de l’organisation, nom de l’unité organisationnelle, etc.) à l&#39;Adobe.
1. Validez le fichier CSR généré par l’Adobe et vérifiez que toutes les informations que vous avez fournies sont correctes.
1. Utilisez les détails de la demande de signature de certificat pour générer un certificat signé par une autorité de certification approuvée <!--taking care of asking for using the subjectAltName SSL extension (SAN) if it is for several domain names, and get/purchase the resulting certificate (ideally) in PEM format for Apache server-->.
1. Validez le certificat SSL et vérifiez qu’il correspond au CSR.
1. Fournissez le certificat SSL à l’Adobe, qui va l’installer.
1. Vérifiez que le certificat SSL est correctement installé pour chaque sous-domaine sécurisé.
1. Surveillez la période de validité du certificat SSL.
1. Mettez à jour toute configuration spécifique dans Adobe Campaign.

## Processus détaillé

### Conditions préalables

Vous devez identifier les noms de domaine et les fonctions (suivi, pages miroir, applications Web, etc.) pour sécuriser.
>[!NOTE]
>
>L&#39;Adobe peut aider à définir les noms de domaine et les fonctions à impliquer. Pour plus d’informations, contactez votre responsable de succès client Adobe.

### Etape 1 - Obtention d’un fichier CSR

Pour obtenir un fichier CSR (Certificate Signing Request), suivez les étapes ci-dessous.

* Si vous avez accès au [Panneau de Contrôle](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html?lang=fr), suivez les instructions de [cette page](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renewing-subdomain-certificate.html#subdomains-and-certificates) pour générer et télécharger un fichier CSR à partir du Panneau de Contrôle.

* Sinon, créez un ticket d’assistance via https://adminconsole.adobe.com/ pour obtenir un fichier CSR auprès du service à la clientèle d’Adobe pour le ou les sous-domaines requis.

Voici quelques bonnes pratiques à suivre :

* Générer une requête par sous-domaine délégué.
* Il est possible de combiner plusieurs sous-domaines en une seule demande de signature de certificat, mais uniquement au sein d’un même environnement. Par exemple, en Campaign Classic, le serveur marketing, le [serveur de midsourcing](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/mid-sourcing-server.html) et l&#39;[instance d&#39;exécution](https://experienceleague.adobe.com/docs/campaign-classic/using/transactional-messaging/instance-configuration/creating-a-shared-connection.html) sont trois environnements distincts.
* Vous devez obtenir un nouveau CSR avant tout renouvellement de certificat SSL. N’utilisez pas un ancien fichier CSR d’il y a un an ou plus.

Vous devrez fournir les informations suivantes.

>[!CAUTION]
>
>Tous les champs indiqués dans les tableaux ci-dessous doivent être remplis. Sinon, la demande de signature de certificat ne peut pas être traitée.

**Informations à fournir avec l&#39;assistance de l&#39;équipe d&#39;Adobe :**

| Informations à fournir | Exemple de valeur | Remarque |
|--- |--- |--- |
| Nom du client | Ma Société Inc. | Nom de votre organisation. Ce champ est utilisé par l’Adobe pour le suivi de votre requête (il ne fera pas partie du certificat CSR/SSL). |
| URL de l’Environnement Adobe Campaign | https://client-mid-prod1.campaign.adobe.com | URL de l’instance Adobe Campaign. |
| Nom commun [CN] | t.subdomain.customer.com | Il peut s’agir de n’importe quel domaine pertinent, mais généralement du domaine de suivi. |
| Autre nom du sujet [SAN] | t.subdomain.customer.com | Veillez à inclure le sous-domaine de suivi en tant que SAN. |
| Autre nom du sujet [SAN] | m.subdomain.customer.com |
| Autre nom du sujet [SAN] | res.subdomain.customer.com |

**Informations à fournir par votre équipe interne IT/SSL :**

| Informations à fournir | Exemple de valeur | Remarque |
|--- |--- |--- |
| Pays [C] | US | Il doit s’agir d’un code à deux lettres. Accédez à la liste complète du pays [ici](https://www.ssl.com/csrs/country_codes/).</br>*Remarque : Pour le Royaume-Uni, utilisez GB (et non UK).* |
| Etat (ou nom de la province) [ST] | Illinois | Le cas échéant. La valeur doit être un nom complet et non abrégé. |
| Nom de la ville/localité [L] | Chicago |
| Nom de l&#39;organisation [O] | ACME |
| Nom de l&#39;unité organisationnelle [OU] | IT |

>[!NOTE]
>
>Remplacez &quot;subdomain.customer.com&quot; par votre sous-domaine délégué, et les autres exemples de valeurs par les valeurs appropriées.

### Étape 2 - Validation du fichier CSR

Après avoir envoyé votre demande avec les informations pertinentes, l’Adobe génère et vous fournit un fichier CSR (Certificate Signing Request).

Le texte du fichier CSR résultant doit être début avec **&quot;—BEGIN CERTIFICATE REQUEST—&quot;**.

Une fois que vous avez reçu le fichier CSR de l’Adobe, procédez comme suit :

1. Copiez et collez le texte du fichier CSR dans un décodeur en ligne tel que https://www.sslshopper.com/csr-decoder.html, <!--https://www.certlogik.com/decoder/,--> ou https://www.entrust.net/ssl-technical/csr-viewer.cfm.
Vous pouvez également utiliser la commande *OpenSSL* localement sur une machine Linux. Pour plus d&#39;informations à ce sujet, consultez [cette page externe](https://www.question-defense.com/2009/09/22/use-openssl-to-verify-the-contents-of-a-csr-before-submitting-for-a-ssl-certificate).
1. Vérifiez que toutes les vérifications ont réussi.
1. Vérifiez que les paramètres et les noms de domaine appropriés sont inclus.
1. Vérifiez que toutes les autres données correspondent aux détails que vous avez fournis lors de l’envoi de votre demande.

### Etape 3 - Génération du certificat SSL

Une fois le fichier CSR fourni, vous devez acheter et générer un certificat SSL pour les domaines appropriés à l’aide du fichier CSR.

* Certificat SSL :
   * doit être au format PEM Apache ;
   * ne doit pas dépasser 2 048 bits ;
   * doit être signée par une autorité de certification valide (autorité de certification);
   * doit inclure tous les SAN (sous-noms alternatifs) tels que mentionnés dans le fichier CSR.
* S’il existe un ou plusieurs certificats intermédiaires, vous devez fournir le certificat racine et tous les certificats intermédiaires à l’Adobe.
* Vous pouvez définir n’importe quelle période de validité du certificat, mais l’Adobe recommande de la choisir suffisamment longtemps (deux ans par exemple).

>[!NOTE]
>
>Si vous utilisez vos propres outils internes ou un portail fourni par une autorité de certification pour demander le certificat, veillez à utiliser les mêmes détails que ceux fournis dans la demande de signature de certificat pour éviter tout retard ou toute incohérence dans le processus de génération de certificat.

### Etape 4 - Validation du certificat SSL

Une fois le certificat SSL généré, vous devez le valider avant de l’envoyer à l’Adobe. Procédez comme suit :

1. Assurez-vous que le certificat possède l’extension .pem. Si ce n’est pas le cas, convertissez-le au format PEM. Vous pouvez effectuer la conversion à l’aide de *OpenSSL*.
1. Confirmez que le certificat début avec **&quot;—BEGIN CERTIFICATE—&quot;**.
1. Copiez le texte du certificat dans un décodeur en ligne, tel que https://www.sslshopper.com/certificate-decoder.html ou https://www.entrust.net/ssl-technical/csr-viewer.cfm.
Vous pouvez également utiliser la commande *OpenSSL* localement sur une machine Linux. Pour plus d&#39;informations à ce sujet, consultez [cette page externe](https://www.shellhacks.com/decode-ssl-certificate/).
1. Assurez-vous que le certificat est correctement résolu, y compris le nom commun, le SAN, l&#39;émetteur et la période de validité.
1. Si la vérification du certificat SSL a réussi, vérifiez que le certificat correspond à la CSR à l’aide de [ce site Web](https://www.sslshopper.com/certificate-key-matcher.html) : sélectionnez **Vérifier si un CSR et un certificat correspondent**, puis entrez votre certificat et votre CSR dans les champs correspondants. Ils devraient faire la même chose.

### Etape 5 - Demande d’installation du certificat SSL

* Si vous avez accès au [Panneau de Contrôle](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html), suivez les instructions de [cette page](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/renewing-subdomain-certificate.html#installing-ssl-certificate) pour télécharger le certificat au Panneau de Contrôle.

* Sinon, créez un autre ticket d&#39;assistance via https://adminconsole.adobe.com/ pour demander à l&#39;Adobe d&#39;installer le certificat sur le ou les serveurs d&#39;Adobe.

Vous devrez fournir les éléments suivants :

* Le fichier de certificat, le certificat racine et tout certificat intermédiaire (joint au ticket), de préférence au format Apache PEM.
* Numéro du ticket d&#39;assistance précédent levé pour la demande de signature de certificat.
* Les mêmes données que celles fournies pour le ticket CSR (y compris le nom commun, l’URL de l’instance, l’état, la ville/la localité, le nom de l’organisation, le nom de l’unité d’organisation, etc.).

### Etape 6 - Test de l’installation du certificat SSL

Une fois le certificat SSL installé et confirmé par le service à la clientèle d’Adobe, vérifiez qu’il a bien été installé pour toutes les URL.

Effectuez les tests ci-dessous avant de fermer le ticket d’installation SSL. Veillez également à mettre à jour toute configuration spécifique conformément aux instructions de [cette section](#update-configuration).

Accédez aux URL suivantes dans votre navigateur (remplacez &quot;subdomain.customer.com&quot; par votre sous-domaine) :

* https://subdomain.customer.com/r/test (pour les sous-domaines [applications Web](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-applications/about-web-applications.html) uniquement - ne s’applique pas aux sous-domaines de courriel)
* https://t.subdomain.customer.com/r/test
* https://m.subdomain.customer.com/r/test
* https://res.subdomain.customer.com/r/test

Un résultat réussi fournit des informations sur l’environnement et la barre d’adresse dans l’URL indique que la connexion est sécurisée. Par exemple, le message suivant s’affiche dans Google Chrome :

![](../../help/assets/ssl-google-successful-result.png)

Si le certificat SSL n’est pas correctement installé, l’avertissement suivant s’affiche :

![](../../help/assets/ssl-google-unsuccessful-result.png)

### Étape 7 - Vérification de la période de validité du certificat

Vous pouvez vérifier la période de validité du certificat dans votre navigateur. Par exemple, dans Google Chrome, cliquez sur **Sécuriser** > **Certificat**.

Il vous appartient de vérifier la période de validité. Adobe vous recommande de mettre en oeuvre un processus de surveillance de l’expiration des certificats. En savoir plus sur ce qui se produit lorsque votre certificat SSL expire dans [cet article](https://www.thesslstore.com/blog/what-happens-when-your-ssl-certificate-expires/).

* Créez un ticket d&#39;assistance pour demander un certificat mis à jour au moins deux semaines avant la date d&#39;expiration du certificat. Vous n’avez pas besoin de demander une autre demande de signature de certificat, à moins que les détails de la demande de signature de certificat aient changé.

* Si vous avez accès au [Panneau de Contrôle](https://experienceleague.adobe.com/docs/control-panel/using/control-panel-home.html) et si votre environnement est hébergé par un Adobe dans un environnement AWS, vous pouvez utiliser le Panneau de Contrôle pour renouveler le certificat avant son expiration. En savoir plus dans [cette section](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/monitoring-ssl-certificates.html#monitoring-certificates).

### Étape 8 - Mise à jour de toute configuration spécifique {#update-configuration}

Une fois que vous êtes certain que les certificats SSL demandés sont correctement installés, vous pouvez mettre à jour toutes les références dans Adobe Campaign du protocole HTTP au protocole HTTPS.

>[!NOTE]
>
>Pour le Campaign Classic, les URL à mettre à jour se trouvent principalement dans l&#39;[Assistant Déploiement](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/initial-configuration/deploying-an-instance.html#deployment-wizard) et dans les [Comptes externes](https://experienceleague.adobe.com/docs/campaign-classic/using/installing-campaign-classic/additional-configurations/external-accounts.html#installing-campaign-classic) (domaines de suivi, de page miroir et de ressource publique). Pour le Campaign Standard, reportez-vous à la section [Configuration de la marque](https://experienceleague.adobe.com/docs/campaign-standard/using/administrating/application-settings/branding.html#about-brand-identity).

Une fois les configurations mises à jour, de nouveaux courriers électroniques sont envoyés avec des URL HTTPS plutôt qu&#39;avec HTTP. Pour vérifier que les URL sont désormais sécurisées, vous pouvez rapidement effectuer les tests suivants :

* Téléchargez une image d’Adobe Campaign. Une fois l’image téléchargée, l’URL renvoyée doit être HTTPS.
* Créez une diffusion de messagerie de test comprenant un lien de page miroir, certaines images, du texte et un lien de désinscription. Envoyez le courrier électronique à un ID de courrier électronique externe (tel que votre adresse Gmail). Une fois reçu, ouvrez le courrier électronique et assurez-vous que tous les liens qu’il contient s’ouvrent correctement dans leur formulaire HTTPS (et non HTTP), sans avertissement de certificat SSL ni erreur.

## Ressources spécifiques au produit

**Campaign Classic**

* [Panneau de Contrôle : Ajouter des certificats SSL (didacticiel)](https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/adding-ssl-certificates.html)  - Découvrez comment ajouter des certificats SSL pour sécuriser vos sous-domaines.

**Campaign Standard**

* [Panneau de Contrôle : Ajouter des certificats SSL (didacticiel)](https://experienceleague.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/adding-ssl-certificates.html)  - Découvrez comment ajouter des certificats SSL pour sécuriser vos sous-domaines.