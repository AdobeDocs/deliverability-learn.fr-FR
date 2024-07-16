---
title: Microsoft (Hotmail, Outlook, Windows Live, etc.)
description: Microsoft est généralement le deuxième ou le troisième plus grand fournisseur selon la composition de votre liste et il gère le trafic légèrement différent des autres FAI.
topics: Deliverability
jira: KT-5319
doc-type: article
activity: understand
role: Admin, Leader, User
level: Beginner
team: TM
exl-id: d706cb90-828a-4ab3-8f93-c9bd71553d63
source-git-commit: 6b312cdbba496818337c97ec4f42962aea757901
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 2%

---

# [!DNL Microsoft] ([!DNL Hotmail], [!DNL Outlook], [!DNL Windows Live], etc.)

[!DNL Microsoft] est généralement le deuxième ou le troisième plus grand fournisseur selon la composition de votre liste et il gère le trafic légèrement différent des autres FAI.

Voici quelques points forts :

## Données importantes

[!DNL Microsoft] se concentre sur la réputation de l’expéditeur, les plaintes, l’engagement des utilisateurs et leur propre groupe d’utilisateurs de confiance (également appelé Sender Reputation Data ou SRD) qu’ils interrogent pour obtenir des commentaires.

## Quelles données mettent-ils à disposition ?

L&#39;outil de reporting propriétaire de l&#39;expéditeur [!DNL Microsoft], [!DNL Smart Network Data Services] (SNDS), vous permet d&#39;afficher des mesures sur le volume de courrier que vous envoyez et le nombre de courriers acceptés, ainsi que les plaintes et pièges à spam. Gardez à l’esprit que les données partagées sont un échantillon et ne reflètent pas des nombres exacts, mais qu’elles représentent le mieux la manière dont [!DNL Microsoft] vous considère comme un expéditeur. [!DNL Microsoft] ne fournit pas d’informations publiques sur son groupe d’utilisateurs de confiance, mais ces données sont disponibles via le programme [!DNL Return Path Certification] moyennant des frais supplémentaires.

## Réputation de l&#39;expéditeur

[!DNL Microsoft] s’est traditionnellement concentré sur l’envoi d’adresses IP dans leurs évaluations de réputation et décisions de filtrage. Ils travaillent également activement à l’extension de leurs fonctionnalités de domaine d’envoi. Tous deux sont en grande partie pilotés par les influenceurs traditionnels de réputation, comme les plaintes et les pièges à spam. La délivrabilité peut également être fortement influencée par le programme de certification Return Path, qui comporte des exigences de programme quantitatives et qualitatives spécifiques.

## Insights

[!DNL Microsoft] combine tous leurs domaines de réception pour établir et suivre la réputation d’envoi. Cela inclut [!DNL Hotmail], [!DNL Outlook], MSN, [!DNL Windows Live], etc., ainsi que tout e-mail hébergé dans Office 365. [!DNL Microsoft] peut être particulièrement sensible aux fluctuations de volume. Par conséquent, envisagez d’appliquer des stratégies spécifiques pour augmenter ou diminuer à partir d’envois volumineux plutôt que d’autoriser des changements soudains basés sur le volume.

[!DNL Microsoft] est également particulièrement strict pendant les premiers jours du réchauffement de l’IP, ce qui signifie généralement que la plupart des courriers sont filtrés initialement. La plupart des FAI considèrent les expéditeurs comme innocents jusqu&#39;à ce qu&#39;ils soient reconnus coupables. [!DNL Microsoft] est l&#39;inverse et vous considère coupable jusqu&#39;à ce que vous vous prouviez innocent.
