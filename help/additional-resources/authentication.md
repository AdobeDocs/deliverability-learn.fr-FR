---
title: Authentification
description: En savoir plus sur les méthodes d’authentification SPF, DKIM et DMARC.
topics: Deliverability
doc-type: article
activity: understand
team: ACS
exl-id: 03609139-b39b-4051-bcde-9ac7c5358b87
source-git-commit: d6094cd2ef0a8a7741e7d8aa4db15499fad08f90
workflow-type: tm+mt
source-wordcount: '757'
ht-degree: 42%

---

# Authentification

## SPF {#spf}

SPF (Sender Policy Framework) est une norme d’authentification d’email qui permet au propriétaire d’un domaine de spécifier les serveurs de messagerie autorisés à envoyer des emails pour le compte de ce domaine. Cette norme utilise le domaine indiqué dans l’en-tête « Return-Path » de l’e-mail (également appelé adresse « Envelope From »).

>[!NOTE]
>
>Vous pouvez utiliser [cet outil externe](https://www.kitterman.com/spf/validate.html) pour vérifier un enregistrement SPF.

La technique SPF permet, dans une certaine mesure, de s&#39;assurer que le nom de domaine utilisé dans un email n&#39;est pas usurpé. Lorsqu’un message provient d’un domaine, le serveur DNS du domaine est interrogé. Il répond par un enregistrement court (enregistrement SPF) détaillant les serveurs autorisés à envoyer des emails depuis ce domaine. Si nous supposons que seul le propriétaire du domaine a les moyens de modifier cet enregistrement, nous pouvons considérer que cette technique ne permet pas de falsifier l’adresse de l’expéditeur, du moins pas la partie située à droite du « @ ».

Dans la dernière [spécification RFC 4408](https://www.rfc-editor.org/info/rfc4408), deux éléments du message sont utilisés pour déterminer le domaine considéré comme l’expéditeur : le domaine spécifié par la commande SMTP &quot;HELO&quot; (ou &quot;EHLO&quot;) et le domaine spécifié par l’adresse de l’en-tête &quot;Return-Path&quot; (ou &quot;MAIL FROM&quot;), qui est également l’adresse de rebond. Différentes considérations permettent de ne prendre en compte que l’une de ces valeurs ; nous vous recommandons de vous assurer que les deux sources spécifient le même domaine.

La vérification SPF produit une évaluation de la validité du domaine expéditeur :

* **None** : aucune évaluation n’a pu être effectuée.
* **Neutral** : le domaine interrogé ne permet pas l’évaluation.
* **Pass** : le domaine est considéré comme authentique.
* **Fail** : le domaine est usurpé et le message doit être rejeté.
* **SoftFail** : le domaine est probablement usurpé, mais le message ne doit pas être rejeté en fonction de ce résultat.
* **TempError** : une erreur temporaire a interrompu l’évaluation. Le message peut être rejeté.
* **PermError** : les enregistrements SPF du domaine sont incorrects.

Il faut bien noter que les modifications des enregistrements au niveau des serveurs DNS peuvent mettre jusqu&#39;à 48 heures pour être prises en compte. Ce délai est en fonction de la fréquence de rafraîchissement des caches DNS des serveurs de réception.

## DKIM {#dkim}

L’authentification DKIM (DomainKeys Identified Mail) est un successeur de SPF. Il utilise la cryptographie à clé publique qui permet au serveur de messagerie de réception de vérifier qu’un message a bien été envoyé par la personne ou l’entité revendiquant l’envoi, et si le contenu du message a été modifié entre le moment où il a été envoyé (et &quot;signé&quot; par DKIM) et celui où il a été reçu. Cette norme utilise généralement le domaine dans l’en-tête « From » ou « Sender ».

DKIM est né de l&#39;union des principes d&#39;authentification DomainKeys, de Yahoo! et Identified Internet Mail, de Cisco et va permettre de vérifier l&#39;authenticité du domaine expéditeur et garantir l&#39;intégrité du message.

DKIM a remplacé l&#39;authentification **DomainKeys**.

L&#39;utilisation de DKIM nécessite quelques prérequis :

* **Sécurité** : le chiffrement est un élément clé du DKIM. Pour garantir le niveau de sécurité du DKIM, la taille de cryptage recommandée est 1024b. Les clés DKIM inférieures ne sont pas considérées comme valides par la majorité des fournisseurs d’accès.
* **Réputation** : la réputation est basée sur l’IP et/ou le domaine, mais le sélecteur DKIM moins transparent est également un élément clé à prendre en compte. Le choix du sélecteur est important : évitez de conserver celui &quot;par défaut&quot; qui peut être utilisé par n’importe qui et qui a donc une mauvaise réputation. Vous devez mettre en oeuvre un sélecteur différent pour les **communications de rétention/acquisition** et pour l’authentification.

En savoir plus sur les conditions préalables DKIM lors de l&#39;utilisation de Campaign Classic dans [cette section](/help/additional-resources/acc-technical-recommendations.md#dkim-acc).

## DMARC {#dmarc}

DMARC (Domain-based Message Authentication, Reporting and Conformance) est la forme la plus récente d’authentification des emails. Le processus s’appuie simultanément sur l’authentification SPF et DKIM pour déterminer si un email sera diffusé avec succès ou non. DMARC est unique et puissant sur deux plans importants :

* Conformité : il permet à l&#39;expéditeur de donner aux FAI des instructions sur ce qu&#39;il doit faire de tout message qui ne parvient pas à s&#39;authentifier (par exemple : ne pas l&#39;accepter).
* Reporting : il fournit à l’expéditeur un rapport détaillé indiquant tous les messages qui ont échoué à l’authentification DMARC, ainsi que le domaine &quot;De&quot; et l’adresse IP utilisée pour chacun d’eux. Cela permet à une entreprise d’identifier les emails légitimes qui ne s’authentifient pas et qui nécessitent un type de &quot;correctif&quot; (par exemple, l’ajout d’adresses IP à leur enregistrement SPF), ainsi que les sources et la prévalence des tentatives de phishing sur leurs domaines de messagerie.

>[!NOTE]
>
>DMARC peut utiliser les rapports générés par [250ok](https://250ok.com/).
