---
title: Bonnes pratiques en matière de réengagement
description: Découvrez comment améliorer la délivrabilité grâce à des stratégies de réengagement.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 30118706-d4c0-4bd8-8c9b-50c26b8374ef
TQID: https://experienceleague.adobe.com/XbAU6Y0r4Ed8W7t71MMNV02jdp2-og04-v-n2lT5m-4
product_v2: id: b27e5950-9033-45ac-9f86-eb22e567f615id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: a075b2c1-7748-4328-b7f6-343aa314616aid: c5f60233-d5ea-4453-a799-0ad258b4d399id: e2290edd-b061-4880-9d79-dee306cf5aa9id: ea90ebee-5c84-42d9-8b21-006bdabc95a3id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: aa2f3246-cb95-4b30-8899-fdf7d73550ccid: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 973
ht-degree: 15%

---

# Bonnes pratiques en matière de réengagement {#re-engagement}

Lors de la mise en œuvre de la délivrabilité, certaines des bonnes pratiques consistent à essayer de maintenir une base d&#39;abonnés saine et d&#39;améliorer la délivrabilité par le biais de stratégies de réengagement (ou de reconquête).

* Le maintien d’une base d&#39;abonnés solide est l’un des aspects essentiels pour assurer une diffusion satisfaisante et cohérente. Nombre de problèmes de délivrabilité résultent de pratiques et d’opérations de maintenance des données inefficaces.
* Parmi les difficultés les plus courantes, les spécialistes marketing sont confrontés aujourd’hui à l’inactivité des profils abonnés (aussi appelée engagement faible ou non-engagement). Ce problème peut avoir une incidence négative sur la diffusion des e-mails et le ROI (retour sur investissement).

>[!NOTE]
>
>Pour plus d’informations sur les stratégies de campagne de réengagement et les services de délivrabilité d’Adobe, contactez votre conseiller en délivrabilité ou votre représentant Adobe.

## Comment les FAI perçoivent-ils les activités hors engagement ? {#how-do-isps-view-non-engagement-activity-}

Pendant des années, les FAI ont utilisé les mesures de retour d&#39;engagement de leurs utilisateurs pour décider où placer les messages ou s&#39;ils doivent les diffuser. L’[engagement](/help/engagement.md) des utilisateurs et utilisatrices consiste en des retours positifs et négatifs, que les FAI surveillent en permanence. L&#39;absence d&#39;engagement est peut-être l&#39;un des principaux facteurs d&#39;engagement négatif. Du point de vue de la délivrabilité, l’envoi systématique de campagnes à des utilisateurs qui ne montrent aucun engagement peut également nuire à la réputation globale de votre adresse IP et de vos domaines.

Les FAI tels que Gmail® Microsoft et OATH considèrent le non-engagement comme un e-mail indésirable et commencent à rediriger les messages vers le dossier des courriers indésirables. En outre, ces abonnés peuvent ne plus être propriétaires du compte de messagerie, qui peut être utilisé comme un piège à spam « recyclé ». Cela signifie que l’adresse n’a pas été valide pendant un certain temps et que tous les messages sont rejetés. Si votre système de gestion des abonnés ne supprime pas les adresses hard bounce, il s&#39;agit probablement d&#39;un publipostage vers des pièges à spam qui peuvent entraîner des problèmes de diffusion importants.

## Comment aborder l&#39;inactivité ? {#how-should-you-approach-inactivity-}

Les clients qui utilisent la plateforme Adobe peuvent afficher l’inactivité dans leur instance en examinant les données d’ouverture et de clic en fonction du segment. Dans la mesure où le non-engagement peut entraver la diffusion, la première idée peut être de supprimer les abonnés de la base de données. Cependant, cela peut parfois s&#39;avérer être une mauvaise option. Par conséquent, une stratégie de réengagement (également appelée reconquête) est la meilleure recommandation pour fidéliser les abonnés qui souhaitent recevoir des emails et éliminer progressivement ceux qui ne montrent plus d’activité.

## Les campagnes de réengagement fonctionnent-elles vraiment ? {#do-re-engagement-campaigns-really-work-}

Selon une étude Return Path, les campagnes de réengagement ont obtenu un taux d’ouverture de 12 %, contre une moyenne de 14 % pour les campagnes normales. Bien que seulement 24 % des abonnés aient lu la campagne de réengagement, environ 45 % d&#39;entre eux ont lu les messages qui ont suivi.

![](../../help/assets/deliverability_implementation_1.png)

## Comment créer une campagne de réengagement ? {#how-do-you-create-a-re-engagement-campaign-}

### Phase 1 {#phase-1}

* La première étape consiste à identifier les abonnés qui n’ont que peu ou pas d’activité d’ouverture ou de clic, et à segmenter ce groupe en fonction d’une période définie. La règle de base consiste à examiner les abonnés qui n’ont pas ouvert ou cliqué sur un e-mail au cours des 90 derniers jours. Toutefois, cela varie selon la nature de l&#39;entreprise (par exemple, les envois saisonniers).
* Un autre point dont vous devez tenir compte lors de la définition des délais est que les FAI et les sociétés de liste bloquée considèrent que l&#39;engagement se situe entre 1,5 et 1,8 an. En outre, les activités comportementales telles que les achats et l’activité du site web, ou d’autres points de contact, tels que les préférences pendant la phase d’inscription ou le premier point de contact.

### Phase 2 {#phase-2}

* Une fois qu’un segment est défini, l’étape suivante consiste à créer une campagne de réengagement qui s’adresse à l’abonné en fonction des mesures qui ont été identifiées. La création d’une ligne d’objet contribue à accroître l’intérêt des abonnés. Selon une étude sur le chemin de retour, les objets et le contenu qui disent « Vous nous manquez » génèrent des taux de réponse plus élevés que « Nous voulons vous récupérer ».
* Une incitation peut également être proposée pour le réengagement avec l’e-mail. Lorsque vous envisagez des offres avec des remises, il est préférable d’utiliser des montants en dollars plutôt qu’en pourcentages. Le chemin de retour suggère également de procéder ainsi, car il entraîne des taux de réponse plus élevés. Enfin, il est également utile d’effectuer des tests de division A/B pour examiner les taux de réponse et de succès.

### Phase 3 {#phase-3}

L’étape suivante consiste à déterminer la fréquence de la campagne de réengagement. Contrairement aux messages de reconfirmation, les campagnes de réengagement sont destinées à reconquérir l’abonné avec une série d’e-mails au fil du temps. L’exemple suivant fournit un exemple de la fréquence .

![](../../help/assets/deliverability_implementation_2.png)

Les abonnés qui interagissent pendant la campagne en suivant l&#39;activité d&#39;ouverture ou de clic sont ajoutés à la liste des abonnés engagés.

### Phase 4 {#phase-4}

* La phase suivante consiste à identifier les abonnés qui ne montrent en permanence aucune activité et à réduire progressivement l’envoi d’e-mails à eux sur une période de temps. S’il n’y a aucune activité au cours de l’année écoulée, il est préférable de mettre l’abonnement par e-mail des abonnés en attente. Bien qu’ils n’aient montré aucun intérêt pour le contenu de l’e-mail, il existe toujours une dernière chance pour qu’ils réactivent leur abonnement en envoyant une campagne de reconfirmation unique.
* Les campagnes de reconfirmation sont un bon moyen de demander aux abonnés qui sont inactifs depuis longtemps s&#39;ils souhaitent rester sur la liste d&#39;abonnements. Lors de la création de la campagne, il est préférable d’ajouter un lien « cliquez ici » afin qu’ils puissent confirmer l’action et vérifier leur adresse. Ainsi, l’action peut être enregistrée dans la base de données. Voici un exemple d’e-mail de reconfirmation :

  ![](../../help/assets/deliverability_implementation_3.png)

  Une fois que l&#39;abonné a effectué une action, une landing page avec la confirmation de sa réinscription peut être proposée. Voici un exemple de page de destination :

  ![](../../help/assets/deliverability_implementation_4.png)

## Ressources spécifiques au produit

**Adobe Campaign**

* [Logs de tracking dans Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/delivery-dashboard.html#tracking-logs)
* [Logs de tracking dans Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/sending-and-tracking-messages/tracking-messages.html#tracking-logs)

**Gestion du Parcours client Adobe**

* [Tracking des messages](https://experienceleague.adobe.com/docs/journey-optimizer/using/reporting/message-tracking.html?lang=fr)
