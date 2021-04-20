---
title: Microsoft (Hotmail, Outlook, Windows Live, etc.)
description: Microsoft est généralement le deuxième ou le troisième plus grand fournisseur selon la composition de votre liste et il gère le trafic légèrement différent des autres fournisseurs d'accès à Internet.
feature: ISPs
topics: Deliverability
kt: 5319
doc-type: article
activity: understand
team: TM
translation-type: tm+mt
source-git-commit: 992bfc9d0aff9daf29fa6878ead19372b065b436
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 1%

---


# [!DNL Microsoft] ([!DNL Hotmail], [!DNL Outlook], [!DNL Windows Live], etc.)

[!DNL Microsoft] est généralement le deuxième ou le troisième plus important fournisseur selon la composition de votre liste, et il gère le trafic légèrement différent des autres FAI.

Voici quelques points forts :

## Quelles sont les données importantes ?

[!DNL Microsoft] se concentre sur la réputation de l’expéditeur, les plaintes, l’engagement des utilisateurs et leur propre groupe d’utilisateurs de confiance (également appelés données de réputation de l’expéditeur ou SRD) qu’ils interrogent pour obtenir des commentaires.

## Quelles données sont-elles mises à disposition ?

[!DNL Microsoft]L’outil de rapports d’expéditeur propriétaire,  [!DNL Smart Network Data Services] (SNDS), vous permet d’afficher des mesures concernant le volume de courrier que vous envoyez et le volume de courrier accepté, ainsi que les plaintes et les pièges à messages indésirables. Gardez à l’esprit que les données partagées constituent un échantillon et ne reflètent pas les nombres exacts, mais qu’elles représentent mieux la façon dont [!DNL Microsoft] vous vue en tant qu’expéditeur. [!DNL Microsoft] ne fournit pas publiquement d’informations sur leur groupe d’utilisateurs de confiance, mais ces données sont disponibles par l’intermédiaire du  [!DNL Return Path Certification] programme moyennant un supplément.

## la réputation de l&#39;expéditeur

[!DNL Microsoft] a toujours été axé sur l’envoi de la PI dans leurs évaluations de réputation et leurs décisions de filtrage. Ils s&#39;efforcent également d&#39;étendre leurs capacités de domaine d&#39;envoi. Tous deux sont en grande partie conduits par les influenceurs traditionnels de réputation, comme les plaintes et les pièges à pourriels. La délivrabilité peut également être fortement influencée par le programme de certification des chemins de retour, qui comporte des exigences spécifiques en matière de programme quantitatif et qualitatif.

## Insights

[!DNL Microsoft] combine tous leurs domaines de réception pour établir et suivre la réputation d’envoi. Cela inclut [!DNL Hotmail], [!DNL Outlook], MSN, [!DNL Windows Live], etc., ainsi que tout courrier électronique hébergé par Office 365. [!DNL Microsoft] peut être particulièrement sensible aux fluctuations du volume. Par conséquent, pensez à appliquer des stratégies spécifiques pour augmenter ou diminuer les émissions à partir de grandes émissions plutôt que de permettre des changements soudains basés sur le volume.

[!DNL Microsoft] est également particulièrement stricte pendant les premiers jours du réchauffement de la PI, ce qui signifie généralement que la plupart des courriels sont filtrés initialement. La plupart des FAI considèrent que les expéditeurs sont innocents jusqu&#39;à preuve de culpabilité. [!DNL Microsoft] est le contraire et vous considère coupable jusqu&#39;à ce que vous vous prouviez innocent.
