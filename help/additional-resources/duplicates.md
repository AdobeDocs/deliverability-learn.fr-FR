---
title: Doublons
description: Découvrez comment identifier et limiter les doublons pour améliorer la délivrabilité.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: f89dbb38-a8d4-4294-b017-6fed72591593
TQID: https://experienceleague.adobe.com/7KlDe-wQmAih6L4bl4xrw-lVS35-wNzyyxneyFbSo0A
product_v2:
  - id: b27e5950-9033-45ac-9f86-eb22e567f615
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: b0bb9048-d951-48d8-8232-45cf248a7e27
  - id: c5f60233-d5ea-4453-a799-0ad258b4d399
  - id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 413
ht-degree: 57%

---

# Doublons {#duplicates}

L’existence de doublons pour une adresse e-mail peut avoir plusieurs conséquences :

* Envois multiples du même message. Même si Adobe effectue une procédure de déduplication par défaut avant l’envoi, rien n’empêche l’envoi d’un même message par différentes actions ayant le même contenu lorsqu’une cible est fractionnée.
* Non-respect de la désinscription. Si une personne se désinscrit suite à la réception d’un message, son profil en double sera quant à lui toujours éligible aux envois.

Outre le non-respect de l’opt-in, cette situation amènera probablement les utilisateurs à considérer les messages comme du spam et déclencher une action de placement sur liste bloquée de la part du FAI.

Il faut être particulièrement prudent lors d&#39;opérations sur la base :

* Les imports doivent être soigneusement paramétrés, en particulier dans le choix de la clé de réconciliation.
* Les modifications d’adresses e-mail peuvent également être source de doublons. En particulier, deux adresses ayant des domaines différents peuvent être acheminées vers la même boîte aux lettres, par exemple si une société a changé de nom et a conservé l&#39;ancien domaine pendant un certain temps : joe.doe@amce-co.com et joe.doe@acme-rebranded.com.
* Les imports automatiques, qu’il s’agisse de listes ou d’autres bases de données, sont des éléments à prendre en compte lors de la gestion des profils. Que se passe-t-il si on supprime ou on déplace un profil dans une autre partition ? Il peut être recréé dans la partition initiale par une importation automatique, par exemple lorsqu&#39;un bon de commande est passé.
* Le rangement des profils dans des dossiers différents peut être mise en oeuvre à l&#39;aide de vues plutôt que de partitions. Ainsi on s&#39;assure que les profils sont physiquement dans la même partition tout en permettant un affichage et une gestion des droits adéquats.

Il existe tout de même des cas où la présence de doublons entre différentes partitions est normale. Par exemple, lorsqu’on opère des envois pour le compte de sociétés ou d’entités différentes, il est logique qu’une même personne puisse être adressée à des titres différents. Il est cependant rarement normal de trouver des doublons dans une même partition.

## Ressources spécifiques au produit

Pour garantir votre réputation et assurer une bonne gestion des quarantaines, dédupliquez les adresses. Pour en savoir plus, consultez les sections suivantes de la documentation du produit :

**Adobe Campaign Classic**

* [Activité Déduplication](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/targeting-activities/deduplication.html)
* [Utilisation de la fonctionnalité de fusion de l’activité Déduplication](https://experienceleague.adobe.com/docs/campaign-classic/using/automating-with-workflows/use-cases/data-management/deduplication-merge.html?lang=fr)

**Adobe Campaign Standard**

* [Dédupliquer les données d&#39;un fichier importé](https://experienceleague.adobe.com/docs/campaign-standard/using/managing-processes-and-data/workflow-use-case/data-management/deduplicating-data-imported-file.html)
