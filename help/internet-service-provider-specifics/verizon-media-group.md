---
title: Verizon Media Group (Yahoo, AOL, Verizon, etc.)
description: '[!DNL Verizon Media Group] est généralement l’un des trois premiers domaines pour la plupart des listes B2C. Ils se comportent de manière quelque peu unique, car ils gèrent généralement ou volent le courrier en cas de problèmes de réputation.'
topics: Deliverability
kt: 5320
doc-type: article
activity: understand
team: TM
exl-id: 43e6d3cb-23c3-4076-8026-a1a08e76bd1b
source-git-commit: 68c403f915287e1a50cd276b67b3f48202f45446
workflow-type: tm+mt
source-wordcount: '290'
ht-degree: 3%

---

# [!DNL Verizon Media Group] (Yahoo, AOL, Verizon, etc.)

[!DNL Verizon Media Group] est généralement l’un des trois premiers domaines pour la plupart des listes B2C. Ils se comportent de manière quelque peu unique, car ils gèrent généralement ou volent le courrier en cas de problèmes de réputation.

Voici quelques points forts :

## Quelles données sont importantes ?

[!DNL Verizon Media Group] (VMG) a créé et conservé ses propres filtres de spam propriétaires, en utilisant un mélange de contenu, de filtrage d&#39;URL et de plaintes pour spam. Avec Gmail, ils sont l’un des premiers FAI à adopter qui filtre les emails par domaine ainsi que par adresse IP.

## Quelles données mettent-ils à disposition ?

VMG dispose d’une FBL utilisée pour transmettre les informations de plainte aux expéditeurs. Ils explorent également la possibilité d&#39;ajouter d&#39;autres données à l&#39;avenir.

## Réputation de l&#39;expéditeur

La réputation d’un expéditeur est composée d’une combinaison d’adresse IP, de domaine et d’adresse. La réputation est calculée à l’aide des composants traditionnels, y compris les plaintes, les pièges à spam, les adresses inactives ou mal formées et l’engagement. VMG utilise la limitation de débit (également appelée ralentissement) ainsi que le pliage en masse pour se défendre contre le spam. Elles complètent leurs systèmes de filtrage internes avec certaines listes bloquées [!DNL Spamhaus], y compris la PBL, SBL et XBL pour protéger leurs utilisateurs.

## Insights

VMG dispose de périodes de maintenance régulières pour les anciennes adresses électroniques inactives dernièrement. Cela signifie qu’il est courant d’observer une augmentation significative des rebonds d’adresse non valides, ce qui peut avoir un impact sur le taux de livraison pendant une courte période. Ils sont également sensibles aux taux élevés de rebonds d’adresses non valides d’un expéditeur, ce qui indique la nécessité de resserrer les politiques d’acquisition ou d’engagement. Les expéditeurs peuvent souvent avoir un impact négatif à environ 1 % des adresses non valides.
