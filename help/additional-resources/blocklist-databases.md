---
title: Listes Blackhole en temps réel
description: Découvrez les organisations qui gèrent des listes d'adresses IP et de domaines susceptibles d'être utilisés par les spammeurs.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 4155b89f-a636-404c-8951-563c1b4d0289
source-git-commit: b859229410ca0199f9e9d57025a9fe022834a217
workflow-type: tm+mt
source-wordcount: '423'
ht-degree: 38%

---

# Listes Blackhole en temps réel

Plusieurs organisations gèrent des bases de données d&#39;adresses IP et de domaines réputés pour être utilisés par les spammeurs. Il peut être utile de consulter ces sites pour comprendre pourquoi certains messages ont été rejetés comme spam. Il est généralement possible de demander la suppression d&#39;une adresse ajoutée par erreur à ces listes.

Ces bases de données sont appelées RBL (Real-time Blackhole List) et leur consultation repose sur un mécanisme DNS. Il existe trois types de RBL :

* Par adresse IP : recense les adresses IP émettrices de spam ou susceptibles de relayer du spam.
* Par domaine d&#39;envoi : recense les domaines d&#39;envoi (domaine complet de l&#39;adresse de mails rebonds) émetteurs de spam ou présentant un défaut de configuration.
* Par domaine web : recense les domaines (domaines de haut niveau tels qu&#39;enregistrés auprès des registrars) trouvés dans les URL des liens et des images contenus dans les spams. Dans les solutions Adobe, le domaine à considérer est généralement l&#39;adresse utilisée pour le tracking.

La liste qui suit répertorie les listes RBL les plus utilisées. Pour obtenir une liste plus complète, consultez la page [https://www.dnsstuff.com/](https://tools.dnsstuff.com/).

* **Spamhaus**

  Consultez la page [https://www.spamhaus.org/](https://www.spamhaus.org/)

  La base de données est plus importante. Être classé sur cette liste est généralement une situation grave. Si cela se produit, vous devez agir IMMÉDIATEMENT et avertir les services commerciaux, les services chargés de la délivrabilité et l&#39;[Assistance clientèle d&#39;Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* **SpamCop**

  Consultez la page [https://www.spamcop.net/](https://www.spamcop.net/)

  C&#39;est l&#39;une des bases de données les plus réputées. Si l&#39;une de vos adresses IP est placée sur cette liste, cela signifie généralement que les utilisateurs de SpamCop ont déclaré vos messages comme étant du spam ou que vous avez envoyé des messages à un leurre de SpamCop.

* **URIBL**

  Consultez la page [https://www.uribl.com/](https://www.uribl.com/)

  Cette liste recense les domaines qui apparaissent régulièrement dans les messages déclarés en spam. Si votre domaine apparaît dans cette liste, cela peut affecter considérablement votre délivrabilité. Vous devez informer immédiatement les services chargés de la délivrabilité et l&#39;[Assistance clientèle d&#39;Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* **SURBL**

  Pour plus d&#39;informations, consultez la section [&#128279;](https://surbl.org/)

  SURBL identifie les sites web qui apparaissent régulièrement dans le spam. Si votre domaine apparaît dans cette liste, cela peut affecter considérablement votre délivrabilité. Vous devez informer immédiatement les services chargés de délivrabilité et l&#39;[Assistance clientèle d&#39;Adobe](https://helpx.adobe.com/fr/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html).

* **iX Manitu**

  Il s&#39;agit d&#39;une liste d&#39;adresses IP largement utilisée en Allemagne. Pour plus d&#39;informations, consultez la section [&#128279;](https://www.heise.de/ix/nixspam/)

<!--
* SORBS

  [https://www.nl.sorbs.net](https://www.nl.sorbs.net) compiles a list of IP addresses that are reputed to be dynamic IP address (i.e. attributed temporarily to ISP subscribers) or "open relay" addresses. Certain domains check whether the IP address of a sender is not listed on this site before accepting email. Checking the IP addresses on this site can prove useful.
-->
