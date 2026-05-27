---
title: Microsoft (Hotmail, Outlook, Windows Live, etc.)
description: Microsoft est généralement le deuxième ou troisième fournisseur le plus important selon la composition de votre liste, et il gère le trafic légèrement différemment des autres FAI.
topics: Deliverability
jira: KT-5319
doc-type: article
activity: understand
role: Admin, Leader, User
level: Beginner
team: TM
exl-id: d706cb90-828a-4ab3-8f93-c9bd71553d63
TQID: https://experienceleague.adobe.com/pbp5vbHUIHSL9zL9gQf4LpIhEYZI1umEesy3czbJx-4
product_v2: id: b27e5950-9033-45ac-9f86-eb22e567f615id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: ea90ebee-5c84-42d9-8b21-006bdabc95a3
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: c66ffd68-0f65-42bb-aa23-b4020f12e0bdid: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: e1e0219c-f879-479f-8427-888ed2a6e9c2
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 335
ht-degree: 2%

---

# [!DNL Microsoft] ([!DNL Hotmail], [!DNL Outlook], [!DNL Windows Live], etc.)

[!DNL Microsoft] est généralement le deuxième ou le troisième plus grand fournisseur selon la composition de votre liste, et il gère le trafic légèrement différent des autres FAI.

Voici quelques points forts :

## Les données importantes

[!DNL Microsoft] se concentre sur la réputation de l&#39;expéditeur, les plaintes, l&#39;interaction client et leur propre groupe d&#39;utilisateurs de confiance (également appelé Sender Reputation Data ou SRD), qu&#39;ils interrogent pour obtenir des commentaires.

## Quelles données rendent-ils disponibles ?

[!DNL Smart Network Data Services] (SNDS), l&#39;outil de reporting d&#39;expéditeur propriétaire de [!DNL Microsoft], vous permet de consulter des mesures sur la quantité d&#39;e-mails envoyés et acceptés, ainsi que des plaintes et des pièges à spam. Gardez à l’esprit que les données partagées sont un exemple et ne reflètent pas les nombres exacts, mais qu’elles représentent mieux la manière dont [!DNL Microsoft] vous perçoit en tant qu’expéditeur ou expéditrice. [!DNL Microsoft] ne fournit pas publiquement d&#39;information sur son groupe d&#39;utilisateurs de confiance, mais ces données sont accessibles par l&#39;entremise du programme [!DNL Return Path Certification] moyennant des frais supplémentaires.

## Réputation de l&#39;expéditeur

[!DNL Microsoft] s’est traditionnellement concentré sur l’envoi d’adresses IP dans ses évaluations de réputation et ses décisions de filtrage. Ils travaillent également activement à l’extension des fonctionnalités de leur domaine d’envoi. Les deux sont en grande partie motivés par les influenceurs de réputation traditionnels, comme les plaintes et les pièges à spam. La délivrabilité peut également être fortement influencée par le programme de certification Return Path, qui comporte des exigences spécifiques quantitatives et qualitatives.

## Insights

[!DNL Microsoft] combine tous ses domaines de réception pour établir et suivre la réputation de l&#39;envoi. Cela inclut [!DNL Hotmail], [!DNL Outlook], MSN, [!DNL Windows Live], etc., ainsi que tous les e-mails hébergés dans Office 365. [!DNL Microsoft] peut être particulièrement sensible aux fluctuations de volume. Par conséquent, envisagez d’appliquer des stratégies spécifiques pour augmenter et diminuer les envois volumineux plutôt que de permettre des changements soudains en fonction du volume.

[!DNL Microsoft] est également particulièrement strict pendant les premiers jours du réchauffement des adresses IP, ce qui signifie généralement que la plupart des e-mails sont filtrés au départ. La plupart des FAI considèrent les expéditeurs innocents jusqu&#39;à preuve du contraire. [!DNL Microsoft]&#39;est le contraire et vous considère coupable jusqu&#39;à ce que vous vous prouvez innocent.
