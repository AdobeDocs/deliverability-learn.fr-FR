---
title: Mise en oeuvre des indicateurs de marque de Gmail pour l’identification des messages (BIMI)
description: Découvrez comment implémenter BIMI
topics: Deliverability
role: Admin
level: Beginner
exl-id: f1c14b10-6191-4202-9825-23f948714f1e
source-git-commit: 2a78db97a46150237629eef32086919cacf4998c
workflow-type: tm+mt
source-wordcount: '1284'
ht-degree: 17%

---

# Mise en oeuvre de [!DNL Domain-based Message Authentication, Reporting and Conformance] (DMARC)

Ce document a pour but de fournir au lecteur des informations supplémentaires sur la méthode d’authentification par email, DMARC. En expliquant le fonctionnement de DMARC et ses différentes options politiques, les lecteurs comprendront mieux l’impact de DMARC sur la délivrabilité des emails.

## Qu’est-ce que DMARC ? {#about}

Authentification, création de rapports et conformité des messages basés sur un domaine, est une méthode d’authentification par email qui permet aux propriétaires de domaine de protéger leur domaine d’une utilisation non autorisée. DMARC fournit également des commentaires sur le statut d’authentification des e-mails et permet aux expéditeurs et expéditrices de contrôler ce qui arrive aux e-mails qui ne parviennent pas à s’authentifier. Cela inclut des options de surveillance, de mise en quarantaine ou de rejet du courrier, selon la politique DMARC mise en œuvre.

DMARC propose trois options de politique :

* **Monitor (p=none):** Indique au fournisseur de messagerie/FAI de faire tout ce qu’il ferait normalement au message.
* **Quarantaine (p=quarantaine) :** Indique au fournisseur de messagerie/FAI de diffuser du courrier électronique qui ne transmet pas DMARC au dossier spam ou courrier indésirable du destinataire.
* **Rejeter (p=Rejeter) :** Indique au fournisseur de messagerie/FAI de bloquer les courriers qui ne transmettent pas DMARC, ce qui entraîne un rebond.

## Comment DMARC fonctionne-t-il ? {#how}

SPF et DKIM sont tous deux utilisés pour associer un e-mail à un domaine et permettent d’authentifier les e-mails. DMARC va plus loin et contribue à empêcher les usurpations en faisant correspondre le domaine vérifié par DKIM et SPF. Pour passer DMARC, un message doit passer SPF ou DKIM. Si l’authentification des deux échoue, DMARC échoue et l’e-mail est envoyé conformément à la politique DMARC que vous avez sélectionnée.

>[!NOTE]
>
>DMARC nécessite un alignement entre l’adresse &quot;De&quot; et l’adresse &quot;Return-Path&quot;.

## Pourquoi mettre en oeuvre DMARC ? {#why}

DMARC est facultatif. Bien qu’il ne soit pas obligatoire, il est gratuit et permet aux destinataires d’emails d’identifier facilement l’authentification des emails, ce qui peut améliorer la diffusion. L’un des principaux avantages de DMARC est qu’il offre un reporting sur les messages qui échouent SPF et/ou DKIM. Il donne également aux expéditeurs un certain contrôle sur ce qui se passe avec les courriers qui ne transmettent aucune de ces méthodes d’authentification. Grâce aux rapports DMARC, les expéditeurs peuvent déterminer quels messages échouent DMARC, ce qui leur permet de prendre des mesures pour limiter d’autres erreurs.

>[!NOTE]
>
>Si vous souhaitez mettre en oeuvre BIMI, une stratégie DMARC p=quarantaine ou p=rejeter est requise.

## Bonnes pratiques relatives à la mise en oeuvre de DMARC {#best-practice}

Comme DMARC est facultatif, il ne sera configuré par défaut sur aucune plateforme ESP. Un enregistrement DMARC doit être créé dans DNS pour votre domaine pour qu’il fonctionne. De plus, une adresse électronique de votre choix est requise pour indiquer où les rapports DMARC doivent se rendre au sein de votre organisation. La bonne pratique consiste à
Il est recommandé de déployer lentement l’implémentation DMARC en réaffectant votre stratégie DMARC de p=none à p=quarantine, puis de p=reject lorsque vous acquérez une compréhension DMARC de l’impact potentiel de DMARC.

1. Analysez les commentaires que vous recevez et utilisez (p=none), qui indique au destinataire d’effectuer aucune action contre les messages qui ne parviennent pas à s’authentifier, tout en envoyant des rapports par e-mail à l’expéditeur. En outre, examinez les problèmes liés à SPF/DKIM et corrigez-les si des messages légitimes échouent à l’authentification.
1. Déterminez si SPF et DKIM sont harmonisés et passent une authentification pour tous les emails légitimes, puis déplacez la stratégie vers (p=quarantine), ce qui indique au serveur de messagerie de réception de mettre en quarantaine les emails qui ne parviennent pas à s’authentifier (cela signifie généralement placer ces messages dans le dossier spam).
1. Ajustez la stratégie à (p=rejets). La politique p=reject indique à la personne destinataire de refuser complètement (rebond) tout e-mail pour le domaine qui ne réussit pas l’authentification. Lorsque cette politique est activée, seul un e-mail qui est vérifié comme étant authentifié à 100 % par votre domaine aura une chance d’être placé en boîte de réception.

   >[!NOTE]
   >
   >Utilisez cette politique avec précaution et déterminez si elle convient à votre entreprise.

## Création de rapports DMARC {#reporting}

DMARC permet de recevoir des rapports sur les emails qui échouent SPF/DKIM. Il existe deux rapports différents générés par les services de FAI dans le cadre du processus d’authentification que les expéditeurs peuvent recevoir par le biais des balises RUA/RUF dans leur stratégie DMARC :

* **Rapports agrégés (RUA) :** Ne contient aucune information d’identification personnelle qui serait sensible au RGPD.
* **Rapports médico-légaux (RUF) :** contient des adresses électroniques sensibles au RGPD. Avant d’utiliser , il est préférable de vérifier en interne comment traiter les informations qui doivent être conformes au RGPD.

L’utilisation principale de ces rapports consiste à recevoir un aperçu des emails qui ont fait l’objet d’une tentative d’usurpation. Il s’agit de rapports hautement techniques qui sont le mieux digérés au moyen d’un outil tiers. Voici quelques entreprises spécialisées dans la surveillance DMARC :

* [ValiMail](https://www.valimail.com/products/#automated-delivery)
* [Agari](https://www.agari.com/)
* [Dmarcian](https://dmarcian.com/)
* [Proofpoint](https://www.proofpoint.com/us)

>[!CAUTION]
>
>Si les adresses e-mail que vous ajoutez pour recevoir des rapports se trouvent en dehors du domaine pour lequel l’enregistrement DMARC est créé, vous devez autoriser leur domaine externe à indiquer au DNS que vous possédez ce domaine. Pour ce faire, procédez comme décrit dans la section [Documentation dmarc.org](https://dmarc.org/2015/08/receiving-dmarc-reports-outside-your-domain).

### Exemple d’enregistrement DMARC {#example}

```
v=DMARC1; p=reject; fo=1; rua=mailto:dmarc_rua@emaildefense.proofpoint.com;ruf=mailto:dmarc_ruf@emaildefense.proofpoint.co
```

## Balises DMARC et ce qu’elles font {#tags}

Les enregistrements DMARC comportent plusieurs composants appelés balises DMARC. Chaque balise a une valeur qui spécifie un certain aspect de DMARC.

| Nom de balise | Obligatoire / Facultatif | Fonction | Exemple | Valeur par défaut |
|  ---  |  ---  |  ---  |  ---  |  ---  |
| v | Obligatoire | Cette balise DMARC spécifie la version. Il n’existe qu’une seule version à ce jour. Par conséquent, cette valeur sera fixe pour v=DMARC1 | V=DMARC1 DMARC1 | DMARC1 |
| p | Obligatoire | Affiche la stratégie DMARC sélectionnée et demande au destinataire de signaler, mettre en quarantaine ou rejeter le courrier qui ne réussit pas les vérifications d’authentification. | p=aucun, mise en quarantaine ou rejet | - |
| fo | Facultatif | Permet au propriétaire du domaine de spécifier des options de création de rapports. | 0 : Générer un rapport en cas d&#39;échec<br/>1 : générer un rapport en cas d&#39;échec<br/>d : générer un rapport en cas d&#39;échec de DKIM<br/>s : générer un rapport en cas d&#39;échec du SPF | 1 (recommandé pour les rapports DMARC) |
| pct | Facultatif | Indique le pourcentage de messages soumis au filtrage. | pct=20 | 100 |
| rua | Facultatif (recommandé) | Identifie l’emplacement où les rapports agrégés seront distribués. | `rua=mailto:aggrep@example.com` | - |
| ruf | Facultatif (recommandé) | Identifie l’endroit où les rapports médico-légaux seront remis. | `ruf=mailto:authfail@example.com` | - |
| sp | Facultatif | Spécifie la stratégie DMARC pour les sous-domaines du domaine parent. | sp=reject | - |
| adkim | Facultatif | Peut être Strict (s) ou Relaxé (r). Alignement décontracté signifie que le domaine utilisé dans la signature DKIM peut être un sous-domaine de l&#39;adresse &quot;De&quot;. Un alignement strict signifie que le domaine utilisé dans la signature DKIM doit correspondre exactement au domaine utilisé dans l’adresse de l’expéditeur. | adkim=r | r |
| aspf | Facultatif | Peut être Strict (s) ou Relaxé (r). Un alignement relâché signifie que le domaine ReturnPath peut être un sous-domaine de l’adresse de l’expéditeur. Un alignement strict signifie que le domaine Return-Path doit correspondre exactement à l’adresse From. | aspf=r | r |

## DMARC et Adobe Campaign {#campaign}

>[!NOTE]
>
>Si votre instance Campaign est hébergée sur AWS, vous pouvez implémenter DMARC pour vos sous-domaines avec le Panneau de Contrôle . [Découvrez comment implémenter des enregistrements DMARC à l’aide de Panneau de Contrôle](https://experienceleague.adobe.com/docs/control-panel/using/subdomains-and-certificates/txt-records/dmarc.html?lang=fr).

Une raison courante des échecs DMARC est le décalage entre l’adresse &quot;De&quot; et &quot;Erreurs à&quot; ou &quot;Chemin de retour&quot;. Pour éviter cela, lors de la configuration de DMARC, il est recommandé de vérifier deux fois les paramètres de vos adresses &quot;De&quot; et &quot;Erreurs-A&quot; dans vos modèles de diffusion.

1. Dans votre modèle de diffusion, vérifiez l’adresse actuellement définie comme votre adresse &quot;De&quot;.

   ![](../assets/dmarc1.png)

1. A partir de là, sélectionnez &quot;Propriétés&quot; qui vous permettra de modifier davantage votre modèle de diffusion. Dans cette fenêtre, sélectionnez SMTP et désélectionnez la case &quot;Utiliser l&#39;adresse d&#39;erreur par défaut définie pour la plateforme&quot; si cette option est sélectionnée. Dans Adobe Campaign, les modèles de diffusion cochent cette case par défaut. L’adresse d’erreur par défaut ne peut pas être l’adresse associée à l’adresse de l’expéditeur dans ce modèle de diffusion.

   ![](../assets/dmarc2.png)

1. Lorsque cette case est décochée, un champ de texte s’affiche. Il vous permet de saisir une adresse d’erreur unique qui utilise le même domaine que celui défini dans l’option Adresse de l’expéditeur.

   ![](../assets/dmarc3.png)

Une fois ces modifications enregistrées, vous pourrez passer à l’implémentation DMARC avec un alignement de domaine correct.

## Liens utiles {#links}

* [DMARC.org](https://dmarc.org/){target="_blank"}
* [Authentification par courrier électronique M3AAWG](https://www.m3aawg.org/sites/default/files/document/M3AAWG_Email_Authentication_Update-2015.pdf){target="_blank"}
