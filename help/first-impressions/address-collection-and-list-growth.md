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
TQID: https://experienceleague.adobe.com/Pq8XpNwqzMbxggauciqILSUqX6BT4OCiDffc7ZgDhWc
product_v2: id: b27e5950-9033-45ac-9f86-eb22e567f615id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2: id: b0bb9048-d951-48d8-8232-45cf248a7e27id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
role_v2: id: b69b2659-1057-424e-8fc5-ed9e016dc554id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2: id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2: id: b4dd41a7-ccf8-4e9d-918e-acaab534a307id: bce87dde-a4ab-44c9-8a18-ad66e4ddb377id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 1670
ht-degree: 6%

---

# Collecte d&#39;adresses et croissance des listes

Les meilleures sources de nouvelles adresses e-mail sont les sources directes telles que les inscriptions sur votre site web ou dans les magasins physiques. Dans ces situations, vous pouvez contrôler l’expérience pour vous assurer qu’elle est positive et que l’abonné est intéressé à recevoir des e-mails de votre marque.

Quelques remarques sur ces méthodes d’inscription :

La collecte des listes **magasin physique** peut présenter des problèmes en raison des entrées d’adresse verbales ou écrites, ce qui entraîne des fautes d’orthographe dans les adresses. Il est recommandé d’envoyer un e-mail de confirmation le plus rapidement possible après les inscriptions en magasin.

La forme la plus courante d’**inscription à un site web** est l’« opt-in unique ». Il s’agit de la norme minimale absolue à utiliser pour acquérir des adresses e-mail. L’opt-in unique correspond au moment où le titulaire d’une adresse e-mail spécifique accorde à un expéditeur l’autorisation de lui envoyer des e-mails marketing, généralement en envoyant l’adresse via un formulaire web ou des inscriptions en magasin. Bien qu’il soit possible d’exécuter une campagne par e-mail réussie à l’aide de cette méthode, elle peut être à l’origine de certains problèmes.

* Les adresses e-mail non confirmées peuvent comporter des fautes de frappe ou être mal formées, incorrectes ou utilisées à des fins malveillantes. Les fautes de frappe et les adresses incorrectes entraînent des taux de rebond élevés, qui peuvent et provoquent effectivement des blocs émis par les FAI ou une perte de réputation des adresses IP.

* L&#39;envoi malveillant de pièges à spam connus (parfois appelés « empoisonnement de liste ») peut causer d&#39;énormes problèmes de diffusion et de réputation si le propriétaire de ce piège agit. Il est impossible de savoir si le destinataire souhaite vraiment être ajouté à une liste marketing sans confirmation. Cela rend également impossible la définition des attentes du destinataire et peut entraîner une augmentation des plaintes pour spam, et parfois une liste bloquée si l&#39;email collecté se trouve être un piège à spam.

Pour obtenir des conseils sur la manière de minimiser les problèmes présentés à la fois dans le magasin physique et l’opt-in unique, accédez à la section [ Qualité et hygiène des données ](#data-quality-and-hygiene) de ce guide pour les détails et les avantages du double opt-in.

>[!NOTE]
>
>Les abonnés utilisent souvent des adresses jetables, des adresses expirées ou des adresses qui ne leur appartiennent pas pour obtenir ce qu’ils veulent d’un site web, mais évitent également d’être ajoutés aux listes marketing. Lorsque cela se produit, les listes des spécialistes marketing génèrent un grand nombre d’erreurs hard, des taux de plainte pour spam élevés et des abonnés qui ne cliquent pas sur les e-mails, ne les ouvrent pas et n&#39;y participent pas positivement. Cela peut être considéré comme un signal d&#39;alarme pour les fournisseurs de messagerie et les FAI.

## Formulaires d’inscription

Outre l’ajout de champs pour les données, que vous souhaitez collecter sur vos nouveaux abonnés, vous devez également utiliser votre formulaire d’inscription sur le site web.

* Définissez clairement les attentes de l’abonné : il accepte de recevoir des e-mails, ce qu’il recevra et à quelle fréquence.
* Ajoutez des options permettant à l’abonné de sélectionner la fréquence ou le type de communications qu’il reçoit. Ces options vous permettent de connaître les préférences de l’abonné dès le départ afin de fournir la meilleure expérience possible à votre nouveau client.
* Équilibrez le risque de perdre l’intérêt de l’abonné pendant le processus d’inscription en demandant le plus d’informations possible. Des éléments tels que leur anniversaire, leur lieu ou leurs centres d’intérêt vous aident à envoyer davantage de contenu personnalisé. Les abonnés de chaque marque ont des attentes et des seuils de tolérance différents. Les tests sont donc essentiels pour trouver le bon équilibre dans votre situation.

>[!NOTE]
>
> N’utilisez pas de cases pré-cochées pendant le processus d’inscription. Bien que cela puisse vous mettre dans le pétrin légalement, c&#39;est également une expérience client négative.

## Qualité et hygiène des données

La collecte de données n’est qu’une partie du défi. Vous devez également vous assurer que les données sont à la fois exactes et utilisables. Vous devez avoir des filtres de format de base en place. Une adresse e-mail n’est pas valide si elle ne comprend pas de caractère « @ » ou « . », par exemple. Veillez à ne pas autoriser les adresses d’alias courantes, également appelées comptes de rôle (comme « info », « admin », « sales », « support »). Les comptes de rôle peuvent présenter un risque car, de par leur nature, le destinataire contient un groupe de personnes plutôt qu’un seul abonné. Les attentes et la tolérance peuvent varier au sein d’un groupe, ce qui entraîne un risque de plaintes, d’engagement variable, de désabonnements et de confusion générale.

Voici quelques solutions aux problèmes courants que vous pouvez rencontrer avec les données de votre adresse e-mail :

**[!DNL Double opt-in (DOI)]**
[!DNL Double opt-in (DOI)] est considéré comme la meilleure pratique en matière de délivrabilité par la plupart des experts en e-mails. Si vous rencontrez des problèmes avec les pièges à spam ou les plaintes sur vos emails de bienvenue, DOI est un bon moyen de s&#39;assurer que l&#39;abonné qui reçoit vos emails s&#39;est inscrit à votre programme d&#39;email et souhaite recevoir vos emails.

Le DOI consiste à envoyer un e-mail de confirmation à l’adresse e-mail de l’abonné qui s’est inscrit à votre programme de messagerie, contenant un lien sur lequel il faut cliquer pour confirmer le consentement. Avec cette méthode d’acquisition, si l’abonné ne confirme pas, l’expéditeur ne lui enverra pas d’autres e-mails. Informez les nouveaux abonnés et abonnées que vous effectuez cette opération sur le site Web, en les encourageant à s’inscrire avant de continuer. Cette méthode permet de réduire le nombre d’inscriptions, mais les personnes qui s’inscrivent ont tendance à être très impliquées et à rester sur le long terme. Généralement, le retour sur investissement de l’expéditeur est beaucoup plus élevé.

**Champ masqué**
L’application d’un champ masqué à votre formulaire d’inscription est un excellent moyen de différencier les inscriptions automatisées aux robots des véritables abonnés humains. Comme le champ de données n’est pas visible, masqué dans le code HTML, un robot saisit des données là où un humain ne le ferait pas. Grâce à cette méthode, vous pouvez créer des règles pour supprimer tout abonnement contenant des données renseignées dans ce champ masqué.

**[!DNL re-CAPTCHA] est une méthode de validation que vous pouvez utiliser pour réduire les risques que l’abonné soit un robot et non une personne réelle. Il existe différentes versions, dont certaines contiennent une identification par mot-clé ou des images. Certaines versions sont plus efficaces que d’autres. En outre, les gains en termes de sécurité et de prévention des problèmes de délivrabilité sont bien supérieurs aux répercussions négatives sur les conversions.

## Directives juridiques

Consultez vos avocats pour interpréter les lois locales et nationales concernant les courriels. N’oubliez pas que les lois sur les courriers électroniques varient considérablement d’un pays à l’autre et parfois d’une région à l’autre.

* Veillez à collecter les informations de localisation d’un abonné afin de vous conformer aux lois du pays de l’abonné. Sans ce détail, vous pouvez être limité dans la façon dont vous pouvez faire la promotion auprès de l&#39;abonné.
* Toutes les lois pertinentes sont déterminées par le lieu du destinataire, et non par l&#39;expéditeur. Vous devez donc connaître et respecter les lois de tout pays où vous pourriez avoir un abonné.
* Il est souvent difficile de connaître avec certitude le pays de résidence de l’abonné. Les données fournies par le client peuvent être obsolètes et les données de localisation des pixels peuvent être inexactes en raison du VPN ou de l&#39;entreposage d&#39;images, comme avec Gmail et Yahoo. En cas de doute, il est plus sûr d’appliquer les lois et directives les plus strictes possibles.

## Autres méthodes de collecte de listes non recommandées

Il existe de nombreuses autres façons de collecter les adresses, chacune ayant ses propres opportunités, défis et inconvénients. Adobe ne recommande pas ces protocoles en général, car leur utilisation est souvent limitée par des politiques d’utilisation acceptables pour le fournisseur. Nous examinerons quelques exemples courants afin que vous puissiez en apprendre davantage sur les dangers pour vous aider à limiter ou à éviter les risques :

**Acheter ou louer une liste**
Il existe de nombreux types d’adresses e-mail. les e-mails de Principal, les e-mails professionnels, les e-mails scolaires, les e-mails secondaires et les e-mails inactifs, pour n’en citer que quelques-uns. Les types d’adresses collectées et partagées par le biais de listes achetées ou louées sont rarement des comptes de messagerie principaux, où se produisent presque toutes les activités d’engagement et d’achat.

Si vous avez de la chance, vous obtenez des comptes secondaires, où les gens recherchent des offres et des offres lorsqu’ils sont prêts à acheter quelque chose. Cela se traduit généralement par de faibles niveaux d’engagement, le cas échéant. Si vous n’avez pas de chance, la liste est pleine d’e-mails inactifs, qui pourraient désormais être des pièges à spam. Souvent, vous recevez un mélange d’e-mails secondaires et inactifs. En général, la qualité de ces types de listes fait plus de mal que de bien à un programme de messagerie. Cette pratique est interdite par la politique d’utilisation acceptable d’Adobe Campaign [](https://www.adobe.com/fr/legal/terms/aup.html).

**Listes ajoutées**
Il s’agit de clients qui ont choisi de s’engager avec votre marque, ce qui est formidable. Mais ils ont choisi une autre méthode que le courriel (en magasin, sur les médias sociaux, etc.). Ils ne pouvaient pas être réceptifs à l’idée de recevoir un e-mail non demandé de votre part et peuvent également s’inquiéter de la manière dont vous avez obtenu leur adresse e-mail puisqu’ils ne l’ont pas fournie. Cette méthode risque de transformer un client ou un client potentiel qui s&#39;est engagé auprès de votre marque en un détracteur qui ne fait plus confiance à votre marque et qui se tourne plutôt vers vos concurrents. Cette pratique est interdite par la politique d’utilisation acceptable d’Adobe Campaign [](https://www.adobe.com/fr/legal/terms/aup.html).

**Salon professionnel ou autre collection d&#39;événements**
Collecter des adresses à un kiosque ou par l&#39;intermédiaire d&#39;une autre méthode officielle clairement identifiée peut être utile. Le risque est que de nombreux événements comme celui-ci collectent toutes les adresses et les distribuent par l&#39;intermédiaire du promoteur ou de l&#39;hôte de l&#39;événement. Cela signifie que les propriétaires de ces adresses e-mail n’ont jamais demandé à recevoir d’e-mails de votre marque. Ces abonnés sont susceptibles de se plaindre et de marquer votre e-mail comme indésirable, et ils peuvent ne pas avoir fourni des coordonnées exactes.

**Concours**

Les tirages au sort fournissent rapidement un grand nombre d’adresses e-mail. Mais ces abonnés veulent le prix, pas vos e-mails. Ils n&#39;ont peut-être même pas prêté attention au nom de ceux qui leur tendraient la main. Ils sont susceptibles de se plaindre et de marquer votre e-mail comme indésirable, et il est peu probable qu’ils s’engagent dans un processus ou effectuent un achat.

## Ressources spécifiques au produit

**Adobe Campaign Classic**

* [Créer un formulaire d’abonnement avec double opt-in](https://experienceleague.adobe.com/docs/campaign-classic/using/designing-content/web-forms/use-cases--web-forms.html?lang=fr-FR#create-a-subscription--form-with-double-opt-in)

**Adobe Campaign Standard**

* [Processus de double opt-in](https://experienceleague.adobe.com/docs/campaign-standard/using/communication-channels/landing-pages/setting-up-a-double-opt-in-process.html?lang=fr#communication-channels)
