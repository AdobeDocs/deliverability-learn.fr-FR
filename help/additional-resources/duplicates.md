---
title: Doublons
description: Découvrez comment identifier et limiter les doublons pour améliorer la délivrabilité.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: f89dbb38-a8d4-4294-b017-6fed72591593
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 59%

---

# Doublons {#duplicates}

L’existence de doublons pour une adresse email peut avoir plusieurs conséquences :

* Envois multiples du même message. Même si Adobe applique par défaut une déduplication avant l&#39;envoi, rien n&#39;empêche l&#39;envoi du même message par des actions différentes ayant le même contenu lorsqu&#39;une cible est partagée.
* Non-respect de la désinscription. Si une personne se désinscrit suite à la réception d’un message, son profil en doublon sera quant à lui toujours éligible aux envois.

Outre le non-respect de l’opt-in, cette situation amènera probablement les utilisateurs à considérer les messages comme du spam et déclencher une action de placement sur liste bloquée de la part du FAI.

Il faut être particulièrement prudent lors d&#39;opérations sur la base :

* Les imports doivent être soigneusement paramétrés, en particulier dans le choix de la clé de réconciliation.
* Les modifications d’adresses électroniques peuvent également être source de doublons. En particulier, deux adresses avec des domaines différents peuvent être routées vers la même boîte mail, par exemple si une société a changé de nom et a conservé un certain temps l&#39;ancien domaine : joe.doe@amce-co.com et joe.doe@acme-rebranded.com.
* Les imports automatiques, qu&#39;il s&#39;agisse de listes ou d&#39;autres bases de données, sont des éléments à prendre en compte dans la gestion des profils. Que se passe-t-il si on supprime ou on déplace un profil dans une autre partition ? Il peut être recréé dans la partition initiale par un import automatique, par exemple lorsqu&#39;une commande est passée.
* Le rangement des profils dans des dossiers différents peut être mise en oeuvre à l&#39;aide de vues plutôt que de partitions. Ainsi on s&#39;assure que les profils sont physiquement dans la même partition tout en permettant un affichage et une gestion des droits adéquats.

Il existe tout de même des cas où la présence de doublons entre différentes partitions est normale. Par exemple, lorsqu’on opère des envois pour le compte de sociétés ou d’entités différentes, il est logique qu’une même personne puisse être adressée à des titres différents. Il est cependant rarement normal de trouver des doublons dans une même partition.

## Ressources spécifiques au produit

Pour garantir votre réputation et assurer une bonne gestion des quarantaines, dédupliquez les adresses. Pour en savoir plus, consultez les sections suivantes de la documentation du produit :

**Adobe Campaign Classic**

* [Activité Déduplication](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/targeting-activities/deduplication.html)
* [Utilisation de la fonctionnalité Déduplication de fusion des activités](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/data-management/deduplication-merge.html?lang=fr)

**Adobe Campaign Standard**

* [Dédupliquer les données d’un fichier importé](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/workflow-use-case/data-management/deduplicating-data-imported-file.html)
