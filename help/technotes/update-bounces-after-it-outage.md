---
title: Mettre à jour la qualification des rebonds après une panne d’Italia Online
description: Découvrez comment mettre à jour la qualification des rebonds après une panne d’Italia Online.
feature: Deliverability
exl-id: a11e88cf-bf37-42cc-9c09-1d58360459b7
hide: true
role: Admin
level: Beginner
TQID: https://experienceleague.adobe.com/hPHB9s3PH7E9L3omZMTWZA2ZB0d1JS5vEfawQOjnBLw
product_v2: id: b27e5950-9033-45ac-9f86-eb22e567f615id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: b3b8a63f-51fc-40f6-a7d2-a31c5d49fb45id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
role_v2: id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 467
ht-degree: 47%

---

# Mettre à jour les rebonds définitifs incorrects après une panne d’Italia Online {#update-bounce-italia}

## Contexte{#outage-context}

Depuis le 22 janvier (heure locale), une panne d’Italia Online a entraîné plusieurs retards et le rejet d’e-mails. Le service a commencé à reprendre avec une capacité limitée le 26 janvier.

Les domaines concernés étaient les suivants : **libero.it**, **virgilio.it**, **inwind.it**, **iol.it** et **blu.it**.

Ce problème s’est produit du 22/01/2023 au 26/01/2023, mais la plupart des mises en quarantaine indésirables ont eu lieu le 26 janvier.

En savoir plus dans la communication officielle [ici](https://tecnologia.libero.it/avviato-il-ritorno-online-di-libero-mail-e-virgilio-mail-66832){_blank}.


## Impact{#outage-impact}

Comme dans la plupart des cas lorsqu’un fournisseur d’accès à Internet (FAI) est en panne, certains e-mails envoyés via Campaign ou Journey Optimizer ont été incorrectement marqués comme des bounces. Cette panne n’a pas seulement eu un impact sur Adobe, mais aussi sur tous ceux qui essayaient d’envoyer des e-mails sur Italia Online pendant la durée de la panne.

Les symptômes étaient les suivants :

* **Soft bounces** avec le message `452 requested action aborted: try again later` : ils ont fait automatiquement l’objet de reprises et aucune action n’était nécessaire.

* Des **rebonds définitifs** avec le message `550 <email address> recipient rejected` ont été retournés par le FAI le 26 janvier, entre 8 h et 14 h, heure locale, pour éviter que les expéditeurs et les expéditrices ne continuent à surcharger leurs serveurs. Comme l’a confirmé le Postmaster d’Italia Online, il ne s’agit pas de véritables rebonds définitifs. Nous recommandons donc de retirer de la quarantaine toutes les adresses e-mail qui ont été exclues le 26 janvier 2023 en raison de ce message.

## Processus de mise à jour{#outage-update}

### Adobe Campaign{#ac-update}

Selon la logique standard de gestion des rebonds, Adobe Campaign a automatiquement ajouté ces destinataires à la liste de quarantaine avec un paramètre **[!UICONTROL Statut]** de **[!UICONTROL Quarantaine]**. Pour corriger ce problème, vous devez mettre à jour votre table de quarantaines dans Campaign en recherchant et en supprimant ces destinataires ou en basculant leur **[!UICONTROL Statut]** sur **[!UICONTROL Valide]** afin que le processus de nettoyage de nuit les supprime.

Pour trouver les destinataires qui ont été affectés par ce problème, ou au cas où cela se reproduirait avec un autre FAI, consultez les instructions ci-dessous :

* Pour Campaign Classic v7 et Campaign v8, consultez [cette page](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html?lang=en#unquarantine-bulk){_blank}.
* Pour Campaign Standard, consultez [cette page](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=en#unquarantine-bulk){_blank}.

### Adobe Journey Optimizer{#ajo-update}

Selon la logique standard de gestion des bounces, Adobe Journey Optimizer a automatiquement ajouté ces adresses e-mail à la liste de suppression avec un paramètre **[!UICONTROL Raison]** de **[!UICONTROL Destinataire non valide]**. Pour corriger ce problème, vous devez mettre à jour la liste de suppression en recherchant et en supprimant ces adresses e-mail.

Une fois identifiées, ces adresses peuvent être supprimées manuellement de la liste de suppression à l’aide du bouton **[!UICONTROL Supprimer]**. Ces adresses peuvent ensuite être incluses dans les futures campagnes par e-mail.

En savoir plus dans [cette section](https://experienceleague.adobe.com/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list.html#remove-from-suppression-list){_blank}.

