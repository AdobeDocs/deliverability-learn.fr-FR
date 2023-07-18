---
title: Résolution des problèmes de délivrabilité
description: Découvrez comment identifier et résoudre les problèmes de délivrabilité.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 4cc85124-e7e4-4cd5-99a9-23d2d8cf08fe
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 91%

---

# Résolution des problèmes de délivrabilité {#troubleshooting}

Vous trouverez ci-dessous quelques bonnes pratiques pour mieux identifier et résoudre les problèmes de délivrabilité.

## Identifier un problème de délivrabilité {#identify-deliverability-issue}

Pour identifier un problème possible, les éléments répertoriés sur [cette page](/help/ongoing-monitoring.md) peut attirer votre attention.

<!--
Mailing or campaign metrics: unsubscribe, abuse complaint and/or bounce rates are higher than usual.
Subscriber activity: opens, clicks and/or transactions are lower than usual.
Seed accounts show filtered or non-delivered mailings.
-->

## Formuler des hypothèses sur les causes potentielles {#potential-causes}

Posez-vous les questions suivantes pour identifier les causes possibles de votre problème de délivrabilité :

* Y a-t-il eu récemment un changement dans la segmentation des listes ?
* Ai-je acquis de nouvelles sources de données ?
* Ai-je envoyé par inadvertance un fichier de quarantaine ?
* Le problème peut-il être dû au contenu de mon message ?
* Est-ce que j’envoie des emails assez souvent pour maintenir le rodage des adresses IP ?
* Ai-je segmenté mes envois par activité/engagement ou ai-je envoyé des fichiers complets ?
* Quel est le segment « sûr » de mon dossier en termes de récence ?
* Des stratégies de réactivation et de reconfirmation sont-elles en place pour les segments qui ne sont pas définis comme sûrs ?

## Résoudre le problème {#address-issue}

### Plaintes

[](/help/metrics/complaints.md)Les plaintes sont définies par les abonnés qui signalent un email comme indésirable en appuyant sur le bouton correspondant de leur boîte de réception.

Si votre problème de diffusion est dû à des plaintes :
* Vous devez essayer de déterminer pourquoi les destinataires se plaignent.
* Vous pouvez également envisager de déplacer votre lien de désabonnement en haut de votre e-mail. Ainsi, les abonnés pourront se désabonner au lieu de se plaindre en utilisant le bouton spam.

Les expéditeurs peuvent recueillir une mine d’informations à partir des plaintes issues d’une [feedback loop](/help/transition-process/infrastructure.md#feedback-loops) :
* Il est important de regrouper les données et de rechercher des schémas dans des éléments comme la source d’opt-in, la durée d’abonnement à l’adresse, ou même certains comportements liés aux données démographiques.
* Les plaintes permettent souvent d’identifier une source ou un segment de données à risque dans le fichier. Le risque se définit comme une probabilité maximale de plainte, ce qui peut nuire à la réputation, et en retour, aux taux de placement en boîte de réception.

Les plaintes proviennent aussi des abonnés qui ne veulent tout simplement plus recevoir d’emails :
* Souvent, cette situation découle d’un nombre excessif de messages, de leur perception par les abonnés, du caractère inattendu des messages ou de l’oubli par les abonnés de leur accord préalable.
* Par ailleurs, il est important de vérifier que tous les points de collecte sont clairs et qu’il n’y a pas de cases précochées dans vos points d’acquisition.
* Vous devez également envoyer un e-mail de bienvenue aux abonnés qui donnent leur accord préalable pour leur expliquer à quelle fréquence ils peuvent s’attendre à recevoir des e-mails de votre part.

### Validité des données

**Les erreurs hard se produisent lorsque vous effectuez un envoi vers une adresse en échec d&#39;un FAI.****** Une adresse peut être en échec pour de nombreuses raisons, notamment :
* Adresse mal orthographiée. Il est possible de résoudre ce problème grâce à un service de validation des données en temps réel ou à l’obligation de confirmer l’accord préalable avant d’envoyer des e-mails marketing à cette adresse.
* Liste ou source de données incorrecte. Si les adresses proviennent d’une nouvelle source, vérifiez comment elles ont été collectées et assurez-vous que leur utilisation a été autorisée.
* Envoi à une adresse active à un moment donné, mais fermée ou supprimée suite à une période d’inactivité.

### Engagement

Outre les plaintes et la validité des données, les FAI privilégient plus que jamais l’**engagement positif** pour prendre des décisions de diffusion. Ils cherchent à savoir si vos abonnés ouvrent vos emails ou les effacent sans les lire. Comme ils ne partagent pas ces données avec les expéditeurs, nous devons utiliser les informations disponibles et traduire les ouvertures/clics/transactions en engagements.

Dans le cadre de la gestion permanente de la réputation, il est important de comprendre le niveau d’engagement des abonnés de votre liste et d’établir une **hiérarchie des risques liés à la récence** pour les abonnés de chaque fichier. La récence est définie comme la date d’ouverture/de clic/de transaction ou d’abonnement la plus récente. Cette période peut différer selon la verticale. Pour ce faire :

1. Déterminez les segments actifs (« sûrs ») pour chaque verticale. Il s’agit généralement d’abonnés qui ont été actifs au cours des 3 à 6 derniers mois.
1. Réduisez la fréquence au niveau des inactifs.
1. Créez une série de [réengagements](/help/additional-resources/re-engagement.md) pour les inactifs à risque modéré. Il s’agit généralement d’abonnés qui ne se sont pas engagés depuis 6 à 9 mois.
1. Développez une campagne de reconfirmation pour les inactifs à risque élevé. Il s’agit généralement d’abonnés qui ne se sont pas engagés par email depuis 9 à 12 mois.
1. Enfin, définissez une règle d’abandon et supprimez les abonnés qui n’ont pas ouvert vos emails depuis « x » mois. Nous recommandons généralement une durée de 12 mois, mais cela peut varier en fonction des ventes et du cycle d’achat.
