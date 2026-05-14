---
title: Implémenter les indicateurs de marque Gmail pour l’identification des messages (BIMI)
description: Découvrez comment implémenter BIMI
topics: Deliverability
role: Admin
level: Beginner
jira: KT-14079
exl-id: 6b911bcc-a531-466a-8bd3-7fa469b96cc7
TQID: https://experienceleague.adobe.com/dPuoipUKH36RSGUfhzOV1Xhu9qQTLYV4zu6Vw0Be-xY
product_v2: id: b27e5950-9033-45ac-9f86-eb22e567f615id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b0bb9048-d951-48d8-8232-45cf248a7e27id: e2290edd-b061-4880-9d79-dee306cf5aa9id: ea90ebee-5c84-42d9-8b21-006bdabc95a3id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 1164
ht-degree: 0%

---

# Implémentation de [!DNL Brand Indicators for Message Identification] (BIMI)

[!DNL Brand Indicators for Message Identification] (BIMI) est une norme du secteur qui permet à un logo approuvé d’apparaître à côté de l’e-mail d’un expéditeur ou d’une expéditrice sur les plateformes participantes.

Avec cette norme, une marque peut déterminer un logo qui doit s&#39;afficher dans les boîtes de réception des fournisseurs de boîtes aux lettres. Une fois publié dans un enregistrement DNS (Domain Name System) BIMI, un fournisseur de boîtes aux lettres peut choisir ce logo et l&#39;afficher dans la boîte de réception si certains critères sont remplis.

Différents fournisseurs effectuent différentes implémentations, mais les avantages sont clairs : ils se démarquent dans la boîte de réception, établissent la confiance et contrôlent ce qui s’affiche.

BIMI n&#39;améliore pas directement la délivrabilité ou votre réputation. Cela peut aider à créer plus de confiance avec vos destinataires et donc à stimuler davantage d’engagement.

## À quoi cela ressemble-t-il ?

Vous trouverez quelques exemples d’implémentations de différents fournisseurs et plus de détails sur les fournisseurs qui affichent le logo sur la page du [Groupe BIMI](https://bimigroup.org/where-is-my-bimi-logo-displayed/){target="_blank"}.

## Qui est le groupe BIMI ?

Le groupe BIMI est un groupe de travail qui développe le BIMI car il couvre non seulement le logo mais aussi les exigences techniques, juridiques et de conformité.

Le groupe BIMI est composé de plusieurs parties prenantes de différents secteurs de l&#39;industrie : Google, Yahoo, Fastmail, Proofpoint, Mailchimp, Sendgrid, Valimail et Validity.

## Qui soutient BIMI ?

La liste des fournisseurs de boîtes aux lettres prenant en charge BIMI ne cesse de s&#39;allonger. Une liste à jour peut être trouvée [ici](https://bimigroup.org/bimi-infographic/){target="_blank"} pour les fournisseurs de soutien ainsi que les fournisseurs qui envisagent BIMI.

Depuis avril 2023, la liste comprend Gmail, Yahoo, La Poste, Fastmail, Onet.pl et Zone, Proofpoint en tant qu&#39;appliance anti-spam et Apple Mail (à partir d&#39;iOS 16).

Les noms les plus en vue sur cette liste sont évidemment Yahoo, Gmail et un utilisateur récent : Apple avec iOS 16. Apple joue un rôle spécial dans ce mix, car il n’est pas un fournisseur de boîtes aux lettres, mais il a ajouté la prise en charge BIMI à son application de messagerie native. La conformité de l&#39;e-mail avec BIMI sera affichée comme « e-mail certifié numériquement », ce qui renforce la confiance dans la marque.

## Mise en œuvre

La mise en œuvre de BIMI se fait en plusieurs étapes :

1. Implémentation de DMARC (Domain based Message Authentication, Reporting and Conformance) au niveau de l&#39;application, tant pour le domaine d&#39;envoi que pour son domaine d&#39;organisation - [En savoir plus](#dmarc)

1. Création de votre logo de marque au format SVG TinyPS - [En savoir plus](#create-brand-logo)

1. S&#39;inscrire à un certificat de marquage vérifié (seulement nécessaire pour certains fournisseurs) - [En savoir plus](#vmc)

1. Publier un enregistrement DNS BIMI avec le logo et le certificat - [En savoir plus](#publish-bimi-record)

1. Avoir une bonne réputation - [En savoir plus](#good-reputation)

>[!NOTE]
>
>Notez que toutes les étapes doivent être cochées.


### DMARC {#dmarc}

DMARC est une norme qui permet à la marque de décider ce qu&#39;un fournisseur de boîte aux lettres doit faire avec un e-mail qui échoue [authentification](../additional-resources/authentication.md). Ces politiques vont de « aucune » à « quarantaine » (emplacement du dossier des spams), en passant par « rejeter » (bloquer carrément l&#39;e-mail). Seules les deux dernières politiques sont appelées « application » et sont admissibles au BIMI. L’e-mail envoyé par Adobe transmet l’authentification, car SPF (Sender Policy Framework) et DKIM (Domain Keys Identified Mail) sont configurés par défaut. Adobe configure DMARC sur votre domaine d’envoi à la demande.

Outre DMARC sur le domaine d’envoi, DMARC doit également être utilisé au niveau de l’application pour le domaine d’organisation (si le domaine d’envoi est news.example.com, example.com est le domaine d’organisation).

### Création de votre logo de marque {#create-brand-logo}

La création du logo doit respecter les exigences à 100 %. Veuillez toujours vous référer aux directives du [Groupe BIMI](https://bimigroup.org/creating-bimi-svg-logo-files/){target="_blank"}.

Le logo doit être stocké dans un emplacement sécurisé (HTTPS). En cas d’utilisation d’un réseau de diffusion de contenu (CDN), toute protection qui empêche les fournisseurs de messagerie d’obtenir le logo (par exemple, la protection des robots) doit être désactivée.

Outre les exigences techniques, il existe quelques recommandations pratiques comme avoir un logo carré, avoir une couleur unie en arrière-plan et autres. Ces recommandations sont destinées à une visualisation optimale. Certains fournisseurs ont leurs propres exigences qui s&#39;ajoutent à celles du groupe de travail BIMI. [Gmail](https://support.google.com/a/answer/10911027?sjid=903725605955621707-EU){target="_blank"} par exemple, nécessite que le logo soit d’au moins 96 x 96 pixels.
Veuillez noter que la non-conformité peut entraîner l’affichage du logo.

### Certificat de marquage vérifié (VMC) {#vmc}

Un certificat de marque vérifiée (VMC) n’est nécessaire que pour certains fournisseurs de boîtes aux lettres tels que Gmail et Apple et est donc facultatif. Nous vous recommandons cependant d&#39;obtenir une VMC pour vraiment tirer parti de BIMI.

Un certificat de marque vérifiée est une validation légale que la marque peut utiliser le logo. Une autorité de certification vérifiera cette information auprès du bureau des marques de commerce où le logo de la marque est enregistré. Ce processus implique plusieurs validations et vérifications juridiques et peut prendre un certain temps. À l&#39;heure actuelle, deux AC (autorités de certification) émettent des CVM : Digicert et Entrust. Les premiers offices de marques sont les États-Unis, le Canada, l&#39;UE, le Royaume-Uni, l&#39;Allemagne, le Japon, l&#39;Australie et l&#39;Espagne.

En règle générale, vous aurez besoin d&#39;une VMC par logo. Disposer d’un VMC pour votre domaine d’organisation couvre les sous-domaines, et avec une fonctionnalité ajoutée, même les différents domaines. Si vous avez des logos différents, plusieurs VMC sont nécessaires. L’autorité de certification ou le partenaire avec lequel vous choisissez de travailler vous aidera à configurer ce service.

>[!NOTE]
>
>Notez que les CVM ont des frais annuels.

### Publier l’enregistrement BIMI {#publish-bimi-record}

Une fois les autres étapes effectuées, l’enregistrement DNS BIMI peut être publié. L’enregistrement ressemble à ceci :

```
default._bimi.[domain] IN TXT "v=BIMI1; l=[SVG URL]; a=[PEM URL]
```

« URL PEM » est l’emplacement du fichier du certificat de marque vérifiée.

Pour votre domaine d&#39;envoi, cela doit être effectué par Adobe.

### Bonne réputation {#good-reputation}

La confiance est essentielle pour BIMI. L&#39;utilisateur fait confiance à son fournisseur de boîte aux lettres pour afficher uniquement le logo pour les expéditeurs légitimes, de sorte que le fournisseur de boîte aux lettres doit faire confiance à la marque, ce que fait votre réputation d&#39;expéditeur. Si vous avez une bonne réputation, tout va bien, mais si vous ne l&#39;avez pas, le logo ne s&#39;affichera pas. Malheureusement, il n’existe aucune information ou mesure que nous pouvons examiner pour déterminer si la réputation est suffisamment élevée.

Même en examinant les efforts et les dépenses d&#39;un VMC, on ne supprime pas cette partie. Si le fournisseur de boîtes aux lettres ne fait pas confiance à la marque, le logo ne s&#39;affichera pas.

## Conseils et astuces

* Le groupe BIMI offre un outil de validation pratique pour BIMI. Si vous souhaitez vérifier si tout est prêt et configuré, ou simplement vérifier si le logo est conforme, cliquez sur [ce lien](https://bimigroup.org/bimi-generator/){target="_blank"}. Pour ce dernier, il vous suffit de cliquer sur **[!UICONTROL Générer BIMI]** et de saisir un domaine d’espace réservé, mais l’URL correcte du logo. L&#39;inspecteur vous dira si le logo est conforme.

* Vous pouvez commencer en toute sécurité sans VMC, il n&#39;y a pas de risque pour votre réputation si votre enregistrement BIMI ne comprend pas d&#39;URL VMC, mais le logo peut déjà être affiché dans Yahoo.

* La mise en œuvre de DMARC au niveau organisationnel est une entreprise de grande envergure. Certaines sociétés sont spécialisées dans l’aide aux marques pour parvenir à une adoption complète de DMARC.

* Une liste exhaustive de questions fréquentes est publiée [ici](https://bimigroup.org/faqs-for-senders-esps/){target="_blank"}.
