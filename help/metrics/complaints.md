---
title: Plaintes
description: 'Découvrez les plaintes qui sont enregistrées lorsqu’un utilisateur indique qu’un courrier électronique est indésirable ou inattendu. '
feature: Mesures
topics: Deliverability
kt: 7048
thumbnail: kt7048.jpg
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: d42a8c3b06308fca0cf3e9db8d634a767fc0cdc6
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 2%

---


# Plaintes

Les plaintes sont enregistrées lorsqu’un utilisateur indique qu’un courriel est indésirable ou inattendu. Cette action d’abonnement est généralement consignée par le client de messagerie de l’abonné lorsqu’il clique sur le bouton spam ou par un système de rapports de messages indésirables tiers.

## plainte de fournisseur

La plupart des FAI de niveau 1 et certains FAI de niveau 2 fournissent une méthode de rapports antispam à leurs utilisateurs, car les processus d&#39;exclusion et de désabonnement ont été utilisés de manière malveillante dans le passé pour valider une adresse électronique. Adobe Campaign reçoit ces plaintes via les FBL des FAI. Ceci est établi pendant le processus de configuration pour tous les FAI qui fournissent des FBL et permet à Adobe Campaign d&#39;ajouter automatiquement des adresses électroniques qui se sont plaintes à la table de quarantaines pour suppression. Les pics de plaintes des fournisseurs de services Internet peuvent être un indicateur de la mauvaise qualité des listes, des méthodes de collecte de listes moins qu&#39;optimales ou des politiques d&#39;engagement déficientes. Ils sont également souvent notés lorsque le contenu n’est pas pertinent.

## Réclamations de tiers

Il existe plusieurs groupes antispam qui permettent un rapports plus large du spam. Les mesures de plainte utilisées par ces tiers sont utilisées pour baliser le contenu des messages électroniques afin d’identifier les messages indésirables. Ce processus est également appelé empreinte digitale. Les utilisateurs de ces méthodes de traitement des plaintes par des tiers sont généralement plus avertis en ce qui concerne les courriels, de sorte qu&#39;ils peuvent avoir un impact plus important que les autres plaintes si elles n&#39;ont pas reçu de réponse.

>[!NOTE]
>
>Les FSI collectent les plaintes et les utilisent pour déterminer la réputation globale d&#39;un expéditeur. Toutes les plaintes devraient être supprimées et ne plus être contactées aussi rapidement que possible et conformément aux lois et règlements locaux.

## Ressources spécifiques au produit

**Adobe Campaign Standard **

* [Plaintes (Complaints)](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/list-of-reports/complaints.html#reporting)