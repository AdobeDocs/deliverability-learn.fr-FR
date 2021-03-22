---
title: Démarrer une nouvelle plateforme
description: En savoir plus sur la gestion de la délivrabilité lors du démarrage d’une nouvelle plateforme avec Adobe Campaign.
feature: Mise en pratique
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 96ed84da391faaabd3001ddd6a411ddc1f46b033
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 57%

---


# Démarrer une nouvelle plate-forme {#starting-new-platform}

Il est essentiel de préserver la réputation de votre domaine et de votre adresse IP lors de la configuration d’une nouvelle plateforme à utiliser avec Adobe Campaign.

## Une étape sensible

Soyez très prudent lorsque vous commencez à envoyer des courriers électroniques sur une nouvelle plateforme, car la plateforme n&#39;a aucun historique d&#39;utilisation et aucune réputation lorsque les adresses IP d&#39;envoi n&#39;ont jamais été utilisées à cette fin.

Or rien n&#39;est plus suspect pour un FAI qu&#39;une adresse IP qui n&#39;a jamais envoyé d&#39;emails et qui commence subitement à envoyer des messages en masse. En effet, les spammeurs utilisent généralement des adresses IP &#39;&#39;inconnues&#39;&#39; (qui n&#39;ont jamais été placées sur liste bloquée) pour envoyer un maximum de messages pendant le laps de temps où ils n&#39;ont pas encore été détectés.

On ne peut donc pas espérer atteindre le régime de croisière en termes de débit dès le début de la mise en production. De surcroît on ne doit pas essayer d&#39;envoyer les premiers messages avec un tel débit, car cela conduirait les FAI à bloquer d&#39;autant plus sévèrement les adresses IP d&#39;envoi et à compromettre gravement la poursuite du démarrage.

## Principaux principes

Vous trouverez ci-dessous la liste des principaux principes à suivre lors du lancement d&#39;une nouvelle plateforme.

* Configurez un sous-domaine dédié qui est spécifique aux campagnes par courrier électronique envoyées depuis l’Adobe.

* Si vous disposez de ces informations, **importez des adresses non valides dans la table des quarantaines**.
Le démarrage d’une plate-forme s’accompagne souvent de l’utilisation d’une liste d’adresses inconnues jusqu’ici, qui n’est pas entièrement qualifiée. L’envoi de messages à des adresses non valides ou à des adresses servant de leurres contribuera à affaiblir la réputation de la plate-forme.

   * Si vous avez une liste d&#39;adresses non valides, il est dans votre intérêt de l&#39;importer dans la table de quarantaines avant de l&#39;envoyer pour la première fois. Le tableau de quarantaine est disponible via les menus **[!UICONTROL Administration > Campaign Management > Non deliverables Management > Non deliverables and addresses]** (Campaign Classic) et **[!UICONTROL Administration > Channels > Quarantines > Addresses]** (Campaign Standard).

   * Si on souhaite malgré tout requalifier les adresses invalides, il est nettement préférable de le faire une fois la réputation de la Plateforme établie et par petites parties afin de &quot;diluer&quot; dans le temps l&#39;usage des mauvaises adresses.

* **Limitez le débit** en limitant le nombre de mtachilds. Pour plus d’informations sur la modification de ce paramètre technique, contactez votre administrateur Adobe Campaign.

* **Augmentez progressivement les volumes envoyés** pour éviter que les emails soient marqués comme spam. Ne ciblez pas l’ensemble de la base de données dès le début, mais ajoutez plutôt une partie supplémentaire de la liste à chaque envoi. Vous devriez ainsi pouvoir augmenter le volume à chaque étape tout en réduisant le taux global d’adresses non valides. Pour un développement fluide de la phase de démarrage, vous pouvez utiliser des vagues.

* **Effectuez régulièrement des envois**. Dans une certaine mesure, il est préférable d&#39;envoyer régulièrement des petits plans plutôt que des campagnes de grande envergure de manière sporadique.
* **Accordez de l’attention aux rapports de diffusion**. La présence d’indicateurs d’erreur élevés peut révéler un paramètre technique mal configuré.

## Ressources supplémentaires

Pour en savoir plus sur les principes énumérés ci-dessus et leur mise en oeuvre avec Adobe Campaign, voir les sections suivantes :

* [Augmentez la réputation de vos emails grâce au rodage des adresses IP](../../help/additional-resources/increase-reputation-with-ip-warming.md)
* [Tout sur les pièges à pourriels](../../help/additional-resources/all-about-spam-traps.md)

**Adobe Campaign Classic**

* [Optimiser votre diffusion par le biais de quarantaines](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html#optimizing-your-delivery-through-quarantines)
* [Identifier les adresses mises en quarantaine pour l&#39;ensemble de la plate-forme](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html#identifying-quarantined-addresses-for-the-entire-platform)
* [Envoyer en plusieurs vagues](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-sending-the-delivery.html#sending-using-multiple-waves)
* [Surveillance des diffusions](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/about-delivery-monitoring.html#sending-messages)

**Adobe Campaign Standard **

* [Optimiser votre diffusion par le biais de quarantaines](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html#optimizing-your-delivery-through-quarantines)
* [Identifier les adresses mises en quarantaine pour l&#39;ensemble de la plate-forme](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html)
* [Contrôler une diffusion](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html)
