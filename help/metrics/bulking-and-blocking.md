---
title: Bloquer les emails et les envoyer vers les courriers indésirables
description: Découvrez pourquoi les FAI placent des emails dans des dossiers de courriers indésirables ou les bloquent.
topics: Deliverability
kt: 7051
thumbnail: kt7051.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 4b280f90-73b9-4b88-adb8-57b6a46ddad7
source-git-commit: 68c403f915287e1a50cd276b67b3f48202f45446
workflow-type: ht
source-wordcount: '321'
ht-degree: 100%

---

# Envoi vers les courriers indésirables et blocage

## Envoi vers les courriers indésirables

L&#39;envoi vers les courriers indésirables est la diffusion de l&#39;email dans le dossier des spams ou de courrier indésirable d&#39;un FAI. Il est identifiable lorsqu’un taux d’ouverture inférieur à la normale (et parfois un taux de clics) est associé à un taux de diffusion élevé. Les raisons pour lesquelles les emails sont envoyés vers les courriers indésirables varient selon le FAI. En règle générale, cependant, si des messages sont placés dans le dossier d&#39;envoi vers les courriers indésirables, un indicateur qui influence la réputation d&#39;envoi (l&#39;hygiène de liste, par exemple) doit être réévalué. Il s’agit d’un signal indiquant que la réputation diminue, ce qui est un problème qui doit être corrigé immédiatement avant d’affecter d’autres campagnes. Travaillez avec votre consultant Adobe en délivrabilité pour résoudre les problèmes d&#39;envoi vers les courriers indésirables en fonction de votre situation.

## Blocage

Un blocage survient lorsque les indicateurs de courriers indésirables atteignent les seuils de fournisseurs de FAI propriétaires et que le FAI commence à bloquer les emails (visible par des tentatives de publipostage retournées) d&#39;un expéditeur. Il existe différents types de blocages. En règle générale, des blocages se produisent spécifiquement à une adresse IP, mais ils peuvent également se produire au niveau du domaine ou de l’entité d’envoi. La résolution d&#39;un blocage nécessite une expertise spécifique. Veuillez donc contacter votre consultant Adobe en délivrabilité pour obtenir de l&#39;aide.

## Liste bloquée

Une liste bloquée se produit lorsqu’un responsable de listes bloquées tiers enregistre un comportement de type spammer associé à un expéditeur. La cause d&#39;une liste bloquée est parfois publiée par le parti de liste bloquée. Une liste est généralement basée sur l’adresse IP, mais dans les cas les plus graves, elle peut être établie par plage d’adresses IP ou même par domaine d’envoi. La résolution d&#39;une liste bloquée doit faire appel à l&#39;assistance de votre consultant Adobe en délivrabilité afin de résoudre et d&#39;empêcher toute nouvelle liste. Certaines listes sont extrêmement sévères et peuvent causer des problèmes de réputation à long terme, qui sont difficiles à résoudre. Le résultat d&#39;une liste bloquée varie selon la liste bloquée mais peut avoir un impact sur la diffusion de tous les emails.

## Ressources supplémentaires

* En savoir plus sur les [Listes Blackhole en temps réel](/help/additional-resources/blocklist-databases.md) qui gèrent des bases de données d’adresses IP et de domaines susceptibles d’être utilisées par les spammeurs.
