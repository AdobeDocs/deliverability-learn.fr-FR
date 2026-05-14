---
title: Transition en douceur lors du changement de plateforme de messagerie.
description: Lors du déplacement de fournisseurs de services de messagerie (ESP), il n’est pas possible de transférer également vos adresses IP existantes et établies. Il est important de suivre les bonnes pratiques pour développer une réputation positive lorsque vous recommencez à zéro.
topics: Deliverability
jira: KT-5259
thumbnail: kt5259.jpg
doc-type: article
activity: understand
role: Admin
level: Beginner
team: ACS
exl-id: 5444d576-5bc1-4fa6-9956-c63dc3c60440
TQID: https://experienceleague.adobe.com/sxCdMHKqdCZ3z2xp-aMYKiFfqu5Y-iDhk8FeergrgZw
product_v2:
  - id: b27e5950-9033-45ac-9f86-eb22e567f615
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b0bb9048-d951-48d8-8232-45cf248a7e27
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 215
ht-degree: 8%

---

# Transition en douceur lors du changement de plateforme de messagerie

Lors du déplacement de fournisseurs de service de messagerie (ESP), il n’est pas possible de faire également la transition vers vos adresses IP existantes et établies. Il est important de suivre les bonnes pratiques pour développer une réputation positive lorsque vous recommencez à zéro. Comme les nouvelles adresses IP que vous utiliserez n’ont pas encore de réputation, les FAI ne peuvent pas faire entièrement confiance au courrier qui leur est envoyé et doivent faire preuve de prudence quant à ce qu’ils permettent de diffuser à leurs clients.

L&#39;établissement d&#39;une réputation positive est un processus. Mais une fois qu&#39;il sera établi, les petits indicateurs négatifs auront moins d&#39;impact sur vous et votre diffusion par la poste.

![Processus de transition](../assets/transition-process.png)

Le délai nécessaire pour préchauffer vos adresses IP et domaines peut varier, mais il est courant pour des expéditeurs standard d’établir une réputation sur une période allant jusqu’à huit semaines auprès de la plupart des FAI de niveau 1 (Gmail, Microsoft, Verizon/Yahoo/AOL, etc.).

Dans les sections suivantes, nous allons examiner certains domaines clés sur lesquels nous devons nous concentrer pour une intégration correcte :

1. [Infrastructure](/help/transition-process/infrastructure.md)
2. [Critères de ciblage](/help/transition-process/targeting-criteria.md)
3. [Considérations spécifiques aux fournisseurs d&#39;accès lors du réchauffement des adresses IP](/help/transition-process/isp-specific-considerations-during-ip-warming.md)
4. [Volume](/help/transition-process/volume.md)
