---
title: Authentification
description: En savoir plus sur les méthodes d’authentification SPF, DKIM et DMARC.
feature: Additional resources
topics: Deliverability
kt: null
thumbnail: null
doc-type: article
activity: understand
team: ACS
translation-type: tm+mt
source-git-commit: 1e539b5df54250a5927701009e7a9c84e5d73fae
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 51%

---


# Authentification

## SPF {#spf}

SPF (Sender Policy Framework) est une norme d’authentification d’email qui permet au propriétaire d’un domaine de spécifier les serveurs de messagerie autorisés à envoyer des emails pour le compte de ce domaine. Cette norme utilise le domaine indiqué dans l’en-tête « Return-Path » de l’email (également appelé adresse « Envelope From »).

>[!NOTE]
>
>Vous pouvez utiliser [cet outil externe](https://www.kitterman.com/spf/validate.html) pour vérifier un enregistrement SPF.

La technique SPF permet, dans une certaine mesure, de vous assurer que le nom de domaine utilisé dans un email n’est pas usurpé. Lorsqu’un message provient d’un domaine, le serveur DNS du domaine est interrogé. Il répond par un enregistrement court (enregistrement SPF) détaillant les serveurs autorisés à envoyer des emails depuis ce domaine. Si nous supposons que seul le propriétaire du domaine a les moyens de modifier cet enregistrement, nous pouvons considérer que cette technique ne permet pas de falsifier l’adresse de l’expéditeur, du moins pas la partie située à droite du « @ ».

Dans la dernière spécification [RFC 4408](https://www.rfc-editor.org/info/rfc4408), deux éléments du message sont utilisés pour déterminer le domaine considéré comme l&#39;expéditeur : le domaine spécifié par la commande SMTP &quot;HELO&quot; (ou &quot;EHLO&quot;) et le domaine spécifié par l&#39;adresse de l&#39;en-tête &quot;Return-Path&quot; (ou &quot;MAIL FROM&quot;), qui est également l&#39;adresse de rebond. Différentes considérations permettent de ne prendre en compte que l’une de ces valeurs ; nous vous recommandons de vous assurer que les deux sources spécifient le même domaine.

La vérification SPF produit une évaluation de la validité du domaine expéditeur :

* **None** : aucune évaluation n’a pu être faite.
* **Neutral** : le domaine interrogé ne permet pas l’évaluation.
* **Pass** : le domaine est considéré comme authentique.
* **Fail** : le domaine est certainement usurpé, le message devrait être rejeté.
* **SoftFail** : Le domaine est probablement falsifié mais le message ne doit pas être rejeté uniquement en fonction de ce résultat.
* **TempError** : une erreur temporaire a interrompu l’évaluation. Le message peut être rejeté.
* **PermError** : les enregistrements SPF du domaine sont incorrects.

Il faut bien noter que les modifications des enregistrements au niveau des serveurs DNS peuvent mettre jusqu&#39;à 48 heures pour être prises en compte. Ce délai est en fonction de la fréquence de rafraîchissement des caches DNS des serveurs de réception.

## DKIM {#dkim}

L&#39;authentification DKIM (DomainKeys Identified Mail) est un successeur de SPF. Il utilise la cryptographie à clé publique qui permet au serveur de messagerie de réception de vérifier qu&#39;un message a bien été envoyé par la personne ou l&#39;entité qui prétend l&#39;avoir envoyé et si le contenu du message a été modifié entre le moment où il a été envoyé initialement (et celui où DKIM a &quot;signé&quot;) et celui où il a été reçu. Cette norme utilise généralement le domaine dans l’en-tête « From » ou « Sender ».

DKIM est né de l&#39;union des principes d&#39;authentification DomainKeys, de Yahoo! et Identified Internet Mail, de Cisco et va permettre de vérifier l&#39;authenticité du domaine expéditeur et garantir l&#39;intégrité du message.

DKIM a remplacé l&#39;authentification **DomainKeys**.

L&#39;utilisation de DKIM nécessite quelques prérequis :

* **Sécurité** : Le chiffrement est un élément clé du DKIM. Pour garantir le niveau de sécurité du DKIM, la valeur 1024b est la meilleure pratique recommandée pour la taille de chiffrement. Les clés DKIM inférieures ne sont pas considérées comme valides par la majorité des fournisseurs d’accès.
* **Réputation** : La réputation est basée sur l&#39;IP et/ou le domaine, mais le sélecteur DKIM moins transparent est aussi un élément clé à prendre en compte. Le choix du sélecteur est important : évitez de conserver le &quot;défaut&quot; qui peut être utilisé par n&#39;importe qui et qui a donc une mauvaise réputation. Vous devez implémenter un autre sélecteur pour les communications **de rétention par rapport à l’acquisition** et pour l’authentification.

Pour en savoir plus sur le prérequis DKIM lors de l&#39;utilisation du Campaign Classic dans [cette section](/help/additional-resources/acc-technical-recommendations.md#dkim-acc).

## DMARC {#dmarc}

DMARC (Domain-based Message Authentication, Reporting and Conformance) est la forme la plus récente d’authentification des emails. Le processus s’appuie simultanément sur l’authentification SPF et DKIM pour déterminer si un email sera diffusé avec succès ou non. DMARC est unique et puissant de deux manières importantes :

* Conformité : permet à l&#39;expéditeur d&#39;indiquer aux FAI ce qu&#39;il faut faire avec tout message qui ne s&#39;authentifie pas (par exemple : ne l&#39;acceptez pas).
* Rapports : fournit à l&#39;expéditeur un rapport détaillé montrant tous les messages qui ont échoué à l&#39;authentification DMARC, ainsi que le domaine &quot;De&quot; et l&#39;adresse IP utilisés pour chacun d&#39;eux. Cela permet à une société d&#39;identifier les courriels légitimes qui ne sont pas authentifiés et qui nécessitent un certain type de &quot;correctif&quot; (par exemple, l&#39;ajout d&#39;adresses IP à leur enregistrement SPF), ainsi que les sources et la fréquence des tentatives d&#39;hameçonnage sur leurs domaines de courriel.

>[!NOTE]
>
>DMARC peut utiliser les rapports générés par [250ok](https://250ok.com/).
