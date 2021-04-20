---
title: Doublons
description: Découvrez comment identifier et limiter les duplicata pour améliorer la délivrabilité.
feature: Additional resources
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 96ed84da391faaabd3001ddd6a411ddc1f46b033
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 56%

---


# Doublons {#duplicates}

L’existence de doublons pour une adresse email peut avoir plusieurs conséquences :

* Envois multiples du même message. Même si l’Adobe effectue par défaut une procédure de déduplication avant l’envoi, rien n’empêche l’envoi du même message par des actions différentes ayant le même contenu lorsqu’une cible est fractionnée.
* Non-respect de la désinscription. Si une personne se désinscrit suite à la réception d’un message, son profil en doublon sera quant à lui toujours éligible aux envois.

Outre le non-respect de l’opt-in, cette situation amènera probablement les utilisateurs à considérer les messages comme du spam et déclencher une action de placement sur liste bloquée de la part du FAI.

Il faut être particulièrement prudent lors d&#39;opérations sur la base :

* Les imports doivent être soigneusement paramétrés, en particulier dans le choix de la clé de réconciliation.
* Les adresses électroniques modifiées peuvent également être une source de duplicata. En particulier, deux adresses avec des domaines différents peuvent être routées vers la même boîte aux lettres, par exemple si une société a changé de nom et a conservé l&#39;ancien domaine pendant un certain temps : joe.doe@amce-co.com et joe.doe@acme-rebranded.com.
* Les importations automatiques, qu&#39;il s&#39;agisse de listes ou d&#39;autres bases de données, sont des éléments à prendre en compte dans la gestion des profils. Que se passe-t-il si on supprime ou on déplace un profil dans une autre partition ? Il peut être recréé dans la partition initiale par une importation automatique, par exemple lorsqu&#39;un bon de commande est placé.
* Le rangement des profils dans des dossiers différents peut être mise en oeuvre à l&#39;aide de vues plutôt que de partitions. Ainsi on s&#39;assure que les profils sont physiquement dans la même partition tout en permettant un affichage et une gestion des droits adéquats.

Il existe tout de même des cas où la présence de doublons entre différentes partitions est normale. Par exemple, lorsqu’on opère des envois pour le compte de sociétés ou d’entités différentes, il est logique qu’une même personne puisse être adressée à des titres différents. Il est cependant rarement normal de trouver des doublons dans une même partition.

## Ressources spécifiques au produit

Pour garantir votre réputation et assurer une bonne gestion des quarantaines, dédupliquez les adresses. Pour en savoir plus, consultez les sections suivantes de la documentation du produit :

**Adobe Campaign Classic**

* [Activité Déduplication](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/targeting-activities/deduplication.html)
* [Utilisation de la fonctionnalité de fusion de l’activité Déduplication](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/data-management/deduplication-merge.html)

**Adobe Campaign Standard **

* [Dédupliquer les données d’un fichier importé](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/workflow-use-case/data-management/deduplicating-data-imported-file.html)