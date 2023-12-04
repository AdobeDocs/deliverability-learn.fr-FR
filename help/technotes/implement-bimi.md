---
title: Mise en oeuvre des indicateurs de marque de Gmail pour l’identification des messages (BIMI)
description: Découvrez comment implémenter BIMI
topics: Deliverability
role: Admin
level: Beginner
jira: KT-14079
exl-id: 6b911bcc-a531-466a-8bd3-7fa469b96cc7
source-git-commit: ad0646da88f2b1474e74b6c741d0dd5701e88978
workflow-type: tm+mt
source-wordcount: '1127'
ht-degree: 0%

---

# Mise en oeuvre [!DNL Brand Indicators for Message Identification] (BIMI)

[!DNL Brand Indicators for Message Identification] (BIMI) est une norme du secteur qui permet l’affichage d’un logo approuvé en regard de l’adresse électronique d’un expéditeur sur les plateformes participantes.

Grâce à cette norme, une marque peut déterminer un logo qui doit être affiché dans les boîtes de réception des fournisseurs de messagerie. Une fois publié dans un enregistrement appelé BIMI DNS (Domain Name System), un fournisseur de messagerie peut sélectionner ce logo et l’afficher dans la boîte de réception si certains critères sont satisfaits.

Différents fournisseurs effectuent des mises en oeuvre différentes, mais les avantages sont évidents : se démarquer dans la boîte de réception, établir la confiance et contrôler ce qui est affiché.

BIMI n&#39;améliore pas directement la délivrabilité ni votre réputation. Cela peut contribuer à renforcer la confiance avec vos destinataires et donc à augmenter l’engagement.

## À quoi ça ressemble ?

Vous trouverez quelques exemples de mise en oeuvre de différents fournisseurs et des informations supplémentaires sur les fournisseurs qui affichent le logo sur la page [Page du groupe BIMI](https://bimigroup.org/where-is-my-bimi-logo-displayed/){target="_blank"}.

## Qui est le groupe BIMI ?

Le groupe BIMI est un groupe de travail qui développe le BIMI, car il couvre non seulement le logo mais aussi les exigences techniques, juridiques et de conformité.

Le groupe BIMI est constitué de plusieurs parties prenantes de différents secteurs de l&#39;industrie : Google, Yahoo, Fastmail, Proofpoint, Mailchimp, Sendgrid, Valimail et Validity.

## Qui soutient BIMI ?

La liste des fournisseurs de messagerie prenant en charge BIMI ne cesse de s&#39;allonger. Une liste à jour est disponible [here](https://bimigroup.org/bimi-infographic/){target="_blank"} tant pour les prestataires d&#39;assistance que pour les prestataires ayant recours à l&#39;IMI.

Depuis avril 2023, la liste inclut Gmail, Yahoo, La Poste, Fastmail, Onet.pl et Zone, Proofpoint en tant qu&#39;outil anti-spam et Apple Mail (à partir d&#39;iOS 16 et plus).

Les noms les plus en vue sur cette liste sont évidemment Yahoo, Gmail et un dernier adoptant : Apple avec iOS 16. Apple joue un rôle particulier dans la combinaison, car il ne s’agit pas d’un fournisseur de messagerie, mais il a ajouté la prise en charge de BIMI à son application de messagerie native. Les emails conformes à BIMI seront affichés sous la forme d’un &quot;email certifié numérique&quot; qui renforce la confiance dans la marque.

## Mise en œuvre

La mise en oeuvre de BIMI se fait en plusieurs étapes :

1. Implémentation DMARC (Domain-based Message Authentication, Reporting and Conformance) au niveau de l’application, tant pour le domaine d’envoi que pour son domaine d’organisation - [En savoir plus](#dmarc)

1. Création du logo de votre marque au format SVG TinyPS - [En savoir plus](#create-brand-logo)

1. S’inscrire à un certificat de marque vérifié (nécessaire uniquement pour certains fournisseurs) - [En savoir plus](#vmc)

1. Publier un enregistrement DNS BIMI avec le logo et le certificat - [En savoir plus](#publish-bimi-record)

1. Avoir une bonne réputation - [En savoir plus](#good-reputation)

>[!NOTE]
>
>Notez que toutes les étapes doivent être désactivées.


### DMARC {#dmarc}

DMARC est une norme qui permet à la marque de décider ce qu’un fournisseur de messagerie doit faire avec un email qui échoue. [authentication](../additional-resources/authentication.md). Les soi-disant politiques vont de &quot;aucun&quot; à &quot;quarantaine&quot; (placement du dossier Spam) en &quot;rejet&quot; (blocage pur et simple du courrier). Seules les deux dernières politiques sont appelées &quot;application&quot; et répondent aux critères du BIMI. Le courrier envoyé par Adobe transmet l’authentification, car SPF (Sender Policy Framework) et DKIM (Domain Keys Identified Mail) sont configurés par défaut. Adobe configure DMARC sur votre domaine d’envoi sur demande.

Outre DMARC sur le domaine d’envoi, DMARC doit également être employé au niveau de l’application pour le domaine d’organisation (si le domaine d’envoi est news.example.com, example.com est le domaine d’organisation).

### Création du logo de votre marque {#create-brand-logo}

La création du logo doit respecter les exigences à 100 %. Veuillez toujours vous reporter à la section [Directives du groupe BIMI](https://bimigroup.org/creating-bimi-svg-logo-files/){target="_blank"}.

Le logo doit être stocké dans un emplacement sécurisé (HTTPS), au cas où un réseau de diffusion de contenu (CDN) serait utilisé pour toute protection qui empêcherait les fournisseurs de messagerie d’obtenir le logo (par exemple, la protection des robots), doit être désactivé.

Outre les exigences techniques, il existe des recommandations pratiques telles que le logo carré, la couleur unie de l’arrière-plan et d’autres. Ces recommandations concernent la meilleure visualisation. Certains fournisseurs ont leurs propres exigences qui s&#39;ajoutent à celles du groupe de travail de l&#39;IMI. [Gmail](https://support.google.com/a/answer/10911027?sjid=903725605955621707-EU){target="_blank"}. par exemple, nécessite que le logo fasse au moins 96 x 96 pixels.
Veuillez noter que la non-conformité peut entraîner l’affichage du logo.

### Certificat de marque vérifié (VMC) {#vmc}

Un certificat de marque vérifié (VMC) n’est nécessaire que pour certains fournisseurs de messagerie tels que Gmail et Apple. Il est donc facultatif. Nous vous recommandons cependant d’obtenir un VMC pour vraiment tirer parti de BIMI.

Un certificat de marque vérifié est une validation légale que la marque peut utiliser le logo. Une autorité de certification vérifie cette information par l’intermédiaire du bureau des marques où le logo de la marque est enregistré. Ce processus implique plusieurs validations et contrôles juridiques, et peut prendre du temps. Actuellement, deux autorités de certification (autorités de certification) émettent des CVM : Digicert et Entrust. Les premiers bureaux de marques sont les États-Unis, le Canada, l’UE, le Royaume-Uni, l’Allemagne, le Japon, l’Australie et l’Espagne.

En règle générale, vous aurez besoin d’un VMC par logo. Disposer d’un VMC pour votre domaine d’organisation couvrira les sous-domaines et avec une fonctionnalité ajoutée, même différents domaines. Si vous disposez de logos différents, plusieurs composants VMC sont nécessaires. L’autorité de certification ou le partenaire avec lequel vous choisissez de travailler vous aidera à configurer cette fonctionnalité.

>[!NOTE]
>
>Notez que les VMC ont des frais annuels.

### Publication de l’enregistrement BIMI {#publish-bimi-record}

Une fois les autres étapes effectuées, l’enregistrement DNS BIMI peut être publié. L&#39;enregistrement ressemble à ceci :

```
default._bimi.[domain] IN TXT "v=BIMI1; l=[SVG URL]; a=[PEM URL]
```

&quot;URL PEM&quot; est l’emplacement du fichier du certificat de marque vérifié.

Pour votre domaine d’envoi, cela doit être effectué par Adobe.

### Bonne réputation {#good-reputation}

La confiance est la clé pour le BIMI. L&#39;utilisateur fait confiance à son fournisseur de boîtes aux lettres pour qu&#39;il affiche uniquement le logo des expéditeurs légitimes. Le fournisseur de boîtes aux lettres doit donc faire confiance à la marque, ce que fait votre réputation d&#39;expéditeur. Si vous avez une bonne réputation, tout est bon, mais si vous ne l&#39;êtes pas, le logo ne s&#39;affichera pas. Malheureusement, il n’existe aucune information ou mesure permettant de déterminer si la réputation est suffisamment élevée.

Même passer par les efforts et les dépenses d&#39;un VMC n&#39;enlève pas cette partie. Si le fournisseur de messagerie n&#39;a pas confiance en la marque, le logo ne s&#39;affiche pas.

## Conseils et astuces

* Le groupe BIMI offre un outil de validation pratique pour BIMI. Si vous souhaitez vérifier si tout est configuré et prêt, ou simplement si le logo est conforme, accédez à [ce lien](https://bimigroup.org/bimi-generator/){target="_blank"}. Pour ce dernier, cliquez simplement sur **[!UICONTROL Générer BIMI]** et saisissez un domaine d’espace réservé, mais l’URL de logo correcte. L&#39;inspecteur vous dira si le logo est conforme.

* Vous pouvez démarrer sans risque sans VMC, votre réputation n’est pas entachée si votre enregistrement BIMI n’inclut pas d’URL VMC, mais le logo peut déjà être affiché dans Yahoo.

* La mise en oeuvre de DMARC au niveau organisationnel est une entreprise de grande envergure. Certaines entreprises sont spécialisées pour aider les marques à réaliser une adoption DMARC complète.

* Une liste complète de questions fréquentes est publiée [here](https://bimigroup.org/faqs-for-senders-esps/){target="_blank"}.
