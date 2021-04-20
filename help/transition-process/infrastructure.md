---
title: Infrastructure
description: 'Découvrez ce qui est nécessaire pour construire correctement une infrastructure de messagerie. '
feature: Transition Process
topics: Deliverability
kt: 7052
thumbnail: kt7052.jpg
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 1e539b5df54250a5927701009e7a9c84e5d73fae
workflow-type: tm+mt
source-wordcount: '912'
ht-degree: 0%

---


# Infrastructure

Le succès de la livraison dépend d&#39;une base solide. L&#39;infrastructure de courriel est un élément essentiel. Une infrastructure de messagerie correctement construite comprend plusieurs composants, à savoir le ou les domaines et les adresses IP. Ces composants sont comme la machine derrière les courriels que vous envoyez et ils sont souvent le point d&#39;ancrage de l&#39;envoi de réputation. Les consultants en livrabilité s’assurent que ces éléments sont correctement configurés lors de l’implémentation, mais en raison de l’élément réputation, il est important pour vous d’avoir cette compréhension de base.

## Configuration et stratégie du domaine {#domain-setup-and-strategy}

Les temps ont changé, et certains FAI (comme Gmail et Yahoo) intègrent désormais la réputation de domaine en tant que point supplémentaire lorsqu&#39;il s&#39;agit d&#39;associer la réputation de courriel à un expéditeur. La réputation de votre domaine repose sur votre domaine d’envoi plutôt que sur votre adresse IP. Cela signifie que votre marque a la priorité en ce qui concerne les décisions de filtrage des fournisseurs de services Internet.

Une partie du processus d&#39;intégration des nouveaux expéditeurs sur les plateformes d&#39;Adobe consiste à configurer vos domaines d&#39;envoi et à veiller à ce que votre infrastructure soit correctement établie. Vous devez travailler avec un expert sur les domaines que vous prévoyez d’utiliser à long terme. Voici quelques conseils qui façonnent une bonne stratégie de domaine :

* Soyez aussi clair et réfléchi à la marque que possible avec le domaine que vous choisissez afin que les utilisateurs n’identifient pas incorrectement le courrier comme indésirable. Voici quelques exemples : newsletter.foo.com, Receiefoo.com, etc.
* Vous ne devriez pas utiliser votre domaine parent ou d’entreprise, car cela pourrait avoir un impact sur la diffusion du courrier de votre entreprise aux FAI.
* Envisagez d’utiliser un sous-domaine de votre domaine parent pour légitimer votre domaine d’envoi.
* Séparez vos sous-domaines pour les catégories de messages transactionnelles et marketing. Cela permettra à votre trafic de courrier électronique d’être plus fiable, car les FAI recherchent cette méthode d’envoi, qui est une pratique recommandée et qui est bien connue.

## Stratégie IP {#ip-strategy}

Il est important de former une stratégie de propriété intellectuelle bien structurée pour aider à établir une réputation positive. Le nombre d’adresses IP et de configurations varie en fonction de votre modèle d’entreprise et de vos objectifs marketing. Travailler avec un expert à l&#39;élaboration d&#39;une stratégie claire pour le début à droite. Considérez les points importants à noter :

* **Trop d&#39;** IPscan déclenchent des problèmes de réputation car il s&#39;agit d&#39;une tactique courante de spammers à la raquette **de** neige, une tactique utilisée par les spammeurs où le trafic est réparti sur de nombreuses IP pour maximiser la diffusion du spam. Même si vous n’êtes pas un spammeur, vous pouvez ressembler à un si vous utilisez trop d’IP, en particulier si ces IP n’ont pas eu de trafic antérieur.
* **Trop peu d&#39;** IPscan provoque des problèmes de débit et peut potentiellement déclencher des problèmes de réputation. Le débit varie en fonction du fournisseur de services Internet. Le montant et la rapidité d&#39;acceptation d&#39;un FAI dépendent généralement de son infrastructure et de l&#39;envoi de seuils de réputation.
* Il est essentiel de séparer le trafic des types de messagerie. Il est important, au minimum, de séparer le marketing et le courrier transactionnel dans des pools d&#39;adresses IP distincts.
* En fonction de votre stratégie de courrier, il peut également être conseillé de séparer différents produits ou flux marketing sur différents pools d’adresses IP si votre réputation est radicalement différente. Certains spécialistes du marketing segmentent également par région. La séparation de l’IP pour le trafic dont la réputation est inférieure ne corrige pas le problème de réputation, mais évite les problèmes liés à vos &quot;bonnes&quot; diffusions de messagerie de réputation. Après tout, vous ne voulez pas sacrifier votre bonne audience pour une  plus risquée.

## Boucles de commentaires {#feedback-loops}

En coulisses, les plateformes d&#39;Adobe traitent les données concernant les rebonds, les plaintes, les désabonnements, etc. La mise en place de ces boucles de rétroaction est un aspect important de la délivrabilité. Les plaintes peuvent porter atteinte à la réputation ; vous devez donc envoyer par courriel des adresses qui enregistrent les plaintes de votre audience de cible. Il est important de noter que Gmail ne fournit pas ces données. Les en-têtes de désabonnement de liste et le filtrage d&#39;engagement sont particulièrement importants pour les abonnés Gmail, qui constituent désormais la majorité des bases de données d&#39;abonnés.

## Authentification {#authentication}

L&#39;authentification est le processus que les FAI utilisent pour valider l&#39;identité d&#39;un expéditeur. Les deux protocoles d&#39;authentification les plus courants sont [!DNL Sender Policy Framework] (SPF) et [!DNL DomainKeys Identified Mail] (DKIM). Ils ne sont pas visibles pour l’utilisateur final mais aident les fournisseurs de services Internet à filtrer les courriers électroniques des expéditeurs vérifiés. [!DNL Domain-based Message Authentication Reporting and Conformance] (DMARC) gagne en popularité, bien que ses politiques ne soient pas encore intégrées par tous les FAI dans leurs systèmes de réputation.

### SPF

[!DNL Sender Policy Framework] (SPF) est une méthode d&#39;authentification qui permet au propriétaire d&#39;un domaine de spécifier les serveurs de messagerie qu&#39;il utilise pour envoyer du courrier à partir de ce domaine.

### DKIM

[!DNL Domain Keys Identified Mail] (DKIM) est une méthode d&#39;authentification utilisée pour détecter les adresses d&#39;expéditeur falsifiées (communément appelée usurpation). Si DKIM est activé, il permet au destinataire de confirmer si l&#39;expéditeur est autorisé à envoyer du courrier à partir de ce domaine.

### DMARC

[!DNL Domain-based Message Authentication, Reporting and Conformance] (DMARC) est une méthode d’authentification qui permet aux propriétaires de domaines de protéger leur domaine contre toute utilisation non autorisée. DMARC utilise SPF ou DKIM ou les deux pour permettre au propriétaire d’un domaine de contrôler ce qui se passe dans les messages dont l’authentification échoue : remis, mis en quarantaine ou rejeté.

## Ressources spécifiques au produit

**Campaign**

* Découvrez comment déléguer entièrement un sous-domaine à Adobe Campaign Classic ou Standard dans [cette section](/help/additional-resources/ac-domain-name-setup.md).
* [Panneau de Contrôle : Délégation de sous-domaine complète (didacticiel)](https://experienceleague.corp.adobe.com/docs/campaign-classic-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html)  -  *Découvrez comment déléguer complètement un sous-domaine à Adobe Campaign Classic.*
* [Panneau de Contrôle : Délégation de sous-domaine complète (didacticiel)](https://experienceleague.corp.adobe.com/docs/campaign-standard-learn/control-panel/subdomains-and-certificates/subdomain-delegation.html)  -  *Découvrez comment déléguer complètement un sous-domaine à Adobe Campaign Standard.*
* Pour en savoir plus sur l&#39;implémentation d&#39;une boucle de rétroaction pour une instance de Campaign Classic dans [cette section](/help/additional-resources/acc-technical-recommendations.md#feedback-loop-acc).

## Ressources supplémentaires

* Pour en savoir plus sur les méthodes d’authentification SPF, DKIM et DMARC, consultez [cette section](/help/additional-resources/authentication.md).
* Pour en savoir plus sur l&#39;augmentation de la réputation de votre courriel avec le réchauffement de la propriété intellectuelle, consultez [cette section](/help/additional-resources/increase-reputation-with-ip-warming.md).
