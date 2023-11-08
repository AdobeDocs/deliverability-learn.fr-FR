---
title: Conseils relatifs aux modifications annoncées sur [!DNL Google] et [!DNL Yahoo]
description: Conseils relatifs aux modifications annoncées sur [!DNL Google] et [!DNL Yahoo]
role: Admin
level: Experienced
doc-type: Article
last-substantial-update: 2023-11-06T00:00:00Z
jira: KT-14320
thumbnail: KT-14320.jpeg
source-git-commit: 00b4b4c3396fc4a71484cd12e8c89cd8371ad1ce
workflow-type: tm+mt
source-wordcount: '1297'
ht-degree: 0%

---


# Conseils relatifs aux modifications annoncées sur [!DNL Google] et [!DNL Yahoo]

Le 3 octobre, les deux [!DNL Google] et [!DNL Yahoo] ont annoncé conjointement les changements prévus sur leurs blogs. Ces modifications ont pour but de préserver la sécurité de leurs utilisateurs et de fournir une meilleure expérience par e-mail en appliquant certaines bonnes pratiques courantes du secteur en tant que nouvelles exigences à compter de février 2024.

[https://blog.google/products/gmail/gmail-security-authentication-spam-protection/](https://blog.google/products/gmail/gmail-security-authentication-spam-protection/){target="_blank"}

![[!DNL Google] Annonce](/help/assets/Gmail.png)

[https://blog.postmaster.yahooinc.com/post/730172167494483968/more-secure-less-spam](https://blog.postmaster.yahooinc.com/post/730172167494483968/more-secure-less-spam){target="_blank"}

![[!DNL Yahoo] Annonce](/help/assets/Yahoo.png)

Les experts en délivrabilité des emails d’Adobe ont lu ces billets de blog et toute la documentation liée afin que vous n’ayez pas à le faire. Voici les points à retenir.

## Alors, qu&#39;est-ce que c&#39;est exactement ? [!DNL Google] et [!DNL Yahoo] à faire ?

Dans le domaine des emails, il existe des exigences légales, des exigences pratiques et des bonnes pratiques générales. Les exigences légales varient considérablement d’un lieu à l’autre et ne font pas partie de ce sujet. Au lieu de cela, [!DNL Google] et [!DNL Yahoo] prennent les bonnes pratiques et les transforment en exigences pratiques. Aucun des éléments [!DNL Google] et [!DNL Yahoo] Les mesures qui vont être prises en février sont nouvelles et ont souvent été recommandées pendant des années, mais leur adoption a été lente et inégale dans l&#39;industrie. Ceci est [!DNL Google] et [!DNL Yahoo]Pour faciliter l’avancement de ce processus d’adoption, utilisez la méthode suivante : &quot;Si vous souhaitez déployer des emails vers vos utilisateurs (cela peut représenter une partie importante de votre liste d’emails, dans certains cas jusqu’à 70 %, selon la région et l’industrie), vous devez effectuer ces tâches.&quot;

## Quels sont les détails ?

Si vous êtes un client Adobe, la plupart de ce qu’il nécessite fait déjà partie de votre configuration, mais il existe quelques éléments clés techniquement facultatifs. Vous voudrez être certain que votre organisation a adopté et configuré correctement ces éléments avant février 2024.

## DMARC:

[!DNL Google] et [!DNL Yahoo] Vous devez disposer d’un enregistrement DMARC pour tout domaine que vous utilisez pour leur envoyer des emails. Ils ne requièrent PAS actuellement de paramètre p=rejets ou p=quarantine. Par conséquent, un paramètre p=none, communément appelé paramètre &quot;monitoring&quot;, est parfaitement acceptable. Cela ne modifie pas le mode de traitement de vos emails, mais fait ce qu’ils feraient normalement sans DMARC. La configuration de cette fonctionnalité est la première étape pour vous protéger avec DMARC. En plus du nouvel avantage de vous aider à envoyer des emails à [!DNL Google] et [!DNL Yahoo] il peut également vous aider à voir s’il existe des problèmes d’authentification n’importe où dans votre éco-système de messagerie.
DMARC est actuellement entièrement pris en charge dans Adobe, mais n’est pas obligatoire. Utilisez n’importe quel vérificateur DMARC gratuit pour voir si vous disposez de la configuration DMARC pour vos sous-domaines. Dans le cas contraire, contactez votre équipe d’assistance Adobe pour voir comment procéder au mieux pour obtenir cette configuration. Vous trouverez également plus d’informations sur DMARC et sur sa mise en oeuvre. [here](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/technotes/implement-dmarc.html?lang=fr){target="_blank"} for Adobe Campaign and Adobe Journey Optimizer Adobe or [here](https://experienceleague.adobe.com/docs/marketo/using/getting-started-with-marketo/setup/configure-protocols-for-marketo.html){target="_blank"} pour le Marketo Engage.

## 1-Click (List) Unsubscribe:

Ne paniquez pas. [!DNL Google] et [!DNL Yahoo] Il ne s’agit pas des liens de désabonnement dans le corps ou le pied de page de votre email sur lesquels un robot de sécurité peut cliquer, mais uniquement pour effectuer son travail ou par accident. Ce qu’elles signifient, c’est la fonctionnalité d’en-tête List-Unsubscribe pour les versions &quot;mailto&quot; ou &quot;http/URL&quot;. Il s’agit de la fonction de la fonction [!DNL Yahoo] et les interfaces utilisateur Gmail dans lesquelles les utilisateurs peuvent cliquer sur se désabonner. Gmail invite même les utilisateurs qui cliquent sur &quot;Signaler du spam&quot; à vérifier s&#39;ils ont eu l&#39;intention de se désabonner, ce qui peut réduire le nombre de plaintes reçues (plaintes qui nuisent à votre réputation) en les transformant plutôt en désabonnements (ce qui ne nuit pas à votre réputation).
Il est important de noter que [!DNL Google] et [!DNL Yahoo] font toutes deux référence à l’option &quot;http/URL&quot; du nom &quot;1-Click&quot;, et cela est intentionnel. Techniquement, l&#39;option &quot;http/URL&quot; d&#39;origine permet de rediriger les destinataires vers un site web. Ce n&#39;est pas l&#39;objectif principal de [!DNL Yahoo] et [!DNL Google], qui font toutes deux référence au RFC8058 mis à jour et qui se concentre sur le traitement du désabonnement via une demande de POST HTTPS au lieu d’un site web, ce qui le rend &quot;1-click&quot;.
Pour Marketo Engage, Adobe a déjà activé l’option &quot;mailto&quot; et ne prend actuellement pas en charge l’option &quot;http/URL&quot;. D&#39;autres mises à jour à venir.
Pour Adobe Campaign et Adobe Journey Optimizer Adobe, il est recommandé d’utiliser les options &quot;mailto&quot; et &quot;1-click&quot;.
Si vous avez besoin d’informations supplémentaires sur la mise en oeuvre du désabonnement à la liste, veuillez consulter Adobe Campaign Classic ici pour Adobe Campaign Standard, ici pour et ici pour Adobe Journey Optimizer, ou contacter l’équipe d’assistance clientèle d’Adobe à tout moment.
La nécessité d’en-têtes list-unsubscribe ne s’applique pas aux emails transactionnels. Notez que les messages déclenchés tels que Panier abandonné et les communications similaires non générées par l’abonné sont considérés comme du marketing par les fournisseurs de messagerie, tels que [!DNL Google] et [!DNL Yahoo] et ceux-ci auraient besoin de list-unsubscribe.

## Traitement Se désabonne dans les 2 jours :

Cela est une bonne pratique recommandée depuis un certain temps, car chaque email que vous déployez à une personne qui se désabonne génère généralement une plainte contre le spam, de sorte que plus tôt vous arrêtez de lui envoyer des emails, mieux c’est. Encore une fois, les exigences légales peuvent être beaucoup plus longues dans certains cas, mais [!DNL Google] et [!DNL Yahoo] sauront que l&#39;utilisateur s&#39;est désabonné via List-Unsubscribe et que vous lui envoyez toujours un email le jour 3, et qu&#39;ils ont déclaré qu&#39;ils n&#39;autoriseront pas les expéditeurs qui le font à continuer à envoyer des emails à N&#39;IMPORTE QUEL de leurs utilisateurs.
Cette exigence de deux jours est valable pour tout désabonnement par le biais des différentes méthodes list-unsubscribe. Dans certains cas (comme &quot;mailto&quot;), cela signifie que l’Adobe les traitera. Adobe traite toutes les demandes de désabonnement immédiatement à la réception de la demande, bien dans un délai de 2 jours. Dans d’autres cas, vous pouvez les traiter. Si vous traitez ces demandes, vous devrez peut-être apporter des modifications de votre côté pour respecter ce délai de 2 jours.

## Taux de plaintes :

Le maintien d&#39;un faible taux de plaintes inférieur à 0,2 % constitue depuis longtemps une bonne pratique. [!DNL Google] La barre est plus élevée de 0,3 % sur une longue période, mais a clairement indiqué qu&#39;il y aurait des avantages à la maintenir en dessous de 0,1 %. Voici les détails qu&#39;ils ont partagés :
* Visez à maintenir votre taux de spam en dessous de 0,10 %.
* Évitez les spams à un taux de 0,30 % ou plus, en particulier pour toute période prolongée.
* Le maintien d’un faible taux de spam rend les expéditeurs plus résilients aux pics occasionnels de commentaires des utilisateurs.
* De même, le maintien d’un taux de spam élevé entraîne une classification accrue des spams. Il peut s’écouler un certain temps avant que les améliorations du taux de spam ne reflètent positivement la classification des spams.
  [!DNL Yahoo] a déclaré que leur seuil de plainte se situerait également dans la fourchette 0,30 %.
Si vous avez besoin d’aide pour surveiller vos taux de plaintes ou si vous souhaitez utiliser des stratégies pour réduire les plaintes, veuillez contacter votre conseiller en délivrabilité d’Adobe ou parler avec votre équipe de compte de l’ajout d’un conseiller en délivrabilité si vous n’en avez pas déjà un.

## Quel impact cela aura-t-il pour moi en tant que marketeur ?

ne pas respecter ces nouvelles exigences de Gmail et [!DNL Yahoo] est susceptible d’entraîner l’entrée ou le blocage des emails dans le dossier spam (c’est-à-dire, un rebond de la part du MBP indiquant que l’email n’a pas été diffusé).
Par conséquent, Adobe vous recommande vivement de passer en revue les modifications décrites ci-dessus et de vous assurer que vous commencez à les respecter dès que possible. C’est également le moment idéal pour commencer à évaluer vos performances à [!DNL Yahoo] et [!DNL Google] pour vous permettre de voir si des changements significatifs ont été apportés à vos mesures au mois de février.
Nous sommes là pour vous aider. Si vous avez des questions ou avez besoin d’aide, contactez votre conseiller en délivrabilité d’Adobe ou contactez votre équipe chargée du compte pour l’ajout d’un conseiller en délivrabilité si vous n’en avez pas déjà un.

## Y a-t-il des moyens pour contourner ceci ?

Bien qu’il s’agisse toujours d’une question qui se pose, la réalité est que ces changements ont un sens pour les utilisateurs finaux de [!DNL Google] et [!DNL Yahoo]Plateformes de . Ils sont motivés par les attentes de ces utilisateurs pour faire appliquer ces règles. Nous ne vous recommandons pas d’essayer de contourner ces changements, mais plutôt de prendre du recul et de réfléchir à la façon de les prendre en compte.
