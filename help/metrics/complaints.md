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
TQID: https://experienceleague.adobe.com/W9G0ZPGeIm5KmVHu5-VuMd-Kb-4x4f7qhBPnpskxqqA
product_v2: id: b27e5950-9033-45ac-9f86-eb22e567f615id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: ea90ebee-5c84-42d9-8b21-006bdabc95a3id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 307
ht-degree: 100%

---

# Plaintes

Les plaintes sont enregistrées lorsqu’un utilisateur indique qu’un email est indésirable ou inattendu. Cette action d’abonné est généralement consignée par le client de messagerie de l’abonné lorsqu’il clique sur le bouton des messages indésirables ou via un système de signalement de messages indésirables tiers.

## Plaintes des FAI

La plupart des FAI de niveau 1 et certains FAI de niveau 2 proposent une méthode de signalement des courriers indésirables à leurs utilisateurs, car les processus d&#39;opt-out et de désabonnement ont été utilisés de manière malveillante dans le passé pour valider une adresse email. Adobe Campaign reçoit ces plaintes via les FBL des FAI. Ce système est établi pendant le processus de configuration pour tous les FAI qui fournissent des FBL. Il permet à Adobe Campaign d&#39;ajouter automatiquement des adresses email à l’origine d’une plainte à la table de mise en quarantaine pour suppression. Les pics des plaintes des FAI peuvent indiquer des listes de mauvaise qualité, des méthodes de collecte de listes qui ne sont pas optimales ou des politiques d&#39;engagement inadaptées. Ils sont également souvent remarqués lorsque le contenu n’est pas pertinent.

## Plaintes de tiers

Il existe plusieurs groupes contre les courriers indésirables qui permettent un signalement à un niveau plus large. Les mesures de plainte utilisées par ces tiers servent à marquer le contenu des emails afin d’identifier les emails indésirables. Ce processus est également appelé pistage par empreinte numérique ou « fingerprinting ». Les utilisateurs de ces méthodes de traitement des plaintes de tiers sont généralement plus avisés en ce qui concerne les emails, de sorte qu&#39;ils peuvent avoir un impact plus important que les autres plaintes si elles n&#39;ont pas reçu de réponse.

>[!NOTE]
>
>Les FAI collectent les plaintes et les utilisent pour déterminer la réputation globale d&#39;un expéditeur. Toutes les plaintes doivent être supprimées et ne plus être contactées aussi rapidement que possible et conformément aux lois et règlements en vigueur.

## Ressources spécifiques au produit

**Adobe Campaign Classic**

* [Indicateurs de tracking](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/reports-on-deliveries/delivery-reports.html?lang=fr-FR#tracking-indicators)

**Adobe Campaign Standard**

* [Rapport de plaintes](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/list-of-reports/complaints.html?lang=fr#reporting)
