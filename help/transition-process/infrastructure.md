---
title: Infrastructure
description: Découvrez ce qui est nécessaire pour construire correctement une infrastructure d’email.
topics: Deliverability
jira: KT-7052
thumbnail: kt7052.jpg
doc-type: article
activity: understand
role: Admin, Leader
level: Beginner
team: ACS
exl-id: 4025d95c-cc77-4e0c-9904-aaf60019b18c
source-git-commit: 6b312cdbba496818337c97ec4f42962aea757901
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 2%

---

# Infrastructure

La réussite de la délivrabilité dépend d’une base solide. L’infrastructure de messagerie est un élément central. Une infrastructure de messagerie correctement construite comprend plusieurs composants, à savoir le ou les domaines et adresses IP. Ces composants sont comme la machine derrière les emails que vous envoyez et ils sont souvent l&#39;ancre de la réputation d&#39;envoi. Les consultants en délivrabilité s’assurent que ces éléments sont correctement configurés lors de l’implémentation, mais en raison de l’élément de réputation, il est important pour vous d’avoir cette compréhension de base.

## Configuration et stratégie du domaine {#domain-setup-and-strategy}

Les temps ont changé, et certains FAI (comme Gmail et Yahoo) intègrent désormais la réputation de domaine comme point supplémentaire lorsqu&#39;il s&#39;agit d&#39;associer la réputation d&#39;un email à un expéditeur. La réputation de votre domaine est basée sur votre domaine d’envoi plutôt que sur votre adresse IP. Cela signifie que votre marque a la priorité sur les décisions de filtrage des FAI.

Une partie du processus d’intégration des nouveaux expéditeurs sur les plateformes d’Adobe inclut la configuration de vos domaines d’envoi et la vérification de la bonne configuration de votre infrastructure. Vous devez travailler avec un expert sur les domaines que vous prévoyez d’utiliser à long terme. Voici quelques conseils pour définir une bonne stratégie de domaine :

* Soyez aussi clair et réfléchissant que possible à la marque avec le domaine que vous choisissez afin que les utilisateurs n&#39;identifient pas incorrectement l&#39;email comme spam. Voici quelques exemples : newsletter.foo.com, receipts.foo.com, etc.
* Vous ne devez pas utiliser votre domaine parent ou d’entreprise, car cela pourrait avoir un impact sur la diffusion du courrier de votre entreprise aux FAI.
* Envisagez d’utiliser un sous-domaine de votre domaine parent pour légitimer votre domaine d’envoi.
* Séparez vos sous-domaines pour les catégories de messages transactionnels et marketing. Cela permettra à votre flux de trafic email d’être plus fiable, car les FAI recherchent cette méthode d’envoi, qui est une bonne pratique connue et vivement recommandée.

## Stratégie IP {#ip-strategy}

Il est important de former une stratégie IP bien structurée pour aider à établir une réputation positive. Le nombre d’adresses IP et de configurations varie en fonction de votre modèle d’entreprise et de vos objectifs marketing. Travailler avec un expert pour élaborer une stratégie claire pour commencer correctement. Tenez compte des points importants à noter :

* **Trop d’adresses IP** peut déclencher des problèmes de réputation, car il s’agit d’une tactique courante pour **raquette**, qui est une tactique utilisée par les spammeurs où le trafic est réparti sur de nombreuses adresses IP afin de maximiser la diffusion des spammeurs. Même si vous n’êtes pas un spammeur, vous pouvez ressembler à un si vous utilisez trop d’adresses IP, en particulier si ces adresses IP n’ont pas eu de trafic précédent.
* **Trop peu d’adresses IP** peut entraîner des problèmes de débit et peut éventuellement déclencher des problèmes de réputation. Le débit varie en fonction du FAI. Le degré et la rapidité d’acceptation d’un FAI dépendent généralement de son infrastructure et de son seuil de réputation.
* La séparation du trafic pour les types de messages est essentielle. Il est important, au minimum, de séparer le marketing et le courrier transactionnel dans des groupes d’adresses IP distincts.
* En fonction de votre stratégie de messagerie, il peut également être conseillé de séparer différents produits ou flux marketing sur différents pools d’adresses IP si votre réputation est radicalement différente. Certains spécialistes du marketing segmentent également par région. La séparation de l’adresse IP pour le trafic ayant une réputation plus faible ne corrige pas le problème de réputation, mais empêchera les problèmes liés à vos diffusions email de &quot;bonne réputation&quot;. Après tout, vous ne voulez pas sacrifier votre bonne audience pour une audience plus risquée.

## Boucles de commentaires {#feedback-loops}

En arrière-plan, les plateformes d’Adobe traitent des données concernant les rebonds, les plaintes, les désabonnements, etc. La configuration de ces boucles de rétroaction est un aspect important de la délivrabilité. Les plaintes peuvent nuire à la réputation. Vous devez donc utiliser des adresses électroniques qui enregistrent les plaintes de votre audience cible. Il est important de noter que Gmail ne fournit pas ces données. Les en-têtes de désabonnement aux listes et le filtrage de l’engagement sont particulièrement importants pour les abonnés Gmail, qui constituent désormais la majorité des bases de données d’abonnés.

## Authentification {#authentication}

L’authentification est le processus que les FAI utilisent pour valider l’identité d’un expéditeur. Les deux protocoles d’authentification les plus courants sont : [!DNL Sender Policy Framework] (SPF) et [!DNL DomainKeys Identified Mail] (DKIM). Ils ne sont pas visibles par l’utilisateur final mais aident les FAI à filtrer les emails des expéditeurs vérifiés. [!DNL Domain-based Message Authentication Reporting and Conformance] (DMARC) gagne en popularité, bien que ses politiques ne soient pas encore intégrées par tous les FAI dans leurs systèmes de réputation.

### SPF

[!DNL Sender Policy Framework] (SPF) est une méthode d’authentification qui permet au propriétaire d’un domaine de spécifier les serveurs de messagerie qu’il utilise pour envoyer des courriers à partir de ce domaine.

### DKIM

[!DNL Domain Keys Identified Mail] (DKIM) est une méthode d’authentification utilisée pour détecter les adresses d’expéditeur falsifiées (communément appelées usurpation). Si DKIM est activé, il permet au destinataire de confirmer si l&#39;expéditeur est autorisé à envoyer des emails depuis ce domaine.

### DMARC

[!DNL Domain-based Message Authentication, Reporting and Conformance] (DMARC) est une méthode d’authentification qui permet aux propriétaires de domaine de protéger leur domaine d’une utilisation non autorisée. DMARC utilise SPF ou DKIM ou les deux pour permettre au propriétaire d’un domaine de contrôler ce qui arrive aux emails qui ne parviennent pas à s’authentifier : délivrés, mis en quarantaine ou rejetés.

## Ressources spécifiques au produit

**Campaign**

* Découvrez comment déléguer entièrement un sous-domaine à Adobe Campaign Classic ou Standard dans [cette section](/help/additional-resources/ac-domain-name-setup.md).
* [Panneau de Contrôle : délégation complète de sous-domaines (tutoriel)](https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html) - *Découvrez comment déléguer entièrement un sous-domaine à Adobe Campaign Classic.*
* [Panneau de Contrôle : délégation complète de sous-domaines (tutoriel)](https://experienceleague.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html) - *Découvrez comment déléguer entièrement un sous-domaine à Adobe Campaign Standard.*
* En savoir plus sur l’implémentation d’une feedback loop pour une instance de Campaign Classic dans [cette section](/help/additional-resources/acc-technical-recommendations.md#feedback-loop-acc).

## Ressources supplémentaires

* En savoir plus sur les méthodes d’authentification SPF, DKIM et DMARC dans [cette section](/help/additional-resources/authentication.md).
* En savoir plus sur l’amélioration de la réputation de vos emails grâce au réchauffement des adresses IP dans [cette section](/help/additional-resources/increase-reputation-with-ip-warming.md).
