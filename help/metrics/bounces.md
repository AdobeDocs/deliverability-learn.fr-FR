---
title: Bounces
description: Découvrez les différents types de bounces.
feature: Mesures
topics: Deliverability
kt: 7047
thumbnail: kt7047.jpg
doc-type: article
activity: understand
team: ACS
translation-type: ht
source-git-commit: 283f1cb2bb40818e11daa1a3753e8428b47e08ee
workflow-type: ht
source-wordcount: '478'
ht-degree: 100%

---


# Bounces

Les bounces sont le résultat d’une tentative de diffusion et d’un échec lorsque le FAI fournit des avis d’échec. Le traitement de la gestion des bounces est un élément essentiel de l&#39;hygiène des listes. Une fois qu’un email donné a fait l’objet de plusieurs bounces, ce processus le signale pour suppression. Le nombre et le type de bounces requis pour déclencher la suppression varient d’un système à un autre. Ce processus empêche les systèmes de continuer à envoyer des adresses email non valides. Les bounces sont l&#39;un des éléments clés de données que les FAI utilisent pour déterminer la réputation des adresses IP. Il est très important de surveiller cette mesure. La méthode la plus courante pour mesurer la diffusion des messages marketing consiste à comparer la mesure « Délivrés » à la mesure « Bounces » : plus le pourcentage Délivrés est élevé, mieux c&#39;est.

Nous allons découvrir plus en détail deux types différents de bounces.

## Hard bounces

Les hard bounces sont des échecs permanents générés après qu’un FAI ait déterminé qu’une tentative d’envoi à une adresse d’abonné n’était pas délivrable. Dans Adobe Campaign, les hard bounces classés comme non délivrables sont ajoutés à la quarantaine, ce qui signifie qu’ils ne feront pas l&#39;objet d&#39;une nouvelle tentative. Dans certains cas, un hard bounce peut être ignoré si la cause de l&#39;échec est inconnue.
Voici quelques exemples courants de hard bounces :

* Adresse inexistante
* Compte désactivé
* Syntaxe incorrecte
* Domaine incorrect

## Soft bounces

Les soft bounces sont des échecs temporaires que les FAI génèrent lorsqu&#39;ils ont des difficultés à diffuser un email. Les erreurs soft feront l’objet de plusieurs reprises (avec des écarts selon l’utilisation de paramètres de diffusion personnalisés ou d’usine) afin de réussir la diffusion. Les adresses qui produisent continuellement des soft bounces ne seront pas ajoutées à la quarantaine tant que le nombre maximal de reprises n’aura pas été tenté (ce qui varie, à nouveau, selon les paramètres). Voici quelques-unes des causes courantes de soft bounces :

* Boîte pleine
* Serveur de réception d’emails en panne
* Problèmes liés à la réputation de l&#39;expéditeur

![Types de bounces](../assets/bounce-types.png)

>[!NOTE]
>
>Les bounces sont un indicateur clé d’un problème de réputation, car ils peuvent mettre en évidence une source de données incorrecte (hard bounce) ou un problème de réputation avec un FAI (soft bounce).
>
>Les soft bounces se produisent souvent dans le cadre de l’envoi d’un email et doivent être autorisés à être résolus pendant les reprises avant de devenir un véritable problème de délivrabilité. Si votre taux de soft bounces est supérieur à 30 % pour un seul FAI et qu’il n’est pas résolu dans un délai de 24 heures, il est préférable de contacter votre consultant Adobe Campaign en matière de délivrabilité.

## Ressources spécifiques au produit

**Adobe Campaign Classic**

* [Types de diffusion en échec et raisons](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html?lang=fr-FR#delivery-failure-types-and-reasons)
* [Gestion des emails bounce](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-delivery-failures.html?lang=fr-FR#bounce-mail-management)
* [Rapport sur les emails non remis et les bounces](https://experienceleague.adobe.com/docs/campaign-classic/using/reporting/reports-on-deliveries/global-reports.html?lang=fr-FR#non-deliverables-and-bounces)

**Adobe Campaign Standard**

* [Types de diffusion en échec et raisons](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-delivery-failures.html?lang=fr-FR#delivery-failure-types-and-reasons)
* [Qualification des emails bounce](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-delivery-failures.html?lang=fr-FR#bounce-mail-qualification)
* [Rapport récapitulatif des bounces](https://experienceleague.adobe.com/docs/campaign-standard/using/reporting/list-of-reports/bounce-summary.html?lang=fr-FR#reporting)
