---
title: Améliorer la réputation de vos emails grâce au réchauffement des adresses IP
description: Découvrez pourquoi il est important d'améliorer la réputation de vos emails avec le réchauffement de votre adresse IP, et comment procéder pour une délivrabilité optimale.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: b553a13e-2055-4abc-b784-fd52792380d0
source-git-commit: eba8162150b5662ca18687b873114858f8eb00cc
workflow-type: ht
source-wordcount: '1582'
ht-degree: 100%

---

# Améliorer la réputation de vos emails grâce au réchauffement des adresses IP

<!--Increase your email reputation with IP warming

## IP Warming overview

In the Adobe Deliverability Consulting and Deliverability Operations teams, we have a vested interest in helping new Campaign customers be as successful as possible as they embark on the route of an IP warming process. If you’ve never been a part of such a project, you may have a lot of questions about it. Let’s get down to the details!-->

## Prise en main

Adobe demande que les clients partagent leur configuration pour aider l&#39;équipe d&#39;Adobe chargée de la délivrabilité à comprendre votre programme spécifique. Les questions que nous posons sont conçues pour aider l&#39;équipe d&#39;Adobe chargée de la délivrabilité à se faire une idée de votre réputation d&#39;envoi et de votre volume d&#39;emails. Faute d&#39;une compréhension concrète de votre modèle commercial, des objectifs de marketing par email et des mesures de réputation, nous ne serons pas en mesure de personnaliser la stratégie, ce qui peut créer un risque de problème de délivrabilité.

Dès le départ, vous recevrez vos propres adresses IP dédiées (Internet Protocol). Dans le cadre de l&#39;envoi d&#39;emails, une adresse IP est l&#39;itinéraire utilisé pour envoyer vos emails à vos clients. Les domaines et adresses IP sont utilisés pour identifier les expéditeurs sur un réseau pour les fournisseurs d&#39;accès à Internet destinataires. Adobe attribue le nombre approprié d&#39;adresses IP dédiées pour l&#39;envoi d&#39;emails, en fonction du volume d&#39;envoi, des programmes d&#39;email, des pratiques de segmentation des données et de votre contrat.

**Rubriques connexes :**
* [Transition en douceur lors du changement de plateforme de messagerie](../../help/transition-process/switching-email-platforms.md)
* [Stratégie IP](../../help/transition-process/infrastructure.md#ip-strategy)
* [Considérations spécifiques aux fournisseurs d’accès (FAI) lors du préchauffage des adresses IP](../../help/transition-process/isp-specific-considerations-during-ip-warming.md)

## Préchauffage d’une adresse IP : pour quoi faire ?  {#why-ip-warming}

Les fournisseurs d’accès à Internet (FAI) ou les fournisseurs de service de messagerie (MBP) prennent des précautions lorsqu’ils détectent une adresse IP et un domaine d’envoi inconnus. Les fournisseurs d’accès à Internet et les fournisseurs de services de messagerie surveillent de près l’adresse IP et le domaine d’envoi pour déterminer si les e-mails envoyés depuis cette adresse IP et ce domaine sont des spams ou non. Il s&#39;agit de la procédure standard associée à toute nouvelle adresse IP d&#39;envoi, quel que soit le type d&#39;expéditeur.

Les FAI examinent attentivement le volume d&#39;envoi, la fréquence d&#39;envoi, les plaintes et les taux de rebond générés par ces messages. Tous ces éléments sont étroitement contrôlés parce que, bons ou mauvais, ils représentent des indicateurs de la réputation de l&#39;expéditeur.

Naturellement, ce processus d&#39;examen de ces points de données prend du temps et ne peut être réalisé en un jour ou deux. La réputation se construit au fil du temps. Ce processus revient à envisager de laisser un étranger pénétrer chez soi. Auriez-vous des réserves pour laisser entrer chez vous quelqu&#39;un que vous n&#39;avez jamais rencontré ?

La réponse est très probablement oui. Vous voudriez analyser cette personne et ses motivations. Vous veulent-elles du mal ? Représentent-elles une menace ? Les FAI font de même pour protéger leur réseau de tout trafic malveillant ou indésirable. Les mesures de réputation positives vous aident à faire un grand pas en avant dans un processus de réchauffement réussi des adresses IP. C&#39;est pourquoi nous insistons sur l&#39;importance de commencer par envoyer de petits volumes d&#39;emails et d&#39;abord à vos clients les plus engagés. Pour plus d&#39;informations à ce sujet, voir la section [Critères de ciblage lors de l&#39;envoi de nouveau trafic](/help/transition-process/targeting-criteria.md).

L&#39;envoi de grandes quantités d&#39;emails à partir d&#39;adresses IP dès la phase initiale ou d&#39;une adresse IP complètement nouvelle est une mauvaise pratique et provoquera probablement des problèmes de délivrabilité. Il est important de noter que même si vous commencez à envoyer de petits volumes et que vous les augmentez progressivement comme recommandé, il est toujours nécessaire de suivre les bonnes pratiques en matière de messagerie électronique.

![](../../help/assets/ip-warming-volume-trend.png)

## Autorisation d&#39;envoyer des emails (opt-in explicite)

Il s&#39;agit du composant le plus important de la gestion et du développement d&#39;une liste d&#39;emails d&#39;abonnés. À mesure que les lois antispam se développent et deviennent plus complètes à l&#39;échelle internationale, il devrait être primordial pour les spécialistes du marketing de s&#39;assurer qu&#39;ils ont reçu le consentement explicite (ou formel) de chaque abonné présent dans leurs listes. Autrement dit, chaque abonné a accepté de recevoir des emails de la part de votre marque. Cette démarche se différencie du consentement implicite lorsqu&#39;une personne est ajoutée à une liste d&#39;emails après avoir effectué une action qui n&#39;était pas explicitement une inscription à un programme d&#39;emails.

En savoir plus sur la [politique d&#39;utilisation acceptable d&#39;Adobe](https://www.adobe.com/fr/legal/terms/aup.html).

## Mesures de la réputation : que recherchent les FAI ?

Les FAI utilisent une technologie sophistiquée pour prendre des décisions pertinentes sur la diffusion ou non des emails provenant de réseaux externes. Ils possèdent parfois des algorithmes complexes et exclusifs parmi leurs outils pour les aider dans ce processus.

Voici quelques-uns des points de données examinés :

* Accès aux pièges à spam
* Accès aux listes bloquées
* E-mails rejetés
* Engagement des abonnés

Les FAI exigent des configurations techniques spécifiques alignées sur leurs politiques et leurs bonnes pratiques. Adobe configure vos adresses IP et sous-domaines délégués afin de vous identifier en tant qu&#39;expéditeur responsable et fiable. Il s&#39;agit de l&#39;[authentification par email](/help/transition-process/infrastructure.md#authentication). L&#39;authentification permet aux destinataires de vérifier si un expéditeur dispose des droits d&#39;envoi à partir de cette adresse IP ou de ce domaine.

L&#39;authentification permet aux FAI de vérifier que l&#39;entreprise qui réalise l&#39;envoi à partir d&#39;un domaine ou d&#39;une adresse IP a le droit de le faire. Il s&#39;agit essentiellement de prouver votre identité et de s&#39;assurer que vous ne vous faites pas passer pour quelqu&#39;un d&#39;autre, et inversement, que quelqu&#39;un d&#39;autre n&#39;usurpe pas votre identité.

Chez Adobe, nous configurons SPF et DKIM par défaut et nous configurons DMARC sur demande. Les FAI référencent SPF et DKIM comme principales formes d&#39;authentification. De nombreux FAI intègrent également DMARC (Domain-based Message Authentication, Reports and Conformance) dans leurs décisions de filtrage. Les emails non authentifiés ne sont pas nécessairement bloqués, mais ils sont soumis à un filtrage supplémentaire.

## Réchauffement des adresses IP : à quoi s&#39;attendre ?

### Emails limités ou bloqués

Les spammeurs changent en permanence d&#39;adresses IP pour leurs envois : ils utilisent un pool d&#39;adresses IP jusqu&#39;à ce qu&#39;elles soient fermées, après quoi ils répètent le processus sur un autre pool. Les FAI traitent donc soigneusement le trafic envoyé à partir de nouvelles adresses IP. Ils bloquent l&#39;envoi d&#39;une grande quantité d&#39;emails à partir d&#39;adresses IP parce qu&#39;ils soupçonnent qu&#39;il s&#39;agit d&#39;une activité malveillante exécutée par des spammeurs.

Il n&#39;est donc pas rare de recevoir des messages de report ou de ralentissement lorsque vous commencez à envoyer des emails à partir de vos nouvelles adresses IP. Après quelques reprises, le message est généralement accepté et remis.

Rétablir un flux de trafic normal vers les FAI qui diffèrent les nouveaux expéditeurs peut prendre plusieurs jours. Malgré cela, continuez à envoyer vos emails : concentrez-vous sur les envois aux abonnés les plus engagés de votre messagerie.

Dans de rares cas, le FAI bloque le nouvel expéditeur. Adobe surveille votre compte, et si un tel blocage est suspecté, Adobe contactera le FAI pour essayer de remédier à la situation de la meilleure façon possible.

Gardez à l&#39;esprit que l&#39;essentiel ici, c&#39;est la cohérence. Les schémas de volume d&#39;envoi d&#39;emails irréguliers et peu fréquents entraînent des problèmes de délivrabilité au cours du processus.

### Plaintes

[Les plaintes](/help/metrics/complaints.md) ont lieu lorsqu&#39;un abonné désigne un email comme indésirable par l&#39;intermédiaire de son programme de messagerie. Un avis est alors envoyé au FAI au sujet de l&#39;activité concernant la plainte. Si un nombre suffisant de plaintes lui parviennent, il interviendra pour protéger ses clients : il s&#39;agira peut-être de bloquer de nombreux emails avant qu&#39;ils n&#39;arrivent aux abonnés, ou de les diriger partiellement vers un dossier de groupage plutôt que vers les boîtes de réception des abonnés. Si votre problème de diffusion résulte de plaintes, il est important de déterminer pourquoi les destinataires les émettent.

Les abonnés se plaignent pour diverses raisons. Parfois, ils ne veulent plus recevoir d&#39;emails de votre part, peut-être parce qu&#39;ils ont l&#39;impression de recevoir trop de messages sur un même sujet, parce qu&#39;ils ne s&#39;attendaient pas au message, ou qu&#39;ils ne se souviennent pas de s&#39;être inscrits pour les recevoir.

### Validité des données

Les rebonds définitifs se produisent lorsque vous effectuez un envoi vers une adresse en échec d’un FAI. Une adresse peut être en échec pour différentes raisons, par exemple une erreur de saisie de l&#39;adresse ou d&#39;envoi à une adresse qui était auparavant principale mais qui a été fermée ou résiliée suite à une période d&#39;inactivité.

Si vous rencontrez un nombre important de rebonds définitifs, il est important de comprendre pourquoi. Vérifiez comment les adresses ont été collectées et confirmez que l&#39;autorisation a été accordée. Parfois, les utilisateurs ferment leur compte de messagerie et n&#39;en informent pas ceux qui ont placé cette adresse dans leur liste marketing.

### Engagement

Les FAI recherchent un volume régulier et une bonne qualité des données. Vous augmenterez progressivement et régulièrement le trafic au cours des quatre à huit semaines suivantes. Il arrive que les cumuls nécessitent plus ou moins de temps en fonction de votre volume et de vos objectifs, mais généralement, il s&#39;agit d&#39;un processus d&#39;au moins 8 semaines.

Le trafic des emails doit être déployé avec une progression lente et régulière, augmentant chaque semaine jusqu&#39;à l&#39;envoi de la liste complète. En outre, chaque segment suit le calendrier jusqu&#39;à l&#39;achèvement. Commencez avec les abonnés les plus récents, et finissez avec les abonnés les moins engagés. À noter également que certains FAI peuvent nécessiter une approche plus personnalisée en raison de leur gestion du nouveau trafic.

En savoir plus sur l&#39;[engagement](/help/engagement.md).

## Garder le cap

Vous pouvez être tenté d&#39;accélérer le processus de réchauffement des adresses IP en diffusant un volume supérieur à celui recommandé, en négligeant de passer du temps à identifier vos abonnés les plus engagés et en n&#39;envoyant pas d&#39;email à ces abonnés lors de la phase initiale pour bâtir une réputation positive. Résistez à cette envie ! Cela ne vous aidera pas à long terme.

Il est très important de commencer à contacter les personnes abonnées les plus engagées (par e-mail !) uniquement, lors des premières étapes du réchauffement des adresses IP. Ces clients sont les plus précieux et leur propension à ouvrir vos emails vous aidera à montrer aux FAI que vous êtes un spécialiste marketing qui envoie des emails intéressants et recherchés. La démarche indique également aux FAI que vous suivez les règles et les bonnes pratiques.

## Conclusion

Gardez à l&#39;esprit que le réchauffement des adresses IP est un marathon, pas un sprint !  Bien que le processus puisse sembler lourd et fastidieux, il serait plus difficile de réparer une réputation altérée par l&#39;omission des bonnes pratiques éprouvées en matière de messagerie électronique.

Plus vos pratiques d&#39;envoi sont efficaces et plus vos scores de réputation sont élevés auprès des FAI, plus vos emails auront une forte probabilité de diffusion. Le réchauffement et la montée en puissance des adresses IP, ainsi que l&#39;application des bonnes pratiques pour la conception de votre envoi, vous aideront à optimiser votre diffusion en boîte de réception.

Notre équipe mondiale chargé de la délivrabilité est votre partenaire dans ce processus et vous aidera, au cours de cette phase de réchauffement des adresses IP, à vous positionner pour réussir.
