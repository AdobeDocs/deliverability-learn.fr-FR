---
title: Démarrage d’une nouvelle plateforme
description: En savoir plus sur la gestion de la délivrabilité lors du démarrage d'une nouvelle plateforme avec Adobe Campaign.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 6c9ade01-3052-4311-af80-888294820024
TQID: https://experienceleague.adobe.com/cQa5nOTSJwxDGX-QkXGez5dpm5N-8I7QZ-LsEW0FRLo
product_v2: id: b27e5950-9033-45ac-9f86-eb22e567f615id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: c5474392-5419-4296-9e41-f6f4ce4f6e9bid: c5f60233-d5ea-4453-a799-0ad258b4d399id: d1d0a9cd-295d-4976-8c39-ddae266f240eid: e2290edd-b061-4880-9d79-dee306cf5aa9id: f71e690b-4480-4b67-9ef5-88f42f9cdfdbid: fdbb8fc9-ffa3-4b86-88fe-aa4c5a3e1bc6
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87cid: eddd9b14-83bd-4ff4-9072-54a4a484abb7
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 680
ht-degree: 49%

---

# Démarrage d’une nouvelle plateforme {#starting-new-platform}

Le maintien de la réputation de votre domaine et de votre adresse IP est essentiel lors de la configuration d’une nouvelle plateforme à utiliser avec Adobe Campaign.

## Une étape sensible

Vous devez être très prudent lorsque vous commencez à envoyer des e-mails sur une nouvelle plateforme, car la plateforme n&#39;a aucun historique d&#39;utilisation, et aucune réputation lorsque les adresses IP d&#39;envoi n&#39;ont jamais été utilisées à cette fin.

Or rien n&#39;est plus suspect pour un FAI qu&#39;une adresse IP qui n&#39;a jamais envoyé d&#39;emails et qui commence subitement à envoyer des messages en masse. En effet, les spammeurs utilisent généralement des adresses IP &#39;&#39;inconnues&#39;&#39; (qui n&#39;ont jamais été placées sur liste bloquée) pour envoyer un maximum de messages pendant le laps de temps où ils n&#39;ont pas encore été détectés.

On ne peut donc pas espérer atteindre le régime de croisière en termes de débit dès le début de la mise en production. De surcroît on ne doit pas essayer d&#39;envoyer les premiers messages avec un tel débit, car cela conduirait les FAI à bloquer d&#39;autant plus sévèrement les adresses IP d&#39;envoi et à compromettre gravement la poursuite du démarrage.

## Principes fondamentaux

Vous trouverez ci-dessous la liste des principaux principes à suivre lors du démarrage d’une nouvelle plateforme.

* Configurez un sous-domaine dédié qui est spécifique aux campagnes par e-mail envoyées à partir d’Adobe.

* Si vous disposez de ces informations, **importez des adresses non valides dans la table des quarantaines**.
Le démarrage d&#39;une plateforme s&#39;effectue souvent lors de la première utilisation d&#39;une liste d&#39;adresses qui n&#39;est pas entièrement qualifiée. Si vous envoyez des messages à des adresses non valides ou à des adresses servant de leurres, cela contribuera à affaiblir la réputation de la plateforme.

   * Si vous disposez d’une liste d’adresses non valides, il est dans votre intérêt de l’importer dans la table de quarantaine avant de l’envoyer pour la première fois. La table des quarantaines est accessible à partir des menus **[!UICONTROL Administration > Gestion de campagnes > Gestion des échecs > Échecs et adresses]** (Campaign Classic) et **[!UICONTROL Administration > Canaux > Quarantaines > Adresses]** (Campaign Standard).

   * Si on souhaite malgré tout requalifier les adresses invalides, il est nettement préférable de le faire une fois la réputation de la plateforme établie et par petites parties afin de &quot;diluer&quot; dans le temps l&#39;usage des mauvaises adresses.

* **Limitez le débit** en limitant le nombre de mtachilds. Pour plus d’informations sur la modification de ce paramètre technique, contactez votre administrateur Adobe Campaign.

* **Augmentez progressivement les volumes envoyés** pour éviter que les emails soient marqués comme spam. Ne ciblez pas l’ensemble de la base de données dès le début, mais ajoutez plutôt une partie supplémentaire de la liste à chaque envoi. Vous devriez ainsi pouvoir augmenter le volume à chaque étape tout en réduisant le taux global d’adresses non valides. Pour assurer le bon développement de la phase de démarrage, vous pouvez utiliser des vagues.

* **Effectuez régulièrement des envois**. Dans une certaine mesure, il est préférable d&#39;envoyer régulièrement de petits plans plutôt que de grandes campagnes sporadiques.
* **Accordez de l’attention aux rapports de diffusion**. Des indicateurs d’erreur élevés peuvent signifier qu’un paramètre technique est mal configuré.

## Ressources supplémentaires

Pour plus d’informations sur les principes répertoriés ci-dessus et leur mise en œuvre avec Adobe Campaign, consultez les sections suivantes :

* [Améliorer la réputation de vos emails grâce au réchauffement des adresses IP](../../help/additional-resources/increase-reputation-with-ip-warming.md)
* [En savoir plus sur les pièges à spam](../../help/additional-resources/all-about-spam-traps.md)

**Adobe Campaign Classic**

* [Optimisation de votre diffusion par le biais de quarantaines](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html#optimizing-your-delivery-through-quarantines)
* [Identifier les adresses en quarantaine pour l&#39;ensemble de la plateforme](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/understanding-quarantine-management.html#identifying-quarantined-addresses-for-the-entire-platform)
* [Envoi en plusieurs vagues](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-sending-the-delivery.html?lang=fr#sending-using-multiple-waves)
* [Surveillance des diffusions](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/about-delivery-monitoring.html?lang=fr#sending-messages)

**Adobe Campaign Standard**

* [Optimisation de votre diffusion par le biais de quarantaines](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html#optimizing-your-delivery-through-quarantines)
* [Identifier les adresses en quarantaine pour l&#39;ensemble de la plateforme](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/understanding-quarantine-management.html?lang=fr)
* [Contrôler une diffusion](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/monitoring-messages/monitoring-a-delivery.html?lang=fr-FR)
