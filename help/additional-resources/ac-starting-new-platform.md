---
title: Démarrage d’une nouvelle plateforme
description: En savoir plus sur la gestion de la délivrabilité lors du démarrage d’une nouvelle plateforme avec Adobe Campaign.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 6c9ade01-3052-4311-af80-888294820024
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 56%

---

# Démarrage d’une nouvelle plateforme {#starting-new-platform}

Le maintien de la réputation de votre domaine et de votre adresse IP est essentiel lors de la configuration d’une nouvelle plateforme à utiliser avec Adobe Campaign.

## Une étape sensible

Soyez très prudent lorsque vous commencez à envoyer des emails sur une nouvelle plateforme, car la plateforme n&#39;a aucun historique d&#39;utilisation et aucune réputation lorsque les adresses IP d&#39;envoi n&#39;ont jamais été utilisées à cette fin.

Or rien n&#39;est plus suspect pour un FAI qu&#39;une adresse IP qui n&#39;a jamais envoyé d&#39;emails et qui commence subitement à envoyer des messages en masse. En effet, les spammeurs utilisent généralement des adresses IP &#39;&#39;inconnues&#39;&#39; (qui n&#39;ont jamais été placées sur liste bloquée) pour envoyer un maximum de messages pendant le laps de temps où ils n&#39;ont pas encore été détectés.

On ne peut donc pas espérer atteindre le régime de croisière en termes de débit dès le début de la mise en production. De surcroît on ne doit pas essayer d&#39;envoyer les premiers messages avec un tel débit, car cela conduirait les FAI à bloquer d&#39;autant plus sévèrement les adresses IP d&#39;envoi et à compromettre gravement la poursuite du démarrage.

## Principes principaux

Vous trouverez ci-dessous la liste des principes essentiels à respecter lors du démarrage d’une nouvelle plateforme.

* Configurez un sous-domaine dédié qui est spécifique aux campagnes par e-mail envoyées depuis Adobe.

* Si vous disposez de ces informations, **importez des adresses non valides dans la table des quarantaines**.
Le démarrage d’une plateforme s’accompagne souvent de l’utilisation d’une liste d’adresses inconnues jusqu’ici, qui n’est pas entièrement qualifiée. L’envoi de messages à des adresses non valides ou à des adresses servant de leurres contribuera à affaiblir la réputation de la plateforme.

   * Si vous disposez d&#39;une liste d&#39;adresses non valides, il est dans votre intérêt de l&#39;importer dans la table des quarantaines avant de réaliser les premiers envois. La table des quarantaines est disponible via les menus **[!UICONTROL Administration > Campaign Management > Gestion des échecs > Echecs et adresses]** (Campaign Classic) et **[!UICONTROL Administration > Canaux > Quarantaines > Adresses]** (Campaign Standard).

   * Si on souhaite malgré tout requalifier les adresses invalides, il est nettement préférable de le faire une fois la réputation de la plateforme établie et par petites parties afin de &quot;diluer&quot; dans le temps l&#39;usage des mauvaises adresses.

* **Limitez le débit** en limitant le nombre de mtachilds. Pour plus d’informations sur la modification de ce paramètre technique, contactez votre administrateur Adobe Campaign.

* **Augmentez progressivement les volumes envoyés** pour éviter que les emails soient marqués comme spam. Ne ciblez pas l’ensemble de la base de données dès le début, mais ajoutez plutôt une partie supplémentaire de la liste à chaque envoi. Vous devriez ainsi pouvoir augmenter le volume à chaque étape tout en réduisant le taux global d’adresses non valides. Pour assurer un développement fluide de la phase de démarrage, vous pouvez utiliser des vagues.

* **Effectuez régulièrement des envois**. Dans une certaine mesure, il est préférable de réaliser de petits envois fréquents plutôt que des envois volumineux et sporadiques.
* **Accordez de l’attention aux rapports de diffusion**. Un indicateur d’erreur élevé peut signifier qu’un paramètre technique est mal configuré.

## Ressources supplémentaires

Pour plus d’informations sur les principes répertoriés ci-dessus et leur mise en oeuvre avec Adobe Campaign, consultez les sections suivantes :

* [Améliorer la réputation de vos emails grâce au réchauffement des adresses IP](../../help/additional-resources/increase-reputation-with-ip-warming.md)
* [En savoir plus sur les pièges à spam](../../help/additional-resources/all-about-spam-traps.md)

**Adobe Campaign Classic**

* [Optimisez votre diffusion par le biais de quarantaines](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html?lang=fr#optimizing-your-delivery-through-quarantines)
* [Identifier les adresses en quarantaine pour l&#39;ensemble de la plateforme](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html?lang=fr#identifying-quarantined-addresses-for-the-entire-platform)
* [Envoi en plusieurs vagues](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-sending-the-delivery.html?lang=fr#sending-using-multiple-waves)
* [Surveillance des diffusions](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/about-delivery-monitoring.html?lang=fr#sending-messages)

**Adobe Campaign Standard**

* [Optimisez votre diffusion par le biais de quarantaines](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=fr#optimizing-your-delivery-through-quarantines)
* [Identifier les adresses en quarantaine pour l&#39;ensemble de la plateforme](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=fr)
* [Surveillance d’une diffusion](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html?lang=fr-FR)
