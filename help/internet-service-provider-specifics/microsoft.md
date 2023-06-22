---
title: Microsoft (Hotmail, Outlook, Windows Live, etc.)
description: Microsoft est généralement le deuxième ou le troisième plus grand fournisseur selon la composition de votre liste et il gère le trafic légèrement différent des autres FAI.
topics: Deliverability
jira: KT-5319
doc-type: article
activity: understand
team: TM
exl-id: d706cb90-828a-4ab3-8f93-c9bd71553d63
source-git-commit: 9444f8601f2f349398ee5deb9d5f4d4f7abb44f5
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 2%

---

# [!DNL Microsoft] ([!DNL Hotmail], [!DNL Outlook], [!DNL Windows Live], etc.)

[!DNL Microsoft] est généralement le deuxième ou le troisième plus grand fournisseur selon la composition de votre liste et il gère le trafic légèrement différent des autres FAI.

Voici quelques points forts :

## Quelles données sont importantes ?

[!DNL Microsoft] se concentre sur la réputation de l’expéditeur, les plaintes, l’engagement des utilisateurs et leur propre groupe d’utilisateurs de confiance (également appelés données de réputation de l’expéditeur ou SRD) qu’ils interrogent pour obtenir des commentaires.

## Quelles données mettent-ils à disposition ?

[!DNL Microsoft]l’outil de reporting propriétaire de l’expéditeur, [!DNL Smart Network Data Services] (SNDS) vous permet d’afficher des mesures relatives au volume de courrier que vous envoyez et au nombre de courriers acceptés, ainsi que les plaintes et pièges à spam. Gardez à l’esprit que les données partagées sont un échantillon et ne reflètent pas des nombres exacts, mais qu’elles représentent le mieux la manière dont les [!DNL Microsoft] vous considère comme un expéditeur. [!DNL Microsoft] ne fournit pas d’informations publiques sur leur groupe d’utilisateurs de confiance, mais ces données sont disponibles via la variable [!DNL Return Path Certification] pour des frais supplémentaires.

## Réputation de l&#39;expéditeur

[!DNL Microsoft] est traditionnellement axé sur l’envoi d’adresses IP dans leurs évaluations de réputation et décisions de filtrage. Ils travaillent également activement à l’extension de leurs fonctionnalités de domaine d’envoi. Tous deux sont en grande partie pilotés par les influenceurs traditionnels de réputation, comme les plaintes et les pièges à spam. La délivrabilité peut également être fortement influencée par le programme de certification Return Path, qui comporte des exigences de programme quantitatives et qualitatives spécifiques.

## Insights

[!DNL Microsoft] combine tous leurs domaines de réception pour établir et suivre la réputation de l’envoi. Cela inclut [!DNL Hotmail], [!DNL Outlook], MSN, [!DNL Windows Live], etc., ainsi que tout courrier électronique hébergé par une entreprise Office 365. [!DNL Microsoft] peuvent être particulièrement sensibles aux fluctuations du volume. Par conséquent, envisagez d’appliquer des stratégies spécifiques pour augmenter ou diminuer les envois à partir de grands envois plutôt que de permettre des changements soudains basés sur le volume.

[!DNL Microsoft] est également particulièrement strict pendant les premiers jours du réchauffement de la IP, ce qui signifie généralement que la plupart des mails sont filtrés initialement. La plupart des FAI considèrent les expéditeurs comme innocents jusqu&#39;à ce qu&#39;ils soient reconnus coupables. [!DNL Microsoft] est le contraire et vous considère coupable jusqu&#39;à ce que vous vous prouviez innocent.
