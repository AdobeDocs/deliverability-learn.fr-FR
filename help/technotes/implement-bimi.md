---
title: Mise en oeuvre des indicateurs de marque de Gmail pour l’identification des messages (BIMI)
description: Découvrez comment implémenter BIMI
topics: Deliverability
exl-id: 6b911bcc-a531-466a-8bd3-7fa469b96cc7
source-git-commit: a4d2a75e85f37f48aa3246707b98e473682e13f6
workflow-type: tm+mt
source-wordcount: '686'
ht-degree: 0%

---

# Mise en oeuvre de Gmail [!DNL Brand Indicators for Message Identification] (BIMI)

Gmail a récemment annoncé qu&#39;ils seraient [déploiement du soutien général de BIMI](https://cloud.google.com/blog/products/identity-security/bringing-bimi-to-gmail-in-google-workspace). Vous devrez traiter un certain nombre d’éléments avant de pouvoir en profiter, notamment : Certificats de marque vérifiés, logos marqués, logos correctement formatés, configuration DMARC, et enfin publication d’un enregistrement BIMI sur votre DNS. Nous passerons en revue toutes ces étapes dans cet article.

[!DNL Brand Indicators for Message Identification] (BIMI) est une norme du secteur qui permet l’affichage d’un logo approuvé en regard de l’adresse électronique d’un expéditeur sur les plateformes participantes. Non seulement cet oeil accroche peut-être l&#39;engagement, mais il aide aussi à confirmer l&#39;authenticité de l&#39;expéditeur en réduisant le risque de phishing et d&#39;autres tactiques d&#39;espionnage.

## Certificat de marque vérifié

L’un des composants clés du programme BIMI de Gmail est l’obligation pour les expéditeurs de disposer d’un certificat de marque vérifié (VMC) émis par une autorité de certification valide. Actuellement, ces VMC ne sont disponibles que depuis Entrust et DigiCert, mais cette liste de fournisseurs va probablement s’allonger à la suite de l’annonce de Gmail.

Les VMC ressembleront d’une certaine manière aux certificats SSL. Vous aurez besoin d’un VMC pour chaque logo que vous souhaitez afficher. Par conséquent, si vous disposez de nombreuses marques, vous devriez prévoir la nécessité de plusieurs VMC. Chaque VMC peut être valide sur plusieurs domaines si vous obtenez un VMC multi-SAN. Ainsi, si vous souhaitez qu’un logo s’affiche sur plusieurs domaines d’envoi, il vous suffit d’un seul VMC.

## Logo Marque

Avant de pouvoir obtenir votre VMC, une autre étape clé doit être effectuée. Pour obtenir un VMC, le logo que vous souhaitez afficher doit être enregistré auprès de l’un des 8 bureaux mondiaux de marques et de brevets approuvés.

* Office des brevets et des marques des États-Unis (USPTO)
* Bureau de la propriété intellectuelle du Canada
* Office de la propriété intellectuelle de l&#39;Union européenne
* Office de la propriété intellectuelle du Royaume-Uni
* Deutsches Brevets - und Markenamt
* Office des marques du Japon
* Office espagnol des brevets et des marques
* IP Australia

Si le logo que vous souhaitez afficher n’est pas enregistré ou n’est pas enregistré auprès de l’une de ces 8 organisations, vous devrez collaborer avec votre équipe juridique pour résoudre ce problème avant de demander le service VMC.

## Logo Image Format

Cela serait également un bon moment pour vous assurer que votre logo répondra aux exigences de format du logo BIMI.

Il doit être au format SVG et se conformer au profil SVG Portable/Secure (SVG-P/S) . Vous trouverez des conseils pour ce faire dans la section [Groupe de travail BIMI](https://bimigroup.org/svg-conversion-tools-released).

## DMARC

Une fois que votre logo Marqué est correctement formaté et que votre certificat Marque Vérifié est correctement mis en forme, vous devez également vous assurer que DMARC est entièrement configuré sur tout domaine d’envoi pour lequel vous souhaitez que BIMI fonctionne.

Cela implique de s’assurer que le paramètre P= est défini sur Quarantaine ou Rejeter. Si votre DMARC utilise P=None, il ne sera pas admissible pour l’IMI. Le paramètre P=Aucun est vivement recommandé pour vous assurer que vous savez quel courrier provient d’un domaine et que rien ne serait accidentellement bloqué si vous passez à &quot;Quarantaine&quot; ou &quot;Rejeter&quot;, pensez-le comme étant la phase de test et de collecte des informations. Vous devrez toutefois passer à l’application avant que l’IMI ne vous soit accessible.

## Entrée DNS

Alors que tout le reste est enfin aligné et prêt à l&#39;emploi, il est temps de mettre à jour l&#39;entrée DNS avec votre BIMI.

Voici une entrée simple qui doit ressembler à ceci :

```
default._bimi.[domain] IN TXT “v=BIMI1; l=[SVG URL] 
```

Vous pouvez obtenir des informations détaillées sur cette entrée et même utiliser un vérificateur BIMI gratuit à l’adresse [Site du groupe de travail BIMI](https://bimigroup.org/implementation-guide).


## Principales mesures à prendre

Si vous êtes un [!DNL Adobe Campaign] Pour le client Marketo, Adobe peut vous aider à créer la mise à jour DNS BIMI : contactez l’assistance clientèle d’Adobe pour en demander une. Adobe peut également vous aider à résoudre les problèmes si BIMI ne fonctionne pas correctement.

Pour obtenir de l’aide sur les marques ou les certificats de marque vérifiés, travaillez avec votre équipe juridique et un fournisseur VMC autorisé.

L’obtention de la configuration BIMI pour Gmail n’est peut-être pas un processus rapide, mais il peut présenter des avantages significatifs du point de vue de Marketing et de la sécurité.
