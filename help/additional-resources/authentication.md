---
title: Authentification
description: En savoir plus sur les méthodes d’authentification SPF, DKIM et DMARC.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 03609139-b39b-4051-bcde-9ac7c5358b87
TQID: https://experienceleague.adobe.com/zuhBmNWmF8CoCSNofsg3FKCcQFLOFfZmRutB2P1L4-U
product_v2:
  - id: b27e5950-9033-45ac-9f86-eb22e567f615
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
feature_v2:
  - id: ea90ebee-5c84-42d9-8b21-006bdabc95a3
  - id: f71e690b-4480-4b67-9ef5-88f42f9cdfdb
role_v2:
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
  - id: f8a45b24-4be7-4f1b-909b-60d06b483a20
level_v2:
  - id: e8ccd51f-da0d-4e3b-939b-e30d5ebb1ea5
topic_v2:
  - id: aa2f3246-cb95-4b30-8899-fdf7d73550cc
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: 75df8537199680e5f1fc4b98cefdb05220fee7bf
workflow-type: tm+mt
source-wordcount: 769
ht-degree: 33%

---

# Authentification

## SPF {#spf}

SPF (Sender Policy Framework) est une norme d’authentification d’email qui permet au propriétaire d’un domaine de spécifier les serveurs de messagerie autorisés à envoyer des emails pour le compte de ce domaine. Cette norme utilise le domaine indiqué dans l’en-tête « Return-Path » de l’e-mail (également appelé adresse « Envelope From »).

>[!NOTE]
>
>Vous pouvez utiliser [cet outil externe](https://www.kitterman.com/spf/validate.html) pour vérifier un enregistrement SPF.

Le SPF est une technique qui, dans une certaine mesure, permet de s’assurer que le nom de domaine utilisé dans un e-mail n’est pas falsifié. Lorsqu’un message provient d’un domaine, le serveur DNS du domaine est interrogé. Il répond par un enregistrement court (enregistrement SPF) détaillant les serveurs autorisés à envoyer des emails depuis ce domaine. Si nous supposons que seul le propriétaire du domaine a les moyens de modifier cet enregistrement, nous pouvons considérer que cette technique ne permet pas de falsifier l’adresse de l’expéditeur, du moins pas la partie située à droite du « @ ».

Dans la dernière spécification [RFC 4408](https://www.rfc-editor.org/info/rfc4408), deux éléments du message sont utilisés pour déterminer le domaine considéré comme l&#39;expéditeur : le domaine spécifié par la commande SMTP « HELO » (ou « EHLO ») et le domaine spécifié par l&#39;adresse de l&#39;en-tête « Return-Path » (ou « MAIL FROM »), qui est également l&#39;adresse de rebond. Différentes considérations permettent de ne prendre en compte que l’une de ces valeurs ; nous vous recommandons de vous assurer que les deux sources spécifient le même domaine.

La vérification SPF produit une évaluation de la validité du domaine expéditeur :

* **Aucune** : aucune évaluation n’a pu être effectuée.
* **Neutre** : le domaine interrogé ne permet pas d&#39;évaluer.
* **Pass** : le domaine est considéré comme authentique.
* **Échec** : le domaine est falsifié et le message doit être rejeté.
* **SoftFail** : le domaine est probablement falsifié, mais le message ne doit pas être rejeté sur la seule base de ce résultat.
* **TempError** : une erreur temporaire a interrompu l’évaluation. Le message peut être rejeté.
* **PermError** : les enregistrements SPF du domaine sont incorrects.

Il est à noter que les enregistrements effectués au niveau des serveurs DNS peuvent prendre jusqu’à 48 heures pour être pris en compte. Ce délai dépend de la fréquence d’actualisation des caches DNS des serveurs de réception.

## DKIM {#dkim}

L&#39;authentification DKIM (DomainKeys Identified Mail) succède à SPF. Il utilise une cryptographie à clé publique qui permet au serveur de messagerie de réception de vérifier qu&#39;un message a bien été envoyé par la personne ou l&#39;entité par laquelle il prétend avoir été envoyé, et si le contenu du message a été modifié entre le moment où il a été initialement envoyé (et le moment où DKIM a « signé ») et le moment où il a été reçu. Cette norme utilise généralement le domaine dans l’en-tête « From » ou « Sender ».

DKIM provient d&#39;une combinaison des DomainKeys, Yahoo ! et les principes d&#39;authentification Cisco Identified Internet Mail et est utilisé pour vérifier l&#39;authenticité du domaine de l&#39;expéditeur et garantir l&#39;intégrité du message.

DKIM a remplacé l&#39;authentification **DomainKeys**.

L&#39;utilisation de DKIM nécessite quelques prérequis :

* **Sécurité** : le chiffrement est un élément essentiel du DKIM. Pour garantir le niveau de sécurité du DKIM, 1024b est la taille de chiffrement recommandée. Les clés DKIM inférieures ne sont pas considérées comme valides par la majorité des fournisseurs d&#39;accès.
* **Réputation** : la réputation dépend de l’adresse IP et/ou du domaine, mais le sélecteur DKIM le moins transparent est également un élément essentiel à prendre en compte. Le choix du sélecteur est important : évitez de conserver celui par défaut qui peut être utilisé par n&#39;importe qui et qui a donc une mauvaise réputation. Vous devez implémenter un sélecteur différent pour les communications **rétention vs acquisition** et pour l’authentification.

En savoir plus sur les conditions préalables requises pour DKIM lors de l’utilisation de Campaign Classic dans [cette section](/help/additional-resources/acc-technical-recommendations.md#dkim-acc).

## DMARC {#dmarc}

DMARC (Domain-based Message Authentication, Reporting and Conformance) est la forme la plus récente d’authentification des emails. Le processus s’appuie simultanément sur l’authentification SPF et DKIM pour déterminer si un email sera diffusé avec succès ou non. DMARC est unique et puissant de deux manières importantes :

* Conformité : elle permet à l’expéditeur d’indiquer aux FAI comment traiter un message dont l’authentification a échoué (par exemple, ne pas l’accepter).
* Reporting : il fournit à l’expéditeur un rapport détaillé indiquant tous les messages qui ont échoué lors de l’authentification DMARC, ainsi que le domaine « From » et l’adresse IP utilisée pour chacun d’eux. Cela permet à une entreprise d’identifier les e-mails légitimes qui ne parviennent pas à s’authentifier et qui ont besoin d’un certain type de « correctif » (par exemple, l’ajout d’adresses IP à leur enregistrement SPF), ainsi que les sources et la prévalence des tentatives d’hameçonnage sur leurs domaines de messagerie.

>[!NOTE]
>
>DMARC peut utiliser les rapports générés par [250ok](https://250ok.com/).
