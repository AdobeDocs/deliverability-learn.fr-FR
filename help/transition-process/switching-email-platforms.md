---
title: Transition en douceur lors du changement de plateforme de messagerie.
description: Lors du déplacement des fournisseurs de services de messagerie électronique (ESP), il n’est pas possible de faire également la transition entre vos adresses IP existantes et établies. Il est important que vous suiviez les bonnes pratiques pour développer une réputation positive lors d’un nouveau départ.
topics: Deliverability
jira: KT-5259
thumbnail: kt5259.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 5444d576-5bc1-4fa6-9956-c63dc3c60440
source-git-commit: 9444f8601f2f349398ee5deb9d5f4d4f7abb44f5
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 11%

---

# Transition en douceur lors du changement de plateforme de messagerie

Lors du déplacement des fournisseurs de services de messagerie électronique (ESP), il n’est pas possible de faire également la transition entre vos adresses IP existantes et établies. Il est important que vous suiviez les bonnes pratiques pour développer une réputation positive lors d’un nouveau départ. Comme les nouvelles adresses IP que vous allez utiliser n’ont pas encore de réputation, les FAI ne peuvent pas entièrement faire confiance au courrier qui leur vient et doivent être prudents dans ce qu’ils permettent d’envoyer à leurs clients.

Établir une réputation positive est un processus. Mais une fois établi, de petits indicateurs négatifs auront moins d&#39;impact sur vous et votre diffusion par courrier.

![Processus de transition](../assets/transition-process.png)

Le temps nécessaire au contrôle de vos adresses et domaines IP peut varier, mais jusqu’à huit semaines de référence est courant pour les expéditeurs types d’établir une réputation dans la plupart des FAI de niveau 1 (Gmail, Microsoft, Verizon/Yahoo/AOL, etc.).

Dans les sections suivantes, nous allons étudier certains domaines clés sur lesquels se concentrer pour embarquer correctement :

1. [Infrastructure](/help/transition-process/infrastructure.md)
2. [Critères de ciblage](/help/transition-process/targeting-criteria.md)
3. [Considérations spécifiques aux fournisseurs d&#39;accès lors du réchauffement des adresses IP](/help/transition-process/isp-specific-considerations-during-ip-warming.md)
4. [Volume](/help/transition-process/volume.md)
