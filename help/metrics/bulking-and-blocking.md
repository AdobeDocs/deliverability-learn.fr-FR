---
title: Bloquer les emails et les envoyer vers les courriers indésirables
description: Découvrez pourquoi les FAI placent des emails dans des dossiers de courriers indésirables ou les bloquent.
topics: Deliverability
jira: KT-7051
thumbnail: kt7051.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 4b280f90-73b9-4b88-adb8-57b6a46ddad7
TQID: https://experienceleague.adobe.com/mNz7Z6yQjlK7-NShGkgXNR8hp9kKUXDl9nHzMG4j3Q4
product_v2: id: b27e5950-9033-45ac-9f86-eb22e567f615id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: c5f60233-d5ea-4453-a799-0ad258b4d399id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 327
ht-degree: 100%

---

# Envoi vers les courriers indésirables et blocage

## Envoi vers les courriers indésirables

L&#39;envoi vers les courriers indésirables est la diffusion de l&#39;email dans le dossier des spams ou de courrier indésirable d&#39;un FAI. Il est identifiable lorsqu’un taux d’ouverture inférieur à la normale (et parfois un taux de clics) est associé à un taux de diffusion élevé. Les raisons pour lesquelles les emails sont envoyés vers les courriers indésirables varient selon le FAI. En règle générale, cependant, si des messages sont placés dans le dossier d&#39;envoi vers les courriers indésirables, un indicateur qui influence la réputation d&#39;envoi (l&#39;hygiène de liste, par exemple) doit être réévalué. Il s’agit d’un signal indiquant que la réputation diminue, ce qui est un problème qui doit être corrigé immédiatement avant d’affecter d’autres campagnes. Travaillez avec votre consultant Adobe en délivrabilité pour résoudre les problèmes d&#39;envoi vers les courriers indésirables en fonction de votre situation.

## Blocage

Un blocage survient lorsque les indicateurs de courriers indésirables atteignent les seuils de fournisseurs de FAI propriétaires et que le FAI commence à bloquer les e-mails (visible par des tentatives de publipostage rejetées) d’un expéditeur. Il existe différents types de blocages. En règle générale, des blocages se produisent spécifiquement à une adresse IP, mais ils peuvent également se produire au niveau du domaine ou de l’entité d’envoi. La résolution d&#39;un blocage nécessite une expertise spécifique. Veuillez donc contacter votre consultant Adobe en délivrabilité pour obtenir de l&#39;aide.

## Liste bloquée

Une liste bloquée se produit lorsqu’un responsable de listes bloquées tiers enregistre un comportement de type spammer associé à un expéditeur. La cause d&#39;une liste bloquée est parfois publiée par le parti de liste bloquée. Une liste est généralement basée sur l’adresse IP, mais dans les cas les plus graves, elle peut être établie par plage d’adresses IP ou même par domaine d’envoi. La résolution d&#39;une liste bloquée doit faire appel à l&#39;assistance de votre consultant Adobe en délivrabilité afin de résoudre et d&#39;empêcher toute nouvelle liste. Certaines listes sont extrêmement sévères et peuvent causer des problèmes de réputation à long terme, qui sont difficiles à résoudre. Le résultat d&#39;une liste bloquée varie selon la liste bloquée mais peut avoir un impact sur la diffusion de tous les emails.

## Ressources supplémentaires

* En savoir plus sur les [Listes Blackhole en temps réel](/help/additional-resources/blocklist-databases.md) qui gèrent des bases de données d’adresses IP et de domaines susceptibles d’être utilisées par les spammeurs.
