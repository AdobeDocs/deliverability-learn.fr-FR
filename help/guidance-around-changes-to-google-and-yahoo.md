---
title: Conseils relatifs aux modifications annoncées sur  [!DNL Google]  et  [!DNL Yahoo]
description: Conseils relatifs aux modifications annoncées sur  [!DNL Google]  et  [!DNL Yahoo]
role: Admin
level: Experienced
doc-type: Article
last-substantial-update: 2023-11-06T00:00:00Z
jira: KT-14320
thumbnail: KT-14320.jpeg
source-git-commit: ce0ecaa7f62e8ba0bbf44dc180908b81475a225e
workflow-type: tm+mt
source-wordcount: '1312'
ht-degree: 76%

---


# Conseils relatifs aux modifications annoncées sur [!DNL Google] et [!DNL Yahoo]

Le 3 octobre, [!DNL Google] et [!DNL Yahoo] ont annoncé conjointement les changements prévus sur leurs blogs. Ces modifications ont pour but de préserver la sécurité de leurs utilisateurs et utilisatrices et de fournir une meilleure expérience par e-mail grâce à la mise en place, à compter de février 2024, de certaines bonnes pratiques courantes du secteur comme nouvelles conditions.

[https://blog.google/products/gmail/gmail-security-authentication-spam-protection/](https://blog.google/products/gmail/gmail-security-authentication-spam-protection/){target="_blank"}

![[!DNL Google] Annonce_](/help/assets/Gmail.png)

[https://blog.postmaster.yahooinc.com/post/730172167494483968/more-secure-less-spam](https://blog.postmaster.yahooinc.com/post/730172167494483968/more-secure-less-spam){target="_blank"}

![[!DNL Yahoo] Annonce](/help/assets/Yahoo.png)

Les experts en délivrabilité des emails d’Adobe ont lu ces billets de blog et toute la documentation liée pour que vous n’ayez pas à le faire. Voici les points à retenir.

## Alors, que font exactement [!DNL Google] et [!DNL Yahoo] ?

Dans le domaine des e-mails, il existe des exigences légales, des exigences pratiques et des bonnes pratiques générales. Les exigences légales varient considérablement d’un endroit à l’autre et ne font pas partie de ce sujet. Au lieu de cela, [!DNL Google] et [!DNL Yahoo] s’inspirent des bonnes pratiques pour les transformer en exigences pratiques. Aucun des éléments que [!DNL Google] et [!DNL Yahoo] vont commencer à exiger en février n’est nouveau. Ils ont souvent été recommandés pendant des années, mais leur adoption a été lente et inégale dans le secteur. Ceci est [!DNL Google] et [!DNL Yahoo]La manière dont nous vous aidons à progresser ce processus d’adoption consiste à dire &quot;Si vous souhaitez déployer des emails vers nos utilisateurs (cela peut représenter une partie importante de votre liste d’emails, dans certains cas jusqu’à 70 %, selon la région et l’industrie), vous devez effectuer ces tâches.&quot;

## Quels sont les détails ?

Si vous êtes une cliente ou un client Adobe, la plupart des eléments exigés font déjà partie de votre configuration, mais il y en a quelques éléments clés qui sont techniquement facultatifs. Vous devez vous assurer que votre organisation a adopté et configuré correctement ces éléments avant février 2024.

## DMARC :

[!DNL Google] et [!DNL Yahoo] exigeront que vous disposiez d’un enregistrement DMARC pour tout domaine que vous utilisez pour leur envoyer des e-mails. Ils ne requièrent PAS actuellement de paramètre p=rejets ou p=quarantine. Par conséquent, un paramètre p=none, communément appelé paramètre &quot;monitoring&quot;, est parfaitement acceptable. Cela ne modifie pas le mode de traitement de vos e-mails, ils feront ce qu’ils feraient normalement sans DMARC. La configuration de cette procédure est la première étape pour vous protéger avec DMARC. En plus du nouvel avantage de vous aider à envoyer des e-mails à [!DNL Google] et [!DNL Yahoo], elle peut également vous aider à voir s’il existe des problèmes d’authentification n’importe où dans votre éco-système de messagerie.
DMARC est actuellement entièrement pris en charge par Adobe, mais n’est pas obligatoire. Utilisez n’importe quel vérificateur DMARC gratuit pour voir si vous disposez de la configuration DMARC pour vos sous-domaines. Dans le cas contraire, contactez votre équipe d’assistance Adobe pour voir comment procéder au mieux pour obtenir cette configuration.

Vous trouverez également plus d’informations sur DMARC et sur son implémentation [ici](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/technotes/implement-dmarc.html?lang=fr){target="_blank"} for Adobe Campaign and Adobe Journey Optimizer Adobe or [here](https://experienceleague.adobe.com/docs/marketo/using/getting-started-with-marketo/setup/configure-protocols-for-marketo.html?lang=fr){target="_blank"} pour Marketo Engage.

## Sé désabonner en un clic (liste) :

Ne paniquez pas. [!DNL Google] et [!DNL Yahoo] ne font pas allusion aux liens de désabonnement dans le corps ou le pied de page de vos e-mails sur lesquels un robot de sécurité peut cliquer faisant son travail ou par accident. Ce qu’elles signifient, c’est la fonctionnalité d’en-tête List-Unsubscribe pour les versions &quot;mailto&quot; ou &quot;http/URL&quot;. Il s’agit de la fonction dans les interfaces utilisateur [!DNL Yahoo] et Gmail où les utilisateurs et utilisatrices peuvent cliquer sur Se désabonner. Gmail invite même les utilisateurs qui cliquent sur &quot;Signaler du spam&quot; à vérifier s&#39;ils ont eu l&#39;intention de se désabonner, ce qui peut réduire le nombre de plaintes reçues (plaintes qui nuisent à votre réputation) en les transformant plutôt en désabonnements (ce qui ne nuit pas à votre réputation).
Il est important de noter que [!DNL Google] et [!DNL Yahoo] font toutes deux référence à l’option &quot;http/URL&quot; du nom &quot;1-Click&quot;, et cela est intentionnel. Techniquement, l&#39;option &quot;http/URL&quot; d&#39;origine permet de rediriger les destinataires vers un site web. Ce n&#39;est pas l&#39;objectif principal de [!DNL Yahoo] et [!DNL Google], qui font toutes deux référence au RFC8058 mis à jour et qui se concentre sur le traitement du désabonnement via une demande de POST HTTPS au lieu d’un site web, ce qui le rend &quot;1-click&quot;.
Pour Marketo Engage, Adobe a déjà activé l’option &quot;mailto&quot; et ne prend actuellement pas en charge l’option &quot;http/URL&quot;. D’autres mises à jour à venir.
Pour Adobe Campaign et Adobe Journey Optimizer Adobe, il est recommandé d’utiliser les options &quot;mailto&quot; et &quot;1-click&quot;.

Si vous avez besoin d’informations supplémentaires sur l’implémentation de list-unsubscribe, rendez-vous [ici](https://experienceleague.adobe.com/docs/deliverability-learn/deliverability-best-practice-guide/additional-resources/campaign/acc-technical-recommendations.html?lang=fr#list-unsubscribe){target="_blank"} for **[!DNL Adobe Campaign Classic]**, [here](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-14778.html?lang=fr){target="_blank"}, or **[!DNL Adobe Campaign Standard]**, and [here](https://experienceleague.adobe.com/docs/journey-optimizer/using/email/email-opt-out.html?lang=fr){target="_blank"} pour ou contactez l’équipe d’assistance clientèle d’Adobe à tout moment.
**[!DNL Adobe Journey Optimizer]**

La nécessité d’en-têtes list-unsubscribe ne s’applique pas aux e-mails transactionnels. Notez que les messages déclenchés tels que Panier abandonné et les communications similaires non générées par les personnes abonnées sont considérés comme du marketing par les fournisseurs de messagerie, tels que [!DNL Google] et [!DNL Yahoo], et ceux-ci auraient besoin de list-unsubscribe.

## Traitement des désabonnements dans les 2 jours :

Il s’agit d’une bonne pratique recommandée depuis un certain temps, car chaque e-mail que vous déployez à une personne qui se désabonne entraîne généralement une réclamation pour spam. Plus tôt vous arrêterez de lui envoyer des e-mails, mieux c’est. Encore une fois, les exigences légales peuvent être beaucoup plus longues dans certains cas, mais [!DNL Google] et [!DNL Yahoo] sauront que leur utilisateur ou utilisatrice a choisi de se désabonner via List-Unsubscribe et que vous continuez à envoyer à cette personne un e-mail le troisième jour. Ils ont déclaré qu’ils n’autoriseraient pas les expéditeurs et expéditrices qui le font à continuer à envoyer des e-mails à L’ENSEMBLE de leurs utilisateurs et utilisatrices.
Cette exigence de deux jours est valable pour tout désabonnement par le biais des différentes méthodes list-unsubscribe. Dans certains cas (comme &quot;mailto&quot;), cela signifie que l’Adobe les traitera. Adobe traite toutes les demandes de désabonnement dès leur réception, bien avant le délai de 2 jours. Dans d’autres cas, vous pouvez les traiter. Si vous traitez ces demandes, vous devrez peut-être apporter des modifications de votre côté pour respecter ce délai de 2 jours.

## Taux de réclamations :

Le maintien d’un taux de réclamations inférieur à 0,2 % constitue depuis longtemps une bonne pratique. [!DNL Google] place la barre plus haut, à 0,3 %, sur une longue période, mais a clairement indiqué qu’il y avait des avantages à la maintenir en dessous de 0,1 %. Voici les détails qui ont été partagés :

* Visez à maintenir votre taux de spam en dessous de 0,10 %.
* Évitez un taux de spam de 0,30 % ou plus, en particulier sur une période prolongée.
* Le maintien d’un faible taux de spam permet aux expéditeurs et expéditrices de mieux faire face aux pics occasionnels de commentaires des utilisateurs et utilisatrices.
* De même, le maintien d’un taux de spam élevé entraîne une meilleure classification des spams. Il peut s’écouler un certain temps avant que les améliorations du taux de spam ne reflètent positivement la classification des spams.
  [!DNL Yahoo] a déclaré que son seuil de réclamation serait également de l’ordre de 0,30 %.


Si vous avez besoin d’aide pour surveiller vos taux de réclamations ou si vous souhaitez utiliser des stratégies pour réduire les réclamations, contactez votre conseiller ou conseillère en délivrabilité d’Adobe ou l’équipe chargée de votre compte pour bénéficier d’un conseiller ou d’une conseillère en délivrabilité.

## Quel impact cela aura-t-il sur moi en tant que spécialiste du marketing ?

Ne pas respecter ces nouvelles exigences de Gmail et [!DNL Yahoo] est susceptible d’entraîner l’arrivée des e-mails dans le dossier spam ou leur blocage (c’est-à-dire, un rebond de la part du fournisseur de service de messagerie indiquant que l’e-mail n’a pas été diffusé).
Par conséquent, Adobe vous recommande vivement de passer en revue les modifications décrites ci-dessus et de vous assurer que vous commencez à les respecter dès que possible. C’est également le moment idéal pour commencer à évaluer vos performances sur [!DNL Yahoo] et [!DNL Google] pour vous permettre de voir s’il y a des changements significatifs dans vos mesures en février.
Nous sommes là pour vous aider. Si vous avez des questions ou que vous avez besoin d’aide, contactez votre conseiller ou conseillère en délivrabilité Adobe ou l’équipe chargée de votre compte pour bénéficier d’un conseiller ou d’une conseillère en délivrabilité.

## Y a-t-il des moyens pour contourner ces changements ?

Bien qu’il s’agisse toujours d’une question qui se pose, la réalité est que ces changements ont un sens pour les utilisateurs finaux de [!DNL Google] et [!DNL Yahoo]Plateformes de . Ils sont motivés par les attentes de ces utilisateurs pour faire appliquer ces règles. Nous ne vous recommandons pas d’essayer de contourner ces changements, mais plutôt de prendre du recul et de réfléchir à la façon de les prendre en compte.
