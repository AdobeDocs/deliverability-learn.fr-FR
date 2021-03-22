---
title: Augmentez la réputation de vos emails grâce au rodage des adresses IP
description: Découvrez pourquoi il est important d'améliorer la réputation de votre courriel avec le réchauffement de votre adresse IP et comment procéder pour une délivrabilité optimale.
feature: Ressources supplémentaires
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 96ed84da391faaabd3001ddd6a411ddc1f46b033
workflow-type: tm+mt
source-wordcount: '1602'
ht-degree: 2%

---


# Augmentez la réputation de vos emails grâce au rodage des adresses IP

<!--Increase your email reputation with IP warming

## IP Warming overview

In the Adobe Deliverability Consulting and Deliverability Operations teams, we have a vested interest in helping new Campaign customers be as successful as possible as they embark on the route of an IP warming process. If you’ve never been a part of such a project, you may have a lot of questions about it. Let’s get down to the details!-->

## Prise en main

L&#39;Adobe exige que les clients partagent leur configuration pour aider l&#39;équipe de délivrabilité des Adobes à comprendre votre programme unique. Les questions que nous posons sont conçues pour aider l&#39;équipe de la délivrabilité des Adobes à se faire une idée de votre réputation d&#39;envoi et de votre volume de courrier électronique. Sans une compréhension concrète de votre modèle d&#39;entreprise, des objectifs de marketing par courriel et des mesures de réputation, nous ne serons pas en mesure de personnaliser la stratégie et il y a un risque de problèmes de délivrabilité.

Dès le départ, vous recevrez vos propres adresses IP dédiées (Internet Protocol). Dans le cadre de l’envoi de courriers électroniques, une adresse IP est l’itinéraire utilisé pour envoyer vos courriers électroniques à vos clients. Les adresses et domaines IP sont utilisés pour identifier les expéditeurs sur un réseau aux fournisseurs d’accès à Internet destinataires. L’Adobe attribue le nombre approprié d’adresses IP dédiées pour l’envoi de courriers électroniques, en fonction du volume d’envoi, des programmes électroniques, des pratiques de segmentation des données et de votre contrat.

**Rubriques connexes :**
* [Transition en douceur lors du changement de plate-forme de messagerie](../../help/transition-process/switching-email-platforms.md)
* [Stratégie IP](../../help/transition-process/infrastructure.md#ip-strategy)
* [Considérations spécifiques aux fournisseurs d’accès lors du réchauffement des IP](../../help/transition-process/isp-specific-considerations-during-ip-warming.md)

## Réchauffement IP : Pourquoi est-ce fait ? {#why-ip-warming}

Les Prestataires Internet (FAI) ou les fournisseurs de boîtes aux lettres (MBP) prennent des précautions lorsqu&#39;ils détectent une adresse IP et un domaine d&#39;envoi inconnus. Il s’agit de la procédure standard associée à toute nouvelle adresse IP d’envoi, quel que soit le type d’expéditeur. Les FAI/MBP surveillent de près l&#39;IP et le domaine d&#39;envoi pour déterminer si les courriels envoyés depuis cette IP et ce domaine sont des spams ou non.  Il s’agit de la procédure standard associée à toute nouvelle adresse IP d’envoi, quel que soit le type d’expéditeur.

Les FSI examinent attentivement le volume d&#39;envoi, la fréquence d&#39;envoi, les plaintes et les taux de rebond générés par ces envois. Tous ces éléments sont étroitement contrôlés parce qu&#39;ils sont des indicateurs de la réputation de l&#39;expéditeur - qu&#39;il soit bon ou mauvais.

Naturellement, ce processus d&#39;examen de ces points de données prend du temps et ne peut être réalisé en un jour ou deux. La réputation est construite au fil du temps. Ce processus est comme laisser un étranger chez lui. Auriez-vous des réserves à faire entrer chez vous quelqu&#39;un que vous n&#39;avez jamais rencontré ?

La réponse est très probablement oui. Vous voudriez analyser cette personne et ses motivations. Est-ce qu&#39;ils signifient du mal ? Sont-ils une menace ? Les FAI font de même pour protéger leur réseau du trafic malveillant ou indésirable. Les mesures de réputation positives vous aident à faire un grand pas en avant dans un processus de réchauffement de la PI réussi. C&#39;est pourquoi nous insistons sur l&#39;importance de commencer par envoyer de petits volumes de courriels et de commencer à envoyer d&#39;abord à vos clients les plus engagés. Pour plus d’informations sur ce sujet, voir [Critères de ciblage lors de l’envoi de nouveau trafic](/help/transition-process/targeting-criteria.md).

L&#39;envoi de grandes quantités d&#39;e-mails à partir d&#39;une adresse IP toute neuve ou d&#39;adresses IP immédiatement à la porte est une mauvaise pratique et vous causera probablement des problèmes de délivrabilité. Il est important de noter que même si vous début envoyer de petits volumes et les augmenter progressivement comme recommandé, il est toujours nécessaire de suivre les meilleures pratiques en matière de messagerie électronique.

![](../../help/assets/ip-warming-volume-trend.png)

## Autorisation de courrier (inclusion explicite)

Il s’agit du composant le plus important de la gestion et de l’augmentation d’une liste de messagerie d’abonnés. À mesure que les lois antispam se développent et deviennent plus complètes à l’échelle internationale, il devrait être Principal pour les spécialistes du marketing de s’assurer qu’ils ont reçu le consentement explicite (ou explicite) de chaque abonné sur leur liste. Autrement dit, chaque abonné a accepté de recevoir des courriels de votre marque. Ceci diffère du consentement implicite lorsqu’une personne est ajoutée à une liste de messagerie après avoir exécuté une action qui n’était pas explicitement inscrite à un programme de messagerie.

Pour en savoir plus sur la [politique d&#39;utilisation acceptable de l&#39;Adobe](https://www.adobe.com/fr/legal/terms/aup.html).

## Mesures de réputation : Que recherchent les FAI ?

Les FAI utilisent une technologie sophistiquée pour prendre des décisions éclairées sur la livraison ou non de courriels qu&#39;ils reçoivent de réseaux externes. Ils ont parfois des algorithmes complexes et propriétaires dans leur ensemble d&#39;outils pour les aider dans ce processus.

Voici quelques-uns des points de données examinés :

* Accès au piège indésirable
* Accès à la Liste bloquée
* Retours par courriel
* Engagement des abonnés

Les fournisseurs de services Internet requièrent des configurations techniques spécifiques qui s&#39;alignent sur leurs politiques et leurs meilleures pratiques. Adobe configure vos adresses IP et sous-domaines délégués afin de vous identifier en tant qu’expéditeur responsable et fiable. Il s’agit de l’authentification [par courrier électronique](/help/transition-process/infrastructure.md#authentication). L’authentification permet aux destinataires de vérifier si un expéditeur dispose des droits d’envoi à partir de cette adresse IP ou de ce domaine.

L’authentification permet aux FAI de vérifier que l’envoi de société à partir d’un domaine ou d’une adresse IP a le droit de le faire. C&#39;est essentiellement pour prouver votre identité et pour s&#39;assurer que vous ne faites pas semblant d&#39;être quelqu&#39;un d&#39;autre, et que quelqu&#39;un d&#39;autre ne fait pas semblant d&#39;être vous.

À l’Adobe, nous configurerons SPF et DKIM par défaut et nous configurerons DMARC sur demande. Les FAI référencent SPF et DKIM comme les Principales formes d&#39;authentification. De nombreux FAI intègrent également DMARC (Domain-based Message Authentication, Rapports &amp; Conformance) dans leurs décisions de filtrage. Les courriels non authentifiés ne sont pas nécessairement bloqués, mais ils sont soumis à un filtrage supplémentaire.

## Réchauffement IP : A quoi s&#39;attendre

### Messagerie limitée ou bloquée

Les spammeurs envoient tout le temps de nouvelles adresses IP - ils vont graver à travers un pool d&#39;adresses IP jusqu&#39;à ce qu&#39;ils se ferment et répètent le processus sur un autre pool d&#39;adresses IP. En conséquence, les fournisseurs de services Internet traitent soigneusement le trafic envoyé à partir de nouvelles adresses IP. Ils bloquent l&#39;envoi d&#39;une grande quantité de courriels par IP parce qu&#39;ils soupçonnent qu&#39;il s&#39;agit d&#39;une activité malveillante exécutée par des spammeurs.

Par conséquent, il n’est pas rare de recevoir des messages de report ou de ralentissement lorsque vous début d’envoyer des messages à partir de vos nouvelles adresses IP. Après quelques Reprises, le message est généralement accepté et remis.

Il peut s&#39;écouler quelques jours avant que les fournisseurs de services Internet ne parviennent à un flux normal de trafic qui retarde l&#39;envoi de nouveaux expéditeurs. Malgré cela, n&#39;arrêtez pas d&#39;envoyer du courrier - continuez à vous concentrer uniquement sur l&#39;envoi à vos abonnés de messagerie les plus engagés.

Dans de rares cas, le FAI bloque le nouvel expéditeur. L&#39;Adobe surveille votre compte, et si un tel blocage est suspecté, tentera de contacter le fournisseur de services Internet pour essayer de remédier à la situation de la meilleure façon possible.

Rappelez-vous que la cohérence est ici la clé. Des schémas de volume d&#39;envoi irréguliers et des modèles d&#39;envoi peu fréquents entraîneront des problèmes de délivrabilité en cours de route.

### Plaintes

[](/help/metrics/complaints.md) Plaintes lorsqu&#39;un abonné désigne un courriel comme indésirable par l&#39;intermédiaire de son programme électronique. Ceci envoie un avis à l&#39;ISP au sujet de l&#39;activité de la plainte. S&#39;il y a assez de ces plaintes qui arrivent au FAI, ce FAI agira pour protéger ses clients - peut-être bloquer de nombreux courriels pour se rendre aux abonnés ou diriger une partie de ces courriels vers le dossier en vrac plutôt que vers les boîtes de réception des abonnés. Si votre problème de diffusion est causé par des plaintes, il est important de déterminer pourquoi les destinataires se plaignent.

Les abonnés se plaignent pour diverses raisons. Parfois, un abonné ne veut plus recevoir d’e-mails de votre part, peut-être parce qu’il a l’impression de recevoir trop de messages sur le même sujet, qu’il n’attendait pas le message ou qu’il ne se souvient pas de s’être inscrit pour recevoir vos e-mails.

### Validité des données

Les erreurs hard se produisent lorsque vous effectuez un envoi à une adresse en échec d’un FAI. Une adresse peut être non livrable pour de nombreuses raisons, comme une erreur de saisie de l&#39;adresse ou d&#39;envoi à une adresse qui était auparavant principale mais qui a été fermée ou terminée après une période d&#39;inactivité.

Si vous rencontrez un nombre important de rebonds durs, il est important de comprendre pourquoi. Vérifiez comment les adresses ont été collectées et confirmez que l&#39;autorisation a été accordée. Parfois, les utilisateurs ferment leur compte de messagerie et n’en informent pas ceux qui ont cette adresse sur leur liste marketing.

### Engagement

Les FAI recherchent un volume cohérent et une bonne qualité de données. Vous augmenterez lentement et régulièrement le trafic au cours des quatre à huit prochaines semaines. Il arrive que les cumuls nécessitent plus ou moins de temps en fonction de votre volume et de vos objectifs, mais généralement, il s’agit d’un processus d’au moins 8 semaines.

Le trafic de courrier électronique doit être déployé avec une progression lente et régulière, augmentant chaque semaine jusqu’à l’envoi de la liste entière. En outre, chaque segment suivra le calendrier jusqu&#39;à l&#39;achèvement. Début avec les abonnés les plus récents en premier, et finir avec les abonnés les moins engagés en dernier. Veuillez également noter que certains FAI peuvent nécessiter une approche plus personnalisée en raison de leur gestion du nouveau trafic.

En savoir plus sur [l&#39;engagement](/help/engagement.md).

## Restez en cours

Vous pouvez être tenté d&#39;accélérer le processus de réchauffement de la propriété intellectuelle en envoyant plus de volume que ce qui est recommandé, en négligeant de passer du temps à identifier vos abonnés les plus engagés et en ne les envoyant pas par la poste d&#39;abord à ces abonnés afin de bâtir une réputation positive. Résistez à cette envie ! Cela ne vous aidera pas à long terme.

Il est très important d&#39;envoyer un début par courrier électronique (avec un email !) abonnés uniquement pour les premières étapes du réchauffement de la propriété intellectuelle. Ces clients sont vos plus précieux et leur propension à ouvrir vos courriels vous aidera à montrer au début que vous êtes un spécialiste du marketing qui envoie des courriels intéressants et recherchés. Il montre également les fournisseurs de services Internet que vous suivez les règles et les bonnes pratiques.

## Conclusion

Rappelez-vous : Le réchauffement IP est un marathon - pas un sprint !  Bien que le processus puisse sembler lourd et chronophage, il serait plus difficile de réparer une réputation endommagée par le fait de ne pas suivre les bonnes pratiques éprouvées en matière de messagerie électronique.

Plus vos pratiques d&#39;envoi sont efficaces et plus vos scores de réputation sont élevés avec les FAI, plus vos courriels seront probablement diffusés. Le réchauffement et l&#39;augmentation des adresses IP, ainsi que le suivi des meilleures pratiques pour la conception de votre envoi, vous aideront à optimiser votre diffusion de boîte de réception.

Notre équipe de livraison mondiale est votre partenaire dans ce processus et vous aidera durant cette phase de réchauffement de la IP à vous positionner pour le succès.
