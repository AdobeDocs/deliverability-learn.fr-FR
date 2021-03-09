---
title: Collecte d’adresses et croissance des listes
description: 'Découvrez quelles sont les meilleures sources pour les nouvelles adresses électroniques, comment garantir une qualité élevée des données et l''alignement sur les directives légales. '
feature: Audiences
topics: Deliverability
kt: 7063
thumbnail: kt7063.jpg
doc-type: article
activity: understand
team: TM
translation-type: tm+mt
source-git-commit: 5a15354aa88e34479f2a1ba37cf4dde239c17bd2
workflow-type: tm+mt
source-wordcount: '1598'
ht-degree: 0%

---


# Collecte d’adresses et croissance des listes

Les meilleures sources de nouvelles adresses électroniques sont les sources directes, telles que les abonnements sur votre site Web ou dans les magasins physiques. Dans ces situations, vous pouvez contrôler l’expérience pour vous assurer qu’elle est positive et que l’abonné souhaite recevoir des courriers électroniques de votre marque.

Quelques remarques sur ces méthodes d&#39;inscription :

**La collecte de** la liste de stockage physique peut poser des problèmes en raison des entrées d&#39;adresse verbale ou écrite qui provoquent une faute d&#39;orthographe dans les adresses. Il est recommandé d’envoyer un courriel de confirmation le plus rapidement possible après l’inscription en magasin.

La forme la plus courante d&#39;**inscription au site Web** est &quot;inclusion unique&quot;. Il s’agit de la norme minimale absolue que vous devez utiliser pour acquérir des adresses électroniques. La souscription unique est lorsque le titulaire d’une adresse électronique spécifique accorde à l’expéditeur l’autorisation de lui envoyer des courriels marketing, généralement en envoyant l’adresse via un formulaire Web ou des abonnements en magasin. Bien qu’il soit possible d’exécuter une campagne par courrier électronique réussie à l’aide de cette méthode, elle peut être la cause de certains problèmes.

* Les adresses électroniques non confirmées peuvent présenter des fautes de frappe ou être mal formées, incorrectes ou utilisées de manière malveillante. Les fautes de frappe et les adresses mal formées provoquent des taux de rebonds élevés, ce qui peut et provoque des blocages émis par les FAI ou une perte de réputation d&#39;IP.

* La soumission malveillante de pièges à spam connus (parfois appelé &quot;empoisonnement de liste&quot;) peut causer d&#39;énormes problèmes de diffusion et de réputation si le propriétaire de ce piège agit. Il est impossible de savoir si le destinataire souhaite vraiment être ajouté à une liste marketing sans confirmation. Il est donc tout aussi impossible de définir les attentes des destinataires et peut entraîner une augmentation des plaintes de spam, et parfois même une placée sur la liste bloquée si le courrier électronique collecté se révèle être un piège de spam.

Pour obtenir des conseils sur la façon de minimiser les problèmes présentés à la fois dans le magasin physique et dans la souscription unique, consultez la section [Qualité des données et hygiène](#data-quality-and-hygiene) de ce guide pour obtenir les détails et les avantages de la souscription au doublon.

>[!NOTE]
>
>Les abonnés utilisent souvent des adresses jetables, des adresses expirées ou des adresses qui ne sont pas les leurs pour obtenir ce qu’ils veulent d’un site Web, mais aussi pour éviter d’être ajoutés aux listes marketing. Dans ce cas, les listes des spécialistes du marketing se traduisent par un nombre élevé de rebonds durs, des taux élevés de plaintes de spam et des abonnés qui ne cliquent pas, n’ouvrent pas ou n’interagissent pas positivement avec les courriels. Cela peut être vu comme un drapeau rouge pour les fournisseurs de boîtes aux lettres et les FAI.

## Formulaires d&#39;inscription

Outre les champs des données, vous souhaitez collecter des informations sur vos nouveaux abonnés, ce qui peut encourager des connexions plus pertinentes avec vos clients, il y a quelques autres choses à faire avec votre formulaire d&#39;inscription sur le site Web.

* Configurez avec l&#39;abonné des attentes claires quant à la réception du courriel, ce qu&#39;il recevra et la fréquence à laquelle il le recevra.
* Ajoutez des options permettant à l&#39;abonné de sélectionner la fréquence ou le type de communications qu&#39;il reçoit. Ces options vous permettent de connaître les préférences de l’abonné à partir du début afin que vous puissiez offrir la meilleure expérience possible à votre nouveau client.
* Équilibrer le risque de perdre l’intérêt de l’abonné pendant le processus d’inscription en demandant autant d’informations que possible. Des choses comme leur anniversaire, leur emplacement ou leurs centres d’intérêt vous aident à envoyer du contenu plus personnalisé. Les abonnés de chaque marque ont des attentes et des seuils de tolérance différents. Les tests sont donc essentiels pour trouver le bon équilibre dans votre situation.

>[!NOTE]
>
> N’utilisez pas de cases pré-cochées pendant le processus d’inscription. Bien qu&#39;il puisse vous attirer des ennuis légalement, il s&#39;agit également d&#39;une expérience client négative.

## Qualité et hygiène des données

La collecte de données n&#39;est qu&#39;une partie du défi. Vous devez vous assurer que les données sont à la fois exactes et utilisables. Vous devez disposer de filtres de format de base. Une adresse électronique n&#39;est pas valide si elle n&#39;inclut pas &quot;@&quot; ou &quot;.&quot; par exemple. Veillez à ne pas autoriser les adresses d’alias courantes, également appelées comptes de rôle (tels que &quot;info&quot;, &quot;admin&quot;, &quot;ventes&quot;, &quot;support&quot;, etc.). Les comptes de rôle peuvent présenter des risques parce que, de par leur nature, le destinataire contient un groupe de personnes plutôt qu’un seul abonné. Les attentes et la tolérance peuvent varier d&#39;un groupe à l&#39;autre, ce qui peut entraîner des plaintes, des engagements variables, des désabonnements et une confusion générale.

Voici quelques solutions aux problèmes courants que vous pouvez rencontrer avec vos données d’adresse électronique :

**[!DNL Double opt-in (DOI)]**
[!DNL Double opt-in (DOI)] est considérée comme la meilleure pratique de délivrabilité par la plupart des experts du courrier électronique. Si vous rencontrez des problèmes avec des pièges à messages indésirables ou des plaintes sur vos courriels de bienvenue, l&#39;interface utilisateur (DOI) est un bon moyen de s&#39;assurer que l&#39;abonné qui reçoit vos courriels est la personne qui s&#39;est effectivement inscrite à votre programme de courriel et qui veut recevoir vos courriels.

L’interface DOI consiste à envoyer un courriel de confirmation à l’adresse électronique de l’abonné qui vient de s’inscrire à votre programme de messagerie. Il contient un lien qui doit être cliqué pour confirmer le consentement. Avec cette méthode d’acquisition, si l’abonné ne confirme pas, l’expéditeur ne lui envoie pas plus de courriels. Informez les nouveaux abonnés que vous effectuez cette opération sur le site Web, en les encourageant à terminer l’inscription avant de continuer. Cette méthode permet certes de réduire le nombre d&#39;abonnements, mais ceux qui s&#39;inscrivent ont tendance à être très engagés et à rester à long terme, ce qui se traduit généralement par un retour sur investissement beaucoup plus élevé pour l&#39;expéditeur.

**Champ masquéL&#39;application d&#39;un champ masqué sur votre formulaire d&#39;inscription est un excellent moyen de différencier les abonnements automatisés par rapport aux abonnés humains réels.**
Comme le champ de données n’est pas visible, masqué dans le code HTML, un robot entre des données qui ne le seraient pas pour un humain. Cette méthode vous permet de créer des règles pour supprimer toute inscription incluant des données renseignées dans ce champ masqué.

**[!DNL re-CAPTCHA]**
[!DNL re-CAPTCHA] est une méthode de validation que vous pouvez utiliser pour réduire les risques que l&#39;abonné soit un robot et non une personne réelle. Il existe différentes versions, dont certaines contiennent des images ou des identifications de mots-clés. Certaines versions sont plus efficaces que d&#39;autres, et ce que vous gagnez en termes de sécurité et de prévention des problèmes de délivrabilité est beaucoup plus important que tout impact négatif sur les conversions.

## Directives juridiques

Consultez vos avocats pour interpréter les lois locales et nationales concernant le courrier électronique. Rappelez-vous que les lois sur les courriels varient considérablement d&#39;un pays à l&#39;autre et parfois de régions locales différentes au sein d&#39;un même pays.

* Veillez à recueillir les informations sur l’emplacement d’un abonné afin de vous conformer aux lois nationales de l’abonné. Sans ce détail, vous pouvez être limité dans la façon dont vous pouvez commercialiser l&#39;abonné.
* Toute loi pertinente est déterminée par l&#39;emplacement du destinataire et non par l&#39;expéditeur. Vous devez donc connaître et suivre les lois de n&#39;importe quel pays où vous pourriez avoir un abonné.
* Il est souvent difficile de connaître avec une certitude absolue le pays de résidence de l’abonné. Les données fournies par le client peuvent être obsolètes et les données de localisation en pixels peuvent être inexactes en raison d&#39;un VPN ou d&#39;un entrepôt d&#39;images, comme avec Gmail et Yahoo. En cas de doute, il est plus sûr d’appliquer les lois et directives les plus strictes possible.

## Autres méthodes de collecte de listes non recommandées

Il existe de nombreuses autres façons de recueillir des réponses, chacune avec ses propres opportunités, défis et inconvénients. Nous ne les recommandons pas en général, car l’utilisation est souvent limitée par des règles d’utilisation acceptables du fournisseur. Nous examinerons quelques exemples courants afin que vous puissiez découvrir les dangers qui vous aideront à limiter ou à éviter les risques :

**Achetez ou louez une**
listeIl existe de nombreux types d&#39;adresses électroniques. e-mails Principal, e-mails de travail, e-mails scolaires, e-mails secondaires et e-mails inactifs pour n&#39;en nommer que quelques-uns. Les types d&#39;adresses collectées et partagées par le biais de listes achetées ou louées sont rarement des comptes de messagerie Principaux, qui sont les lieux où se produisent presque toutes les activités d&#39;engagement et d&#39;achat.

Si vous avez de la chance, vous obtenez des comptes secondaires, où les gens recherchent des affaires et des offres lorsqu&#39;ils sont prêts à acheter quelque chose. Cela se traduit généralement par de faibles niveaux d&#39;engagement, le cas échéant. Si vous n&#39;avez pas de chance, la liste sera pleine de courriels inactifs, qui peuvent maintenant être des pièges à spam. Souvent, vous recevez un mélange de courriers électroniques secondaires et inactifs. En général, la qualité de ces types de listes fait plus de mal que de bien à un programme électronique. Cette pratique est interdite par la [politique d&#39;utilisation acceptable de Adobe Campaign](https://www.adobe.com/fr/legal/terms/aup.html).

**Listes**
appendCe sont des clients qui ont choisi de s&#39;engager avec votre marque, ce qui est génial. Mais ils ont choisi d&#39;utiliser une méthode autre que le courriel (en magasin, les médias sociaux, etc.). Ils n’ont pas pu être réceptifs à l’obtention d’un courriel non demandé de votre part et peuvent aussi s’inquiéter de la façon dont vous avez obtenu leur adresse électronique puisqu’ils ne l’ont pas fournie. Cette méthode risque de transformer un client ou un client potentiel qui s&#39;est engagé avec votre marque en un détracteur qui ne fait plus confiance à votre marque et qui ira plutôt à votre concurrence. Cette pratique est interdite par la [politique d&#39;utilisation acceptable de Adobe Campaign](https://www.adobe.com/legal/terms/aup.html).

**Foire commerciale ou autre**
collection de événementsLa collecte d&#39;adresses à un kiosque ou par l&#39;intermédiaire d&#39;une autre méthode officielle et clairement marquée peut s&#39;avérer utile. Le risque est que de nombreux événements comme celui-ci recueillent toutes les adresses et les distribuent par l&#39;intermédiaire du promoteur de événement ou de l&#39;hôte. Cela signifie que les utilisateurs de ces adresses électroniques n’ont jamais demandé à recevoir de courriels de votre marque. Ces abonnés sont susceptibles de se plaindre et de signaler votre courrier comme indésirable, et ils n&#39;ont peut-être pas fourni de coordonnées exactes.

****
TirageTirage permet de fournir rapidement un grand nombre d&#39;adresses électroniques. Mais ces abonnés veulent le prix, pas vos courriels. Ils n&#39;ont peut-être même pas prêté attention au nom de qui leur tenterait la main. Ces abonnés sont susceptibles de se plaindre et de signaler votre courrier comme indésirable, et il est peu probable qu&#39;ils s&#39;engagent ou fassent un achat.
