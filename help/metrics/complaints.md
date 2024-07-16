---
title: Plaintes
description: Découvrez les plaintes qui sont enregistrées lorsqu’un utilisateur indique qu’un email est indésirable ou inattendu.
topics: Deliverability
jira: KT-7048
thumbnail: kt7048.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 0343820d-f5af-4b8a-bcab-dbb47ae7aecb
source-git-commit: 9444f8601f2f349398ee5deb9d5f4d4f7abb44f5
workflow-type: tm+mt
source-wordcount: '276'
ht-degree: 100%

---

# Plaintes

Les plaintes sont enregistrées lorsqu’un utilisateur indique qu’un email est indésirable ou inattendu. Cette action d’abonné est généralement consignée par le client de messagerie de l’abonné lorsqu’il clique sur le bouton des messages indésirables ou via un système de signalement de messages indésirables tiers.

## Plaintes des FAI

La plupart des FAI de niveau 1 et certains FAI de niveau 2 proposent une méthode de signalement des courriers indésirables à leurs utilisateurs, car les processus d&#39;opt-out et de désabonnement ont été utilisés de manière malveillante dans le passé pour valider une adresse email. Adobe Campaign reçoit ces plaintes via les FBL des FAI. Ce système est établi pendant le processus de configuration pour tous les FAI qui fournissent des FBL. Il permet à Adobe Campaign d&#39;ajouter automatiquement des adresses email à l’origine d’une plainte à la table de mise en quarantaine pour suppression. Les pics des plaintes des FAI peuvent indiquer des listes de mauvaise qualité, des méthodes de collecte de listes qui ne sont pas optimales ou des politiques d&#39;engagement inadaptées. Ils sont également souvent remarqués lorsque le contenu n’est pas pertinent.

## Plaintes de tiers

Il existe plusieurs groupes contre les courriers indésirables qui permettent un signalement à un niveau plus large. Les mesures de plainte utilisées par ces tiers servent à marquer le contenu des emails afin d’identifier les emails indésirables. Ce processus est également appelé fingerprinting. Les utilisateurs de ces méthodes de traitement des plaintes de tiers sont généralement plus avisés en ce qui concerne les emails, de sorte qu&#39;ils peuvent avoir un impact plus important que les autres plaintes si elles n&#39;ont pas reçu de réponse.

>[!NOTE]
>
>Les FAI collectent les plaintes et les utilisent pour déterminer la réputation globale d&#39;un expéditeur. Toutes les plaintes doivent être supprimées et ne plus être contactées aussi rapidement que possible et conformément aux lois et règlements en vigueur.

## Ressources spécifiques au produit

**Adobe Campaign Classic**

* [Indicateurs de tracking](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/reports-on-deliveries/delivery-reports.html?lang=fr-FR#tracking-indicators)

**Adobe Campaign Standard**

* [Rapport de plaintes](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/list-of-reports/complaints.html?lang=fr#reporting)
