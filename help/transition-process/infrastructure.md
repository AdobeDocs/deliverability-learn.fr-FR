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
TQID: https://experienceleague.adobe.com/FWlVtNGACEM6dKsnYQJU-z04mP902M5EXZmxxsKDyqU
product_v2:
  - id: b27e5950-9033-45ac-9f86-eb22e567f615
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b0bb9048-d951-48d8-8232-45cf248a7e27
  - id: c5f60233-d5ea-4453-a799-0ad258b4d399
  - id: e2290edd-b061-4880-9d79-dee306cf5aa9
  - id: ea90ebee-5c84-42d9-8b21-006bdabc95a3
  - id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 923
ht-degree: 2%

---

# Infrastructure

La réussite de la délivrabilité repose sur une base solide. L’infrastructure de messagerie est un élément essentiel. Une infrastructure de messagerie correctement construite comprend plusieurs composants, à savoir un ou plusieurs domaines et une ou plusieurs adresses IP. Ces composants sont comme la machine derrière les e-mails que vous envoyez et ils sont souvent le point d&#39;ancrage de la réputation d&#39;envoi. Les consultants en délivrabilité s’assurent que ces éléments sont correctement configurés lors de la mise en œuvre. Toutefois, en raison de l’élément « réputation », il est important que vous ayez cette compréhension de base.

## Configuration et stratégie du domaine {#domain-setup-and-strategy}

Les temps ont changé et certains FAI (comme Gmail et Yahoo) intègrent désormais la réputation de domaine comme point supplémentaire lorsqu&#39;il s&#39;agit de joindre la réputation d&#39;un email à un expéditeur. La réputation de votre domaine repose sur votre domaine d’envoi et non sur votre adresse IP. Cela signifie que votre marque est prioritaire en ce qui concerne les décisions de filtrage des FAI.

Une partie du processus d&#39;intégration des nouveaux expéditeurs sur les plateformes Adobe comprend la configuration de vos domaines d&#39;envoi et l&#39;assurance que votre infrastructure est correctement établie. Vous devez travailler avec un expert sur les domaines que vous prévoyez d’utiliser à long terme. Voici quelques conseils pour définir une bonne stratégie de domaine :

* Soyez aussi clair et représentatif de la marque que possible avec le domaine que vous choisissez afin que les utilisateurs n&#39;identifient pas incorrectement l&#39;e-mail comme spam. Voici quelques exemples : newsletter.foo.com, receipts.foo.com, etc.
* Vous ne devez pas utiliser votre domaine parent ou d’entreprise, car cela pourrait avoir un impact sur la diffusion du courrier de votre organisation vers les FAI.
* Envisagez d’utiliser un sous-domaine de votre domaine parent pour légitimer votre domaine d’envoi.
* Séparez les sous-domaines pour les catégories de messages transactionnels et marketing. Cela permet d&#39;améliorer la fiabilité du flux de trafic de messagerie, car les FAI recherchent cette méthode d&#39;envoi. Il s&#39;agit d&#39;une bonne pratique de messagerie connue qui est vivement recommandée.

## Stratégie IP {#ip-strategy}

Il est important d&#39;élaborer une stratégie de PI bien structurée pour contribuer à établir une réputation positive. Le nombre d’adresses IP et la configuration varient en fonction de votre modèle commercial et de vos objectifs marketing. Collaborez avec un expert afin d&#39;élaborer une stratégie claire pour bien démarrer. Tenez compte des points suivants qu’il est important de noter :

* **Trop d&#39;adresses IP** peut entraîner des problèmes de réputation, car il s&#39;agit d&#39;une tactique courante des spammeurs pour **raquette**, qui est une tactique utilisée par les spammeurs où le trafic est réparti sur de nombreuses adresses IP afin de maximiser la diffusion du spam. Même si vous n&#39;êtes pas un spammeur, vous pouvez ressembler à l&#39;un d&#39;eux si vous utilisez trop d&#39;adresses IP, en particulier si ces adresses IP n&#39;ont pas eu de trafic antérieur.
* **Un nombre trop faible d’adresses IP** peut entraîner des problèmes de débit et potentiellement des problèmes de réputation. Le débit varie selon le FAI. Le montant et la rapidité qu&#39;un FAI est prêt à accepter dépendent généralement de son infrastructure et des seuils de réputation d&#39;envoi.
* La séparation du trafic pour les types de message est essentielle. Il est important de séparer au minimum le courrier marketing et transactionnel sur des pools d&#39;adresses IP distincts.
* En fonction de votre stratégie de messagerie, il peut également être conseillé de séparer différents produits ou flux marketing sur différents pools d&#39;adresses IP si votre réputation est radicalement différente. Certains professionnels du marketing segmentent également par région. La séparation des adresses IP pour le trafic de réputation inférieure ne permet pas de résoudre le problème de réputation. En revanche, cette séparation évite les problèmes liés à la « bonne » réputation des diffusions par e-mail. Après tout, vous ne voulez pas sacrifier votre bon public pour un public plus risqué.

## Boucles de retours {#feedback-loops}

En coulisse, les plateformes Adobe traitent les données concernant les bounces, les plaintes, les désabonnements, etc. La configuration de ces boucles de commentaires est un aspect important de la délivrabilité. Les plaintes peuvent nuire à une réputation. Vous devriez donc utiliser des adresses e-mail qui enregistrent les plaintes de votre audience cible. Il est important de noter que Gmail ne renvoie pas ces données. Les en-têtes de désabonnement des listes et le filtrage des engagements sont particulièrement importants pour les abonnés Gmail, qui constituent désormais la majorité des bases de données d’abonnés.

## Authentification {#authentication}

L’authentification est le processus utilisé par les FAI pour valider l’identité d’un expéditeur. Les deux protocoles d’authentification les plus courants sont [!DNL Sender Policy Framework] (SPF) et [!DNL DomainKeys Identified Mail] (DKIM). Ils ne sont pas visibles par l’utilisateur final, mais ils aident les FAI à filtrer les e-mails provenant d’expéditeurs vérifiés. [!DNL Domain-based Message Authentication Reporting and Conformance] (DMARC) gagne en popularité, bien que ses politiques ne soient pas encore intégrées par tous les FAI dans leurs systèmes de réputation.

### SPF

[!DNL Sender Policy Framework] (SPF) est une méthode d’authentification qui permet au propriétaire d’un domaine de spécifier les serveurs de messagerie qu’il utilise pour envoyer des e-mails à partir de ce domaine.

### DKIM

[!DNL Domain Keys Identified Mail] (DKIM) est une méthode d’authentification utilisée pour détecter les adresses d’expéditeur falsifiées (usurpation d’adresse). Si DKIM est activé, il permet au destinataire de confirmer si l’expéditeur est autorisé à envoyer du courrier depuis ce domaine.

### DMARC

[!DNL Domain-based Message Authentication, Reporting and Conformance] (DMARC) est une méthode d’authentification qui permet aux propriétaires de domaine de protéger leur domaine contre une utilisation non autorisée. DMARC utilise SPF ou DKIM, ou les deux, pour permettre à un propriétaire de domaine de contrôler ce qui arrive aux e-mails dont l’authentification échoue : envoyés, mis en quarantaine ou rejetés.

## Ressources spécifiques au produit

**Campagne**

* Découvrez comment déléguer entièrement un sous-domaine à Adobe Campaign Classic ou à Standard dans [cette section](/help/additional-resources/ac-domain-name-setup.md).
* [Panneau de Contrôle : délégation complète de sous-domaine (tutoriel)](https://experienceleague.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html) - *Découvrez comment déléguer entièrement un sous-domaine à Adobe Campaign Classic.*
* [Panneau de Contrôle : délégation complète de sous-domaine (tutoriel)](https://experienceleague.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html) - *Découvrez comment déléguer entièrement un sous-domaine à Adobe Campaign Standard.*
* Pour en savoir plus sur l’implémentation d’une feedback loop pour une instance Campaign Classic, consultez [cette section](/help/additional-resources/acc-technical-recommendations.md#feedback-loop-acc).

## Ressources supplémentaires

* En savoir plus sur les méthodes d’authentification SPF, DKIM et DMARC dans [cette section](/help/additional-resources/authentication.md).
* Pour en savoir plus sur l’amélioration de la réputation des e-mails avec le réchauffement des adresses IP, consultez [cette section](/help/additional-resources/increase-reputation-with-ip-warming.md).
