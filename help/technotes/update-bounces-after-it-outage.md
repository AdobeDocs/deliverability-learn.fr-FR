---
title: Mettre à jour la qualification des bounces après une panne d’Italia Online
description: Découvrez comment mettre à jour la qualification des bounces après une panne d’Italia Online.
feature: Deliverability
exl-id: a11e88cf-bf37-42cc-9c09-1d58360459b7
hide: true
hidefromtoc: true
role: Admin
level: Beginner
source-git-commit: 6b312cdbba496818337c97ec4f42962aea757901
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 53%

---

# Mettre à jour les hard bounces incorrects après une panne d’Italia Online {#update-bounce-italia}

## Contexte{#outage-context}

Depuis le 22 janvier (heure locale), Italia Online a subi une panne qui a entraîné plusieurs retards et refusé les emails. Le service a commencé à reprendre avec une capacité limitée le 26 janvier.

Les domaines concernés étaient les suivants : **libero.it**, **virgilio.it**, **inwind.it**, **iol.it** et **blu.it**.

Ce problème s’est produit du 22/01/2023 au 26/01/2023, mais la plupart des mises en quarantaine indésirables ont eu lieu le 26 janvier.

En savoir plus dans la communication officielle [ici](https://tecnologia.libero.it/avviato-il-ritorno-online-di-libero-mail-e-virgilio-mail-66832){_blank}.


## Impact{#outage-impact}

Comme dans la plupart des cas, lorsqu’un fournisseur d’accès Internet (FAI) est en panne, certains emails envoyés via Campaign ou Journey Optimizer sont marqués à tort comme des bounces. Cette panne n’a pas seulement eu un impact sur Adobe, mais aussi sur tous ceux qui essayaient d’envoyer des e-mails sur Italia Online pendant la durée de la panne.

Les symptômes étaient les suivants :

* **Soft bounces** avec le message `452 requested action aborted: try again later` - ont été automatiquement relancés et aucune action n’est nécessaire.

* Des **Hard bounces** avec le message `550 <email address> recipient rejected` ont été retournés par le FAI le 26 janvier, entre 8 h et 14 h, heure locale, pour éviter que les expéditeurs et les expéditrices ne continuent à surcharger leurs serveurs. Comme l’a confirmé le Postmaster d’Italia Online, il ne s&#39;agit pas de véritables hard bounces. Nous recommandons donc de retirer de la quarantaine toutes les adresses e-mail qui ont été exclues le 26 janvier 2023 en raison de ce message.

## Processus de mise à jour{#outage-update}

### Adobe Campaign{#ac-update}

Selon la logique standard de gestion des bounces, Adobe Campaign a automatiquement ajouté ces destinataires à la liste de quarantaine avec un **[!UICONTROL Statut]** de **[!UICONTROL Quarantaine]**. Pour corriger ce problème, vous devez mettre à jour votre table de quarantaines dans Campaign en recherchant et en supprimant ces destinataires ou en basculant leur **[!UICONTROL Statut]** sur **[!UICONTROL Valide]** afin que le processus de nettoyage de nuit les supprime.

Pour trouver les destinataires qui ont été affectés par ce problème , ou au cas où cela se reproduirait avec un autre FAI, référez-vous aux instructions ci-dessous:

* Pour Campaign Classic v7 et Campaign v8, voir [cette page](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html?lang=en#unquarantine-bulk){_blank}.
* Pour le Campaign Standard, reportez-vous à la section [cette page](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=en#unquarantine-bulk){_blank}.

### Adobe Journey Optimizer{#ajo-update}

Selon une logique standard de gestion des rebonds, Adobe Journey Optimizer a automatiquement ajouté ces adresses électroniques à la liste de suppression avec une **[!UICONTROL Motif]** paramètre de **[!UICONTROL Destinataire non valide]**. Pour corriger ce problème, vous devez mettre à jour la liste de suppression en recherchant et en supprimant ces adresses électroniques.

Une fois identifiées, ces adresses peuvent être supprimées manuellement de la liste de suppression à l’aide du **[!UICONTROL Supprimer]** bouton . Ces adresses peuvent ensuite être incluses dans les futures campagnes par e-mail.

En savoir plus dans [cette section](https://experienceleague.adobe.com/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list.html#remove-from-suppression-list){_blank}.

