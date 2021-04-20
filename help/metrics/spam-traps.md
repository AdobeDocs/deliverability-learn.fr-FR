---
title: Pièges de courriers indésirables
description: Découvrez les différents types de pièges de courriers indésirables.
feature: Metrics
topics: Deliverability
kt: 7050
thumbnail: kt7050.jpg
doc-type: article
activity: understand
team: ACS
exl-id: ffacc1b1-bf3f-466e-9a1d-63aad4d2ec45
translation-type: ht
source-git-commit: e433002423bd1ab2f4a89425198c16160dae0719
workflow-type: ht
source-wordcount: '454'
ht-degree: 100%

---

# Pièges de courriers indésirables

Il existe des pièges de courriers indésirables qui permettent d’identifier les messages envoyés par des expéditeurs frauduleux ou qui ne suivent pas les bonnes pratiques en matière d&#39;email. En règle générale, l&#39;adresse email du piège de courriers indésirables n&#39;est pas publiée publiquement et est presque impossible à identifier. La diffusion d&#39;emails à des pièges de courriers indésirables peut avoir un impact sur votre réputation avec des degrés de gravité différents selon le type de piège et le FAI. Pour en savoir plus sur les différents types de pièges de courriers indésirables, consultez les sections ci-après.

## Recyclé

Les pièges de courriers indésirables recyclés sont des adresses qui étaient autrefois valides mais qui ne sont plus utilisées. L&#39;un des principaux moyens pour garder les listes aussi propres que possible est d&#39;envoyer régulièrement des emails à votre liste entière et de supprimer de manière appropriée les emails bounces. Cela permet de mettre en quarantaine les adresses email abandonnées et de les empêcher d&#39;être utilisées.

Dans certains cas, une adresse peut être recyclée sous 30 jours. L&#39;envoi régulier est un aspect essentiel d&#39;une bonne hygiène des listes, avec la suppression régulière des utilisateurs inactifs. Les **campagnes de réengagement** font généralement partie de programmes sophistiqués de marketing par email. Ce style de campagne permet à l’expéditeur de tenter de récupérer des utilisateurs qui autrement ne feraient plus l&#39;objet d&#39;envois d&#39;emails.

## Coquille

Un piège de courrier indésirable avec coquille est une adresse qui contient une faute d&#39;orthographe ou une déformation. Cela se produit souvent avec des fautes d&#39;orthographe connues de domaines majeurs comme Gmail (ex : gmial est une faute de frappe courante). Les FAI et les autres opérateurs de liste bloquée enregistreront les mauvais noms de domaine connus pour être utilisés comme piège de courriers indésirables afin d&#39;identifier les spammeurs et de mesurer la santé des expéditeurs. Le meilleur moyen d’éviter les pièges de courriers indésirables consiste à utiliser un **processus de double opt-in** pour la collecte de listes.

## Intact

Un piège de courriers indésirables intact est une adresse qui n&#39;a pas d&#39;utilisateur final et n&#39;a jamais eu d&#39;utilisateur final. Il s’agit d’une adresse créée uniquement pour identifier les messages indésirables. Il s&#39;agit du type de piège de courriers indésirables le plus efficace, car il est pratiquement impossible de l&#39;identifier et nécessite un effort considérable pour le nettoyer de votre liste. La plupart des listes bloquées utilisent des pièges de courriers indésirables intacts pour répertorier des expéditeurs non fiables. La seule façon d&#39;éviter que les pièges de courriers indésirables ne viennent infecter votre liste d’emails marketing plus large consiste à utiliser un **processus de double opt-in** pour la collecte de listes.

## Ressources supplémentaires

* Pour en savoir plus sur l’identification et l’évitement des spam traps, consultez [cette section](/help/additional-resources/all-about-spam-traps.md).
* Pour en savoir plus sur l’amélioration de la délivrabilité grâce à des stratégies de réengagement, consultez [cette section](/help/additional-resources/re-engagement.md).

## Ressources spécifiques au produit

**Adobe Campaign Classic**

* [SpamAssassin](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/deliverability-management/spamassassin.html?lang=fr-FR#using-spamassassin)
* [Création d’un formulaire d’abonnement avec double opt-in](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-forms/use-cases--web-forms.html?lang=fr-FR#create-a-subscription--form-with-double-opt-in)

**Adobe Campaign Standard**

* [Prévisualisation de votre analyse email et anti-spam](https://experienceleague.adobe.com/docs/campaign-standard-learn/tutorials/designing-content/email-designer/preview-your-email.html?lang=fr#designing-content)
* [Processus de double opt-in](https://experienceleague.adobe.com/docs/campaign-standard/using/communication-channels/landing-pages/setting-up-a-double-opt-in-process.html?lang=fr#communication-channels)
