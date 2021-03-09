---
title: Groupe multimédia Verizon (Yahoo, AOL, Verizon, etc.)
description: '[!DNL Verizon Media Group] est généralement l''un des trois premiers domaines pour la plupart des listes B2C. Ils se comportent de façon quelque peu unique, car ils bloquent ou bloquent généralement le courrier en masse en cas de problèmes de réputation.'
feature: FSI
topics: Deliverability
kt: 5320
doc-type: article
activity: understand
team: TM
translation-type: tm+mt
source-git-commit: 992bfc9d0aff9daf29fa6878ead19372b065b436
workflow-type: tm+mt
source-wordcount: '291'
ht-degree: 1%

---


# [!DNL Verizon Media Group] (Yahoo, AOL, Verizon, etc.)

[!DNL Verizon Media Group] est généralement l&#39;un des trois premiers domaines pour la plupart des listes B2C. Ils se comportent de façon quelque peu unique, car ils bloquent ou bloquent généralement le courrier en masse en cas de problèmes de réputation.

Voici quelques points forts :

## Quelles sont les données importantes ?

[!DNL Verizon Media Group] (VMG) a créé et entretient ses propres filtres de spam propriétaires, en utilisant un mélange de contenu et de filtrage d&#39;URL et de plaintes de spam. Avec Gmail, ils sont l&#39;un des premiers fournisseurs d&#39;accès à Internet à adopter un filtre de courriel par domaine et par adresse IP.

## Quelles données sont-elles mises à disposition ?

VMG a une FBL utilisée pour transmettre les informations de plainte aux expéditeurs. Ils étudient également la possibilité d&#39;ajouter d&#39;autres données à l&#39;avenir.

## la réputation de l&#39;expéditeur

La réputation d’un expéditeur est composée d’une combinaison d’adresse IP, de domaine et d’adresse. La réputation est calculée à l&#39;aide des composants traditionnels, y compris les plaintes, les pièges à pourriels, les adresses inactives ou mal formées et l&#39;engagement. VMG utilise la limitation de débit (également appelée limitation) ainsi que le pliage en vrac pour se protéger contre le spam. Ils complètent leurs systèmes de filtrage internes avec certaines listes bloquées [!DNL Spamhaus], dont la PBL, SBL et XBL, afin de protéger leurs utilisateurs.

## Insights

VMG dispose de périodes de maintenance régulières pour les anciennes adresses électroniques inactives. Cela signifie qu&#39;il est courant d&#39;observer une augmentation significative des rebonds d&#39;adresse non valides, ce qui peut avoir un impact sur votre taux de livraison pendant une courte période de temps. Ils sont également sensibles aux taux élevés de rebonds d&#39;adresse non valides d&#39;un expéditeur, ce qui indique la nécessité de resserrer les politiques d&#39;acquisition ou d&#39;engagement. Les expéditeurs peuvent souvent ressentir un impact négatif à environ 1 % d&#39;adresses non valides.
