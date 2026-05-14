---
title: Verizon Media Group (Yahoo, AOL, Verizon, etc.)
description: '[!DNL Verizon Media Group] est généralement l’un des trois premiers domaines pour la plupart des listes B2C. Ils se comportent de manière assez unique, car ils ralentiront ou encombreront généralement le publipostage en cas de problèmes de réputation.'
topics: Deliverability
jira: KT-5320
doc-type: article
activity: understand
role: Admin, Leader, User
level: Beginner
team: TM
exl-id: 43e6d3cb-23c3-4076-8026-a1a08e76bd1b
TQID: https://experienceleague.adobe.com/ycELLXdqC1E3EIxywp-I1HWnSyWayRHcwkNOzmzSBvY
product_v2: id: b27e5950-9033-45ac-9f86-eb22e567f615id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dfc56824-e8b9-499e-85d4-21aedb507314
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 289
ht-degree: 3%

---

# [!DNL Verizon Media Group] (Yahoo, AOL, Verizon, etc.)

[!DNL Verizon Media Group] est généralement l’un des trois premiers domaines pour la plupart des listes B2C. Ils se comportent de manière assez unique, car ils ralentiront ou encombreront généralement le publipostage en cas de problèmes de réputation.

Voici quelques points forts :

## Les données importantes

[!DNL Verizon Media Group] (VMG) a créé et gère ses propres filtres de spam propriétaires, en combinant filtrage de contenu et d&#39;URL et plaintes contre le spam. Avec Gmail, ils sont l’un des premiers FAI à avoir adopté le filtrage des e-mails par domaine ainsi que par adresse IP.

## Quelles données rendent-ils disponibles ?

VMG dispose d&#39;un FBL utilisé pour transmettre des informations sur les plaintes aux expéditeurs. Ils envisagent également d’ajouter d’autres données à l’avenir.

## Réputation de l&#39;expéditeur

La réputation d&#39;un expéditeur est composée d&#39;une combinaison d&#39;adresses IP, de domaines et d&#39;adresses d&#39;expédition. La réputation est calculée à l’aide des composants traditionnels, notamment les plaintes, les pièges à spam, les adresses inactives ou malformées et l’engagement. VMG utilise la limitation de débit (également appelée ralentissement) ainsi que le dossier en bloc pour se défendre contre le spam. Ils complètent leurs systèmes de filtrage interne par des listes noires [!DNL Spamhaus], dont PBL, SBL et XBL pour protéger leurs utilisateurs.

## Insights

VMG a récemment mis en place des périodes de maintenance régulières pour les anciennes adresses e-mail inactives. Cela signifie qu’il est courant d’observer une augmentation significative des rebonds d’adresses non valides, ce qui peut avoir un impact sur votre taux de délivrabilité pendant une courte période. Ils sont également sensibles aux taux élevés de rebonds d’adresses non valides provenant d’un expéditeur, qui indiquent un besoin de renforcer les politiques d’acquisition ou d’engagement. Les expéditeurs peuvent souvent subir un impact négatif à environ 1 % d&#39;adresses non valides.
