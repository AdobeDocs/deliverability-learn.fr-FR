---
title: Retours
description: Découvrez les différents types de rebonds
feature: Mesures
topics: Deliverability
kt: 7047
thumbnail: kt7047.jpg
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: d42a8c3b06308fca0cf3e9db8d634a767fc0cdc6
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 3%

---


# Retours

Les rebonds sont le résultat d’une tentative de diffusion et d’un échec lorsque le fournisseur de services Internet fournit des avis d’échec. Le traitement de la manipulation des rebonds est un élément essentiel de l&#39;hygiène des listes. Une fois qu’un message électronique donné a rebondi plusieurs fois de suite, ce processus le signale pour suppression. Le nombre et le type de rebonds requis pour déclencher la suppression varient d’un système à l’autre. Ce processus empêche les systèmes de continuer à envoyer des adresses électroniques non valides. Les rebonds sont l&#39;un des éléments clés de données que les FAI utilisent pour déterminer la réputation de leur IP. Il est très important de garder un oeil sur cette mesure. La méthode la plus courante pour mesurer la diffusion des messages marketing consiste à comparer &quot;distribués&quot; et &quot;rebondissés&quot; : plus le pourcentage de prestations est élevé, mieux c&#39;est.

Nous allons creuser deux types différents de rebonds.

## Hard bounces

Les rebonds en dur sont des échecs permanents générés après qu’un FAI ait déterminé qu’une tentative d’envoi à une adresse d’abonné n’était pas livrable. En Adobe Campaign, les rebonds durs classés comme non livrables sont ajoutés à la quarantaine, ce qui signifie qu’ils ne seront pas tentés de nouveau. Dans certains cas, un rebond brutal serait ignoré si la cause de l&#39;échec est inconnue.
Voici quelques exemples courants de rebonds durs :

* L&#39;adresse n&#39;existe pas
* Compte désactivé
* Syntaxe incorrecte
* Domaine incorrect

## Soft bounces

Les rebonds à la baisse sont des échecs temporaires que les FAI génèrent lorsqu&#39;ils ont des difficultés à livrer du courrier. Les échecs d’optimisation se répètent à plusieurs reprises (avec des écarts selon l’utilisation de paramètres de diffusion personnalisés ou prêts à l’emploi) afin de tenter une diffusion réussie. Les adresses qui rebondissent continuellement doucement ne seront pas ajoutées à la quarantaine tant que le nombre maximal de Reprises n’aura pas été tenté (ce qui varie à nouveau selon les paramètres). Voici quelques-unes des causes courantes des rebonds en douceur :

* Boîte pleine
* Réception du serveur de messagerie vers le bas
* Problèmes de réputation de l&#39;expéditeur

![types de rebond](../assets/bounce-types.png)

>[!NOTE]
>
>Les rebonds sont un indicateur clé d’un problème de réputation car ils peuvent mettre en évidence une source de données incorrecte (rebond) ou un problème de réputation avec un fournisseur de services Internet (rebond en douceur).
>
>Les retours à l’écran se produisent souvent dans le cadre de l’envoi d’un courrier électronique et doivent être autorisés à résoudre ce problème pendant le traitement de la nouvelle tentative avant de le caractériser comme un véritable problème de délivrabilité. Si votre taux de rebonds en douceur est supérieur à 30 % pour un seul FAI et qu’il ne se résout pas dans les 24 heures, il est préférable de soulever une question auprès de votre consultant en livrabilité Adobe Campaign.

## Ressources spécifiques au produit

**Adobe Campaign Standard **

* [Liste des rapports - Récapitulatif des rebonds (documentation du produit)](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/list-of-reports/bounce-summary.html?lang=en#reporting)
* [Comprendre les échecs de diffusion (documentation du produit)](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-delivery-failures.html?lang=en#about-delivery-failures)

**Adobe Campaign Classic**

* [Comprendre les échecs de diffusion (documentation du produit)](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html?lang=en#sending-messages)