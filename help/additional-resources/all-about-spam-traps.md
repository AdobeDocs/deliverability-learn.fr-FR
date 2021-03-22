---
title: Tout sur les pièges à pourriels
description: Découvrez comment comprendre, identifier et éviter les pièges à spam lors de la gestion de la délivrabilité.
feature: Ressources supplémentaires
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 3696ec013014ea41c634ac4829ec40977d224ff1
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 1%

---


# Tout sur les pièges à pourriels

Un piège de messages indésirables [spam](/help/metrics/spam-traps.md) est une adresse valide, sans message d&#39;erreur lorsque des messages électroniques sont envoyés à. Un piège à pourriels a pour mission principale : identifier les spammeurs ou les expéditeurs sans processus d&#39;hygiène des données.

## Qui gère ces adresses de piège à spam ?

Le premier type d&#39;adresses de piège de spam est la société de liste bloquée IP et domaine, comme SpamHaus, Sorbs, SpamCop. Ces sociétés ont un immense réseau d&#39;adresses qui sont distribuées sur diverses pages Internet comme site web, blog, forums pour que leurs adresses soient collectées par des spammeurs.

Le deuxième type de piège antispam est basé sur de vieilles principales adresses de FAI. Ces FAI disposent de leur propre réseau de piège à messages indésirables basé sur des adresses inactives reconverties dans un piège et chaque accès impacte la réputation de l&#39;adresse IP et du domaine de l&#39;expéditeur.

## Comment fonctionne-t-il ?

**Adresse électronique sans utilisateur** final : Ces adresses n&#39;ont pas et n&#39;auront jamais d&#39;utilisateur final qui puisse s&#39;inscrire aux bulletins d&#39;information ou à tout autre type de communication.

**Adresse électronique abandonnée par un utilisateur** : Après une période d’inactivité, les adresses sont désactivées par les FAI. Des messages de rebonds sont envoyés aux expéditeurs pour les informer de ce nouvel état. Les expéditeurs doivent envoyer ces adresses en quarantaine ou les supprimer des futures communications. Les FAI utilisent ces adresses transformées en &quot;piège à spam&quot; pour surveiller les expéditeurs qui ont des mauvaises pratiques.

## Comment reconnaître ou identifier un piège à spam ?

Il est difficile d&#39;identifier les pièges à spam, ces adresses doivent rester anonymes car elles sont utilisées pour identifier les mauvais expéditeurs. La plupart des FAI n&#39;ont pas de système ouvert et de clics pour surveiller les accès des expéditeurs inappropriés. Selon les définitions précédentes, il est possible de déterminer une capsule d&#39;adresses suspectes et de tester l&#39;efficacité de la sélection de la capsule.

## Pourquoi votre base de données est infectée par des pièges à messages indésirables ?

Votre base de données d&#39;adresses e-mail contient un piège de spam, comment cela pourrait-il être possible ? Les deux principales raisons sont le manque de procédures d&#39;hygiène dans la base de données ou la collecte des dysfonctionnements.

Ces quelques points vous aident à vérifier vos processus :

* Collect dysfunction :
   * D&#39;où viennent vos adresses électroniques ? Combien de sources sont utilisées pour collecter ces adresses ? Êtes-vous capable de les identifier ? Interne/d&#39;enregistrement ?
   * Votre système d’inclusion fonctionne-t-il correctement ?
   * Avez-vous vérifié les domaines et l&#39;alias de vos adresses ? Faites-le avec le tableau ci-dessous !
* Processus d&#39;hygiène des bases de données :
   * Quel est votre processus concernant l&#39;adresse inactive au cours des 12 derniers mois ?
   * Traitez-vous une quarantaine sur les rebonds logiciels comme &quot;utilisateur inactif&quot; ?
   * Quand avez-vous pris soin de votre base de données pour la dernière fois et essayé de la nettoyer ? Fais-le régulièrement.

## Alias et domaines à éviter

**Alias**

![](../../help/assets/aliases.png)

**Domaines**

![](../../help/assets/domains.png)