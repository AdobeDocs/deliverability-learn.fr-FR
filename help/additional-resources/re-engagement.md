---
title: Meilleures pratiques de réengagement
description: Apprenez à améliorer la délivrabilité grâce à des stratégies de réengagement.
feature: Additional resources
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 96ed84da391faaabd3001ddd6a411ddc1f46b033
workflow-type: tm+mt
source-wordcount: '928'
ht-degree: 36%

---


# Meilleures pratiques de réengagement {#re-engagement}

Lors de la mise en oeuvre de la délivrabilité, certaines des meilleures pratiques consistent à essayer de maintenir une base d&#39;abonnés saine et d&#39;améliorer la délivrabilité par le biais de stratégies de réengagement (ou de reprise).

* Le maintien d’une base d&#39;abonnés solide est l’un des aspects essentiels pour assurer une diffusion satisfaisante et cohérente. Nombre de problèmes de délivrabilité résultent de pratiques et d’opérations de maintenance des données inefficaces.
* Parmi les difficultés les plus courantes, les marketeurs sont confrontés aujourd’hui à l’inactivité des abonnés (aussi appelée engagement faible ou non-engagement). Ce problème peut avoir une incidence négative sur la diffusion des emails et le ROI (retour sur investissement).

>[!NOTE]
>
>Pour plus d’informations sur les stratégies de campagne de réengagement et les services de délivrabilité d’Adobe, contactez votre conseiller en délivrabilité ou votre représentant Adobe.

## Comment les FAI considèrent-ils une activité de non-engagement ?{#how-do-isps-view-non-engagement-activity-}

Depuis des années, les FAI utilisent les mesures de retour d&#39;intérêt de leurs utilisateurs pour décider où placer les messages ou s&#39;ils doivent les diffuser. L&#39;engagement [des utilisateurs](/help/engagement.md) consiste à la fois en commentaires positifs et négatifs et les FAI surveillent les deux de manière constante. N&#39;avoir aucun engagement est peut-être l&#39;un des principaux contributeurs de l&#39;engagement négatif. Du point de vue de la délivrabilité, l’envoi régulier de campagnes aux utilisateurs qui ne montrent aucun engagement peut également réduire la réputation globale de votre adresse IP et de vos domaines.

Les FAI tels que Gmail, Microsoft et OATH vue ne s’engagent pas en tant qu’e-mail indésirable et début redirigeant les messages vers le dossier de messages indésirables. En outre, ces abonnés peuvent ne plus être propriétaires du compte de messagerie, et cela peut être utilisé comme piège antispam &quot;recyclé&quot;. Cela signifie que l&#39;adresse n&#39;a pas été valide pendant un certain temps et que tous les messages sont rejetés. Si votre système de gestion des abonnés ne supprime pas les adresses &quot;reportées&quot;, il est très probable que l&#39;envoi par courrier postal à des pièges à messages indésirables peut entraîner des problèmes de diffusion importants.

## Comment aborder l’inactivité ?{#how-should-you-approach-inactivity-}

Les clients qui utilisent la plate-forme d’Adobe peuvent vue l’inactivité au sein de leur instance en examinant les données d’ouverture et de clic en fonction du segment. Comme le non-engagement peut entraver la diffusion, la première idée peut être de supprimer les abonnés de la base de données. Cependant, cette option peut parfois s&#39;avérer erronée. Par conséquent, une stratégie de réengagement (également connue sous le nom de stratégie de retour sur investissement) est la meilleure recommandation pour retenir les abonnés intéressés à recevoir du courrier et pour éliminer progressivement ceux qui ne font plus activité.

## Les campagnes de réengagement fonctionnent-elles vraiment ?{#do-re-engagement-campaigns-really-work-}

Selon une étude Return Path, les campagnes de réengagement ont un taux d&#39;ouverture de 12 % par rapport à une moyenne de 14 % pour les campagnes normales. Bien que seulement 24 % des abonnés aient lu la campagne de réengagement, environ 45 % d&#39;entre eux ont lu les messages suivants.

![](../../help/assets/deliverability_implementation_1.png)

## Comment créer une campagne de réengagement ?{#how-do-you-create-a-re-engagement-campaign-}

### Phase 1 {#phase-1}

* La première étape consiste à identifier les abonnés qui ont très peu ou pas d’activité d’ouverture ou de clic et, par conséquent, à segmenter ce groupe en fonction d’une période définie. La règle générale consiste à consulter les abonnés qui n’ont pas ouvert ou cliqué sur un courriel au cours des 90 derniers jours. Cependant, cette situation varie en fonction de la nature de l’entreprise (par exemple, l’envoi saisonnier).
* Un autre point dont vous devez tenir compte lors de la définition des délais est que les FAI et les sociétés de liste bloquée considèrent que l&#39;engagement se situe entre 1,5 et 1,8 an. En outre, les activités comportementales telles que les achats et l’activité du site Web, ou d’autres points de contact, tels que les préférences pendant la phase d’inscription ou le premier point de contact.

### Phase 2 {#phase-2}

* Une fois qu’un segment est défini, l’étape suivante consiste à créer une campagne de réengagement qui s’adresse à l’abonné en fonction des mesures qui ont été identifiées. La création d’une ligne d’objet aide à accroître l’intérêt de l’abonné. Selon une étude sur le Chemin de retour, les sujets et le contenu qui disent &quot;Vous nous manquez&quot; génèrent des taux de réponse plus élevés que &quot;Nous voulons que vous soyez revenu&quot;.
* Un incitatif peut également être proposé pour réengager le courrier électronique. Lorsque vous considérez des offres avec des remises, il est préférable d&#39;utiliser des montants en dollars par rapport aux pourcentages. Le chemin de retour suggère également de le faire car il entraîne des taux de réponse plus élevés. Enfin, l’exécution de tests de fractionnement A/B pour examiner les taux de réponse et de réussite est également une option utile.

### Phase 3 {#phase-3}

L&#39;étape suivante consiste à déterminer la fréquence de la campagne de réengagement. Contrairement aux messages de reconfirmation, les campagnes de réengagement ont pour but de reconquérir les abonnés grâce à des emails envoyés au fil du temps. L&#39;exemple suivant illustre la fréquence.

![](../../help/assets/deliverability_implementation_2.png)

Les abonnés qui interagissent pendant la campagne en suivant l&#39;activité d&#39;ouverture ou de clic sont ajoutés à la liste des abonnés engagés.

### Phase 4 {#phase-4}

* La prochaine étape consiste à identifier les abonnés qui ne montrent pas d&#39;activité en permanence et à réduire progressivement l&#39;envoi de courriels vers eux sur une période donnée. S&#39;il n&#39;y a pas d&#39;activité au cours de l&#39;année écoulée, il est bon de mettre l&#39;abonnement de courriel des abonnés en attente. Bien qu’ils n’aient montré aucun intérêt pour le contenu du courrier électronique, il existe toujours une dernière chance de les faire réactiver en envoyant une campagne de confirmation unique à leur abonnement.
* Les campagnes de reconfirmation sont un bon moyen de demander aux abonnés inactifs depuis une longue période s&#39;ils souhaitent être conservés dans la liste d&#39;inscription. Lors de la création de la campagne, il est préférable d&#39;ajouter un lien « cliquez ici » afin que les abonnés puissent confirmer l&#39;action et vérifier leur adresse. De cette façon, l&#39;action peut être enregistrée dans la base de données. Voici un exemple d&#39;email de reconfirmation :

   ![](../../help/assets/deliverability_implementation_3.png)

   Une fois que l&#39;abonné a exécuté une action, une landing page avec la confirmation de la réinscription peut être proposée. Voici un exemple de landing page :

   ![](../../help/assets/deliverability_implementation_4.png)

## Ressources spécifiques au produit

**Adobe Campaign**

* [Logs de tracking en Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/monitoring-deliveries/delivery-dashboard.html#tracking-logs)
* [Logs de tracking en Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/testing-and-sending/sending-and-tracking-messages/tracking-messages.html#tracking-logs)

**Gestion des Parcours clients Adobe**

* [Tracking des messages](https://experienceleague.adobe.com/docs/customer-journey-management/using/reporting/message-tracking.html)