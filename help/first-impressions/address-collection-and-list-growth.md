---
title: Collecte d'adresses et croissance des listes
description: Découvrez quelles sont les meilleures sources pour les nouvelles adresses email, comment garantir une qualité des données et l’alignement avec les directives juridiques.
topics: Deliverability
jira: KT-7063
thumbnail: kt7063.jpg
doc-type: article
activity: understand
team: TM
exl-id: 350950dc-4703-402a-8e22-3862f4e21d52
source-git-commit: 9444f8601f2f349398ee5deb9d5f4d4f7abb44f5
workflow-type: tm+mt
source-wordcount: '1594'
ht-degree: 3%

---

# Collecte d&#39;adresses et croissance des listes

Les meilleures sources de nouvelles adresses électroniques sont les sources directes comme les inscriptions sur votre site web ou dans les magasins physiques. Dans ces situations, vous pouvez contrôler l’expérience pour vous assurer qu’elle est positive et que l’abonné est intéressé par l’obtention d’emails de votre marque.

Quelques remarques sur ces méthodes d’inscription :

La collection de listes **Magasin physique** peut présenter des défis en raison de la saisie verbale ou écrite de l’adresse, ce qui entraîne une faute d’orthographe des adresses. Il est recommandé d’envoyer un email de confirmation le plus rapidement possible après les inscriptions en magasin.

La forme la plus courante de **abonnement au site web** est &quot;abonnement unique&quot;. Il s’agit de la norme minimale absolue que vous devez utiliser pour acquérir des adresses électroniques. L’option d’opt-in unique est lorsque le détenteur d’une adresse email spécifique accorde à l’expéditeur l’autorisation d’envoyer des emails marketing, généralement en envoyant l’adresse via un formulaire web ou des inscriptions en magasin. Bien qu’il soit possible d’exécuter une campagne par e-mail réussie à l’aide de cette méthode, cela peut être la cause de certains problèmes.

* Les adresses électroniques non confirmées peuvent avoir des fautes de frappe ou être mal formées, incorrectes ou utilisées de manière malveillante. Les fautes de frappe et les adresses incorrectes provoquent des taux de rebond élevés, ce qui peut et provoque des blocs émis par les FAI ou une perte de réputation IP.

* L’envoi malveillant de pièges à spam connus (parfois appelé &quot;empoisonnement par liste&quot;) peut entraîner d’énormes problèmes de diffusion et de réputation si le propriétaire de ce piège agit. Il est impossible de savoir si le destinataire souhaite réellement être ajouté à une liste marketing sans confirmation. Il est donc tout aussi impossible de définir les attentes du destinataire et cela peut entraîner une augmentation des plaintes pour spam — et parfois placer sur la liste bloquée si l&#39;email collecté se trouve être un piège pour spam.

Pour plus d’informations sur la manière de minimiser les problèmes présentés à la fois dans le magasin physique et dans l’inclusion unique, consultez la section [Qualité des données et hygiène](#data-quality-and-hygiene) de ce guide pour plus d’informations sur les avantages du double opt-in.

>[!NOTE]
>
>Les abonnés utilisent souvent des adresses de jeton, des adresses expirées ou des adresses qui ne sont pas les leurs pour obtenir ce qu’ils veulent d’un site web, mais également pour éviter d’être ajoutés à des listes marketing. Dans ce cas, les listes des marketeurs génèrent un nombre élevé de hard bounces, un taux élevé de plaintes pour spam et des abonnés qui ne cliquent pas, n’ouvrent pas ou n’interagissent pas positivement avec les emails. Il peut être considéré comme un drapeau rouge pour les fournisseurs de messagerie et les FAI.

## Formulaires d’inscription

Outre l’ajout de champs pour les données, vous souhaitez collecter des informations sur vos nouveaux abonnés. Vous devez également effectuer d’autres actions avec votre formulaire d’inscription sur le site web.

* Définissez avec l’abonné des attentes claires quant à la réception des emails, ce qu’il recevra et la fréquence à laquelle il les recevra.
* Ajoutez des options permettant à l&#39;abonné de sélectionner la fréquence ou le type de communication qu&#39;il reçoit. Ces options vous permettent de connaître les préférences de l’abonné dès le départ afin que vous puissiez offrir la meilleure expérience possible à votre nouveau client.
* Équilibrez le risque de perte d’intérêt de l’abonné lors du processus d’inscription en demandant autant d’informations que possible. Des éléments tels que leur anniversaire, leur emplacement géographique ou leurs centres d’intérêt vous aident à envoyer du contenu plus personnalisé. Les abonnés de chaque marque ont des attentes et des seuils de tolérance différents. Les tests sont donc essentiels pour trouver le bon équilibre pour votre situation.

>[!NOTE]
>
> N’utilisez pas de cases pré-cochées pendant le processus d’inscription. Bien qu’il puisse vous attirer des ennuis légalement, il s’agit également d’une expérience client négative.

## Qualité et hygiène des données

La collecte de données n&#39;est qu&#39;une partie du défi. Vous devez également vous assurer que les données sont à la fois précises et utilisables. Les filtres de format de base doivent être en place. Une adresse électronique n’est pas valide si elle n’inclut pas le &quot;@&quot; ou le &quot;.&quot; par exemple. Veillez à ne pas autoriser les adresses d’alias courantes, également appelées comptes de rôle (comme &quot;info&quot;, &quot;admin&quot;, &quot;sales&quot;, &quot;support&quot;, etc.). Les comptes de rôle peuvent présenter des risques car, par nature, le destinataire contient un groupe de personnes plutôt qu’un seul abonné. Les attentes et la tolérance peuvent varier au sein d&#39;un groupe, ce qui peut entraîner des plaintes, des engagements variables, des désabonnements et une confusion générale.

Voici quelques solutions aux problèmes courants que vous pouvez rencontrer avec les données de vos adresses électroniques :

**[!DNL Double opt-in (DOI)]**
[!DNL Double opt-in (DOI)] est considéré comme la meilleure pratique de délivrabilité par la plupart des experts en messagerie électronique. Si vous rencontrez des problèmes avec des pièges à spam ou des plaintes concernant vos emails de bienvenue, l’interface de commande est un bon moyen de vous assurer que l’abonné qui reçoit vos emails s’est réellement inscrit à votre programme de messagerie et souhaite recevoir vos emails.

L’interface utilisateur consiste à envoyer un courrier électronique de confirmation à l’adresse électronique de l’abonné qui s’est inscrit à votre programme de messagerie. Il contient un lien qui doit être cliqué pour confirmer le consentement. Avec cette méthode d’acquisition, si l’abonné ne confirme pas, l’expéditeur ne lui envoie pas plus d’emails. Informez les nouveaux abonnés que vous effectuez cette opération sur le site web, en les encourageant à terminer l’inscription avant de continuer. Cette méthode permet certes de réduire le nombre d&#39;inscriptions, mais les personnes qui s&#39;inscrivent ont tendance à être fortement engagées et à rester à long terme. Cela génère généralement un ROI beaucoup plus élevé pour l’expéditeur.

**Champ masqué**
L’application d’un champ masqué à votre formulaire d’inscription est un excellent moyen de différencier les abonnements automatisés aux robots des abonnés humains réels. Comme le champ de données n’est pas visible, masqué dans le code de l’HTML, un robot saisit les données qui ne le seraient pas pour un humain. Grâce à cette méthode, vous pouvez créer des règles pour supprimer toute inscription incluant des données renseignées dans ce champ masqué.

**[!DNL re-CAPTCHA] est une méthode de validation que vous pouvez utiliser pour réduire les risques que l’abonné soit un robot et non une personne réelle. Il existe différentes versions, dont certaines contiennent des identifications par mot-clé ou des images. Certaines versions sont plus efficaces que d’autres, et ce que vous gagnez en termes de prévention des problèmes de sécurité et de délivrabilité est beaucoup plus élevé que tout impact négatif sur les conversions.

## Directives juridiques

Consultez vos avocats pour interpréter les lois locales et nationales concernant les courriels. N&#39;oubliez pas que les lois sur les emails varient énormément d&#39;un pays à l&#39;autre et parfois de différentes régions locales au sein d&#39;un même pays.

* Veillez à collecter les informations de localisation d’un abonné afin de respecter les lois du pays de l’abonné. Sans ce détail, vous pouvez être limité dans la manière dont vous pouvez vendre à l&#39;abonné.
* Toutes les lois pertinentes sont déterminées par l&#39;emplacement du destinataire, et non par l&#39;expéditeur. Vous devez donc connaître et suivre les lois de n&#39;importe quel pays où vous pourriez avoir un abonné.
* Il est souvent difficile de connaître avec une totale certitude le pays de résidence de l&#39;abonné. Les données fournies par le client peuvent être obsolètes et les données de localisation des pixels peuvent être inexactes en raison d’un entrepôt VPN ou d’images, comme avec Gmail et Yahoo. En cas de doute, il est plus sûr d&#39;appliquer les lois et les directives les plus strictes possible.

## Autres méthodes de collecte de listes non recommandées

Il existe de nombreuses autres façons de recueillir des réponses, chacune ayant ses propres opportunités, défis et inconvénients. Adobe ne recommande pas ces règles en général, car l&#39;utilisation est souvent limitée par le biais de stratégies d&#39;utilisation acceptables par le fournisseur. Nous allons consulter quelques exemples courants afin que vous puissiez découvrir les dangers pour vous aider à limiter ou éviter les risques :

**Acheter ou louer une liste**
Il y a de nombreux types d&#39;adresses électroniques là-bas. Principal de courriers électroniques, de courriers électroniques de travail, de courriers électroniques secondaires et d’emails inactifs, pour n’en citer que quelques-uns. Les types d’adresses collectées et partagées par le biais de listes achetées ou louées sont rarement des comptes de messagerie principaux, qui sont les lieux où se produisent presque toutes les activités d’engagement et d’achat.

Si vous avez de la chance, vous obtenez des comptes secondaires, où les gens recherchent des offres et des offres lorsqu’ils sont prêts à acheter quelque chose. Cela se traduit généralement par de faibles niveaux d’engagement, le cas échéant. Si vous n’avez pas de chance, la liste est pleine d’emails inactifs, qui peuvent désormais être des pièges à spam. Souvent, vous obtenez un mélange d’emails secondaires et inactifs. En règle générale, la qualité de ce type de liste fait plus de mal qu&#39;elle ne fait de bien à un programme de messagerie. Cette pratique est interdite par la [stratégie d’utilisation acceptable Adobe Campaign](https://www.adobe.com/fr/legal/terms/aup.html).

**Listes ajoutées**
Ce sont des clients qui ont choisi de s&#39;engager avec votre marque, ce qui est génial. Mais ils ont choisi de s&#39;engager par une autre méthode que le courriel (en magasin, les médias sociaux, etc.). Ils n’ont pas pu être réceptifs à l’obtention d’un email non demandé de votre part et peuvent également être inquiets de la façon dont vous avez obtenu leur adresse électronique puisqu’ils ne l’ont pas fournie. Cette méthode risque de transformer un client ou un client potentiel qui s’est engagé avec votre marque en un détracteur qui ne fait plus confiance à votre marque et qui se tourne plutôt vers votre concurrence. Cette pratique est interdite par la [stratégie d’utilisation acceptable Adobe Campaign](https://www.adobe.com/fr/legal/terms/aup.html).

**Foire commerciale ou autre collection d&#39;événements**
La collecte des adresses sur un stand ou par le biais d&#39;une autre méthode officielle, nettement identifiée, peut s&#39;avérer utile. Le risque est que de nombreux événements comme celui-ci collectent toutes les adresses et les distribuent par l’intermédiaire du promoteur ou de l’hôte de l’événement. Ce qui signifie que les propriétaires de ces adresses email n&#39;ont jamais demandé à recevoir d&#39;emails de votre marque. Il est probable que ces abonnés se plaignent et marquent votre email comme du spam, et qu&#39;ils n&#39;ont pas fourni d&#39;informations de contact précises.

**Tirage**

Les tirages fournissent rapidement un grand nombre d’adresses électroniques. Mais ces abonnés veulent le prix, pas vos emails. Ils n&#39;ont peut-être même pas prêté attention au nom de qui leur tenterait la main. Il est probable qu’ils se plaignent et marquent votre email comme du spam, et il est peu probable qu’ils s’engagent ou effectuent un achat.

## Ressources spécifiques au produit

**Adobe Campaign Classic**

* [Création d’un formulaire d’abonnement avec double opt-in](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-forms/use-cases--web-forms.html?lang=fr-FR#create-a-subscription--form-with-double-opt-in)

**Adobe Campaign Standard**

* [Processus de double opt-in](https://experienceleague.adobe.com/docs/campaign-standard/using/communication-channels/landing-pages/setting-up-a-double-opt-in-process.html?lang=fr#communication-channels)
