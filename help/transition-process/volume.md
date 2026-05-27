---
title: Volume - Conseils pour une transition en douceur
description: Le volume d'e-mails que vous envoyez est essentiel pour établir une réputation positive. Découvrez ce que vous pouvez faire pour effectuer une transition en douceur.
topics: Deliverability
jira: KT-7055
thumbnail: kt7055.jpg
doc-type: article
activity: understand
role: Admin,User
level: Beginner
team: ACS
exl-id: 1bc56061-0c64-4033-b49c-66618916bca6
TQID: https://experienceleague.adobe.com/piIfp9yQkAa1F1bkO9zM7PcOConZhTrwARo4Y8wtMsQ
product_v2:
  - id: b27e5950-9033-45ac-9f86-eb22e567f615
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: e64968b2-4ee5-47f9-8cae-0588f184b9eb
  - id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 600
ht-degree: 4%

---

# Volume

Le volume d&#39;e-mails que vous envoyez est essentiel pour établir une réputation positive. Mettez-vous à la place d&#39;un FAI : si vous commencez à voir une tonne de trafic provenant d&#39;une personne que vous ne connaissez pas, ce serait alarmant. L’envoi immédiat d’un grand volume d’e-mails est risqué et entraîne à coup sûr des problèmes de réputation souvent difficiles à résoudre. Il peut s’avérer frustrant, long et coûteux de se sortir d’une mauvaise réputation et de générer du trafic et de bloquer des problèmes résultant d’un envoi trop précoce.

Les seuils de volume varient selon le FAI et peuvent également varier en fonction de vos mesures d’engagement moyennes. Certains expéditeurs nécessitent une rampe de volume très basse et lente, tandis que d&#39;autres peuvent permettre une rampe de volume plus raide. Nous vous recommandons de travailler avec un expert, tel qu’un consultant en délivrabilité d’Adobe, pour développer un plan de volume personnalisé.

Voici une liste d’astuces et de conseils pour une transition en douceur :

* **Autorisation** est la base de tout programme de messagerie réussi.
* **Faible et lent** — Commencez avec de faibles volumes d&#39;envoi, puis augmentez au fur et à mesure que vous établissez la réputation de votre expéditeur.
* Une **stratégie de publipostage tandem** vous permet d’augmenter le volume de Campaign tout en terminant avec votre fournisseur de service de messagerie actuel, sans perturber votre calendrier de messagerie.
* **L’engagement est important** — commencez par les abonnés qui ouvrent et cliquent régulièrement sur vos e-mails.
* **Suivez le plan** — nos recommandations ont aidé des centaines de clients de Campaign à développer leurs programmes de messagerie.
* **Surveiller votre compte de messagerie de réponse**. Utiliser noreply@xyz.com ou ne pas répondre est une mauvaise expérience pour votre client.
* Les adresses inactives peuvent avoir un impact négatif sur la délivrabilité. **Réactiver et réautoriser sur votre plateforme actuelle** et non sur vos nouvelles adresses IP.
* **Domaines** — utilisez un domaine d&#39;envoi qui est un sous-domaine du domaine réel de votre entreprise
   * Par exemple, si le domaine de votre société est xyz.com, email.xyz.com offre plus de crédibilité aux FAI que xyzemail.com
* **Transparence** — les informations d&#39;enregistrement de votre domaine de messagerie doivent être disponibles publiquement et ne doivent pas être privées.

Dans de nombreuses circonstances, le courrier transactionnel ne suit pas l’approche traditionnelle de réchauffement promotionnel. Il est évidemment difficile de contrôler le volume des e-mails transactionnels en raison de leur nature, car cela nécessite généralement une interaction de l’utilisateur pour déclencher le contact avec l’e-mail. Dans certains cas, le courrier transactionnel peut simplement être transféré sans plan formel. Dans d’autres cas, il peut être préférable de transitionner chaque type de message au fil du temps pour augmenter lentement le volume. Par exemple, vous pouvez effectuer la transition comme suit :

1. Confirmations d’achat - engagement élevé en général
2. Abandon de panier (engagement moyen à élevé, en général)
3. Emails de bienvenue : engagement élevé, mais peut contenir des adresses incorrectes selon les méthodes de collecte de votre liste
4. E-mails de reconquête : engagement réduit en général

## Ressources spécifiques au produit

**Campagne**

* En savoir plus sur la gestion de la délivrabilité lors du démarrage d&#39;une nouvelle plateforme avec Adobe Campaign dans [cette section](/help/additional-resources/ac-starting-new-platform.md).
* Découvrez comment envoyer en plusieurs vagues avec Adobe Campaign Classic dans [cette section](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/key-steps-when-creating-a-delivery/steps-sending-the-delivery.html?lang=fr#sending-using-multiple-waves).
* Découvrez comment déléguer entièrement un sous-domaine à Adobe Campaign Classic ou à Standard dans [cette section](/help/additional-resources/ac-domain-name-setup.md).
* [Panneau de Contrôle : délégation complète de sous-domaine (tutoriel)](https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html?lang=fr) - *Découvrez comment déléguer entièrement un sous-domaine à Adobe Campaign Classic.*
* [Panneau de Contrôle : délégation complète de sous-domaine (tutoriel)](https://experienceleague.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html?lang=fr) - *Découvrez comment déléguer entièrement un sous-domaine à Adobe Campaign Standard.*

## Ressources supplémentaires

* Pour en savoir plus sur l’amélioration de la réputation des e-mails avec le réchauffement des adresses IP, consultez [cette section](/help/additional-resources/increase-reputation-with-ip-warming.md).
