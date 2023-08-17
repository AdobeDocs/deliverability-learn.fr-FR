---
title: Bonnes pratiques en matière de réengagement
description: Découvrez comment améliorer la délivrabilité grâce à des stratégies de réengagement.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 30118706-d4c0-4bd8-8c9b-50c26b8374ef
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 26%

---

# Bonnes pratiques en matière de réengagement {#re-engagement}

Lors de la mise en oeuvre de la délivrabilité, certaines des bonnes pratiques consistent à essayer de maintenir une base d’abonnés saine et d’améliorer la délivrabilité par le biais de stratégies de réengagement (ou de retour).

* Le maintien d’une base d&#39;abonnés solide est l’un des aspects essentiels pour assurer une diffusion satisfaisante et cohérente. Nombre de problèmes de délivrabilité résultent de pratiques et d’opérations de maintenance des données inefficaces.
* Parmi les difficultés les plus courantes, les spécialistes marketing sont confrontés aujourd’hui à l’inactivité des abonnés (aussi appelée engagement faible ou non-engagement).Ce problème peut avoir une incidence négative sur la diffusion des emails et le ROI (retour sur investissement).

>[!NOTE]
>
>Pour plus d’informations sur les stratégies de campagne de réengagement et les services de délivrabilité d’Adobe, contactez votre conseiller en délivrabilité ou votre représentant Adobe.

## Comment les FAI considèrent-ils une activité de non-engagement ? {#how-do-isps-view-non-engagement-activity-}

Pendant des années, les FAI ont utilisé les mesures de retour d’engagement de leurs utilisateurs pour décider où placer les messages, ou s’ils doivent les diffuser ou non. Utilisateur [engagement](/help/engagement.md) se compose de commentaires positifs et négatifs et les FAI surveillent les deux de manière constante. N&#39;avoir aucun engagement est peut-être l&#39;un des principaux facteurs de l&#39;engagement négatif. Du point de vue de la délivrabilité, l’envoi régulier de campagnes aux utilisateurs qui ne montrent aucun engagement peut également réduire la réputation globale de vos adresses IP et domaines.

Les FAI tels que Gmail, Microsoft® et OATH considèrent le non-engagement comme un email indésirable et commencent à rediriger les messages vers le dossier spam. En outre, ces abonnés peuvent ne plus être propriétaires du compte de messagerie, qui peut être utilisé comme piège à spam &quot;recyclé&quot;. Cela signifie que l&#39;adresse n&#39;a pas été valide pendant un certain temps et que tous les messages sont rejetés. Si votre système de gestion des abonnés ne supprime pas les adresses &quot;hard bounce&quot;, il est probable qu’il envoie vers des pièges à spam qui peuvent entraîner des problèmes de diffusion importants.

## Comment aborder l’inactivité ? {#how-should-you-approach-inactivity-}

Les clients qui utilisent la plateforme Adobe peuvent afficher l’inactivité au sein de leur instance en examinant les données d’ouverture et de clic en fonction du segment. Comme le non-engagement peut entraver la diffusion, la première idée peut être de supprimer des abonnés de la base de données. Cependant, cette option peut s’avérer parfois erronée. Par conséquent, une stratégie de réengagement (également appelée &quot;contre-retour&quot;) est la meilleure recommandation pour conserver les abonnés intéressés par la réception du courrier et éliminer progressivement ceux qui ne montrent plus d’activité.

## Les campagnes de réengagement fonctionnent-elles vraiment ? {#do-re-engagement-campaigns-really-work-}

Selon une étude Return Path, les campagnes de réengagement ont un taux d&#39;ouverture de 12 % par rapport à une moyenne de 14 % pour les campagnes normales. Bien que seulement 24 % des abonnés aient lu la campagne de réengagement, environ 45 % d&#39;entre eux ont lu les messages suivants.

![](../../help/assets/deliverability_implementation_1.png)

## Comment créer une campagne de réengagement ? {#how-do-you-create-a-re-engagement-campaign-}

### Phase 1 {#phase-1}

* La première étape consiste à identifier les abonnés qui ont peu ou pas d’activité d’ouverture ou de clic et, en conséquence, à segmenter ce groupe selon une période définie. La règle de base consiste à passer en revue les abonnés qui n’ont ni ouvert ni cliqué un email au cours des 90 derniers jours. Cependant, cela varie en fonction de la nature de l’entreprise (par exemple, l’envoi saisonnier).
* Un autre point dont vous devez tenir compte lors de la définition des délais est que les FAI et les sociétés de liste bloquée considèrent que l&#39;engagement se situe entre 1,5 et 1,8 an. En outre, les activités comportementales telles que les achats et l’activité du site web, ou d’autres points de contact, tels que les préférences pendant la phase d’inscription ou le premier point de contact.

### Phase 2 {#phase-2}

* Une fois qu’un segment est défini, l’étape suivante consiste à créer une campagne de réengagement qui s’adresse à l’abonné en fonction des mesures qui ont été identifiées. La création d’un objet permet d’augmenter l’intérêt de l’abonné. Selon une étude Return Path, les objets et le contenu qui indiquent &quot;We miss you&quot; génèrent des taux de réponse plus élevés que &quot;We want you back&quot; (Nous voulons que vous soyez revenu).
* Une incitation peut également être proposée pour réengager l&#39;email. Lorsque vous envisagez des offres avec des remises, il est préférable d’utiliser des montants en euros plutôt que des pourcentages. Return Path suggère également de le faire, car cela entraîne des taux de réponse plus élevés. Enfin, l’exécution de tests de partage A/B pour examiner les taux de réponse et de réussite est également une option utile.

### Phase 3 {#phase-3}

L&#39;étape suivante consiste à déterminer la fréquence de la campagne de réengagement. Contrairement aux messages de reconfirmation, les campagnes de réengagement ont pour but de reconquérir les abonnés grâce à des emails envoyés au fil du temps. L&#39;exemple suivant illustre la fréquence.

![](../../help/assets/deliverability_implementation_2.png)

Les abonnés qui interagissent pendant la campagne en suivant l&#39;activité d&#39;ouverture ou de clic sont ajoutés à la liste des abonnés engagés.

### Phase 4 {#phase-4}

* La phase suivante consiste à identifier les abonnés qui ne montrent aucune activité et à réduire progressivement l’envoi d’emails à ces derniers sur une période donnée. S’il n’y a pas d’activité au cours de l’année écoulée, il est recommandé de suspendre l’abonnement aux emails des abonnés. Bien qu’ils n’aient manifesté aucun intérêt pour le contenu de l’email, il est toujours possible de leur demander de réactiver leur abonnement en envoyant une campagne de reconfirmation unique.
* Les campagnes de confirmation sont un bon moyen de demander aux abonnés inactifs depuis longtemps s&#39;ils souhaitent rester sur la liste d&#39;abonnements. Lors de la création de l&#39;opération, il est préférable d&#39;ajouter un lien &quot;cliquez ici&quot; afin qu&#39;il puisse confirmer l&#39;action et vérifier son adresse. Ainsi, l’action peut être enregistrée dans la base de données. Voici un exemple d&#39;email de reconfirmation :

  ![](../../help/assets/deliverability_implementation_3.png)

  Une fois que l&#39;abonné a effectué une action, une landing page avec la confirmation de sa réinscription peut être proposée. Voici un exemple de landing page :

  ![](../../help/assets/deliverability_implementation_4.png)

## Ressources spécifiques au produit

**Adobe Campaign**

* [Logs de tracking dans Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/delivery-dashboard.html#tracking-logs)
* [Logs de tracking dans Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/sending-and-tracking-messages/tracking-messages.html#tracking-logs)

**Adobe de la gestion des Parcours client**

* [Suivi des messages](https://experienceleague.adobe.com/docs/journey-optimizer/using/reporting/message-tracking.html?lang=fr)
