---
title: Présentation de la stratégie de délivrabilité et définition de la délivrabilité
description: Découvrez comment la délivrabilité est définie, pourquoi elle est importante et quelles en sont les mesures clés.
topics: Deliverability
jira: KT-5255
thumbnail: kt5255.jpg
doc-type: article
activity: understand
team: ACS
exl-id: 5285eda9-5099-48d5-b150-ce2c376ee549
source-git-commit: 9444f8601f2f349398ee5deb9d5f4d4f7abb44f5
workflow-type: ht
source-wordcount: '843'
ht-degree: 100%

---

# Stratégie et définition de la délivrabilité

Le succès des campagnes marketing par e-mail dépend de la compréhension des objectifs marketing, qu’il s’agisse de prospection ou d’initiatives de gestion de la relation client (GRC) Cela permet de déterminer qui cibler, quoi promouvoir et quand communiquer.

Voici quelques exemples d’objectifs de stratégie de marketing par email :

* Acquisition de nouveaux clients
* Conversion de prospects en nouveaux acheteurs
* Croissance des relations client actuelles avec des offres client supplémentaires
* Conservation des clients fidèles
* Amélioration de la satisfaction des clients et leur fidélité à la marque
* Réactivation des clients perdus ou obsolètes

## Définition de la délivrabilité

Deux mesures clés jouent un rôle dans la définition de la délivrabilité. Le *taux de délivrabilité* correspond au pourcentage d&#39;emails qui ne sont pas retournés et qui sont acceptés par le FAI. Le *placement dans la boîte de réception* s&#39;applique aux messages qui sont acceptés par le FAI et détermine si l&#39;email arrive dans la boîte de réception ou dans le dossier de courriers indésirables.

Il est important de comprendre à la fois le taux de délivrabilité et le taux de placement dans la boîte de réception lors de la mesure des performances des emails. Un taux de délivrabilité élevé n&#39;est pas la seule facette de la délivrabilité. Ce n’est pas parce qu’un message est reçu par l’intermédiaire du point de contrôle initial d’un FAI que votre abonné a réellement consulté votre communication et interagi avec celle-ci.

## Importance de la délivrabilité

Vous devriez savoir si vos emails sont diffusés ou s’ils arrivent dans la boîte de réception ou le dossier des courriers indésirables. Voici pourquoi.

De nombreuses heures sont consacrées à la planification et à la production des campagnes par e-mail. Si les email sont retournés ou s’ils finissent dans le dossier des courriers indésirables de vos abonnés, vos clients ne les liront probablement pas, votre appel à l&#39;action ne sera pas entendu et vous ne serez pas en mesure de réaliser vos objectifs en matière de chiffre d’affaires en raison de conversions perdues. En d’autres termes, vous ne pouvez pas vous permettre d’ignorer la délivrabilité. Celle-ci est essentielle au succès de vos efforts de marketing par e-mail et à vos bénéfices.

Suivez les bonnes pratiques en matière de délivrabilité pour vous assurer que votre email aura les meilleures chances d&#39;être ouvert, de faire l&#39;objet d&#39;un clic et d&#39;atteindre l&#39;objectif de conversion. Vous pouvez trouver un objet accrocheur, présenter de belles images et un contenu attrayant, mais si l’email n’est pas diffusé, le client n’aura aucune opportunité de conversion. Dans le cadre de la délivrabilité des emails, chaque étape du processus d&#39;acceptation des emails dépend de la précédente pour le succès du programme.

### Étape 1 : diffusion de l’email

Facteurs importants pour la diffusion :

* **Infrastructure solide** : configuration des adresses IP et du domaine, configuration de la feedback loop (y compris le suivi et le traitement des plaintes) et traitement régulier des bounces. Pour ses clients, Adobe est chargé de cette configuration pour le compte de nos clients.
* **Authentification renforcée** : [!DNL Sender Policy Framework] (SPF), [!DNL DomainKeys Identified Mail] (DKIM),[!DNL Domain-based Message Authentication], reporting et conformité (DMARC).
* **Liste de qualité supérieure** : opt-in explicite, méthodes d’acquisition des emails valides et politiques d’engagement.
* **Cadence d&#39;envoi constante et minimisation des fluctuations de volume**.
* **Bonne réputation des adresses IP et des domaines**.

### Étape 2 : placement dans la boîte de réception des emails

Les FAI disposent d’algorithmes uniques, complexes et en constante évolution pour déterminer si votre email doit être placé dans la boîte de réception ou le dossier des courriers indésirables.

Voici quelques facteurs importants pour le placement dans les boîtes de réception :

* Email diffusé
* Engagement élevé
* Faibles plaintes (moins de 0,1 % dans l&#39;ensemble)
* Volume cohérent
* Pièges de messages indésirables faibles
* Taux de hard bounces faible
* Problèmes liés à un manque de liste bloquée

### Étape 3 : engagement emailing — ouvertures

Voici quelques facteurs importants concernant le taux d&#39;ouverture :

* Email diffusé et arrivé dans la boîte de réception
* Reconnaissance de la marque
* Objet et en-têtes attrayants
* Personnalisation
* Fréquence
* Pertinence ou valeur du contenu

### Étape 4 : engagement emailing — clics

Voici quelques facteurs importants concernant le taux de clic :

* Email diffusé, arrivé dans la boîte de réception et ouvert
* Fort appel à l’action
   * Il s&#39;agit de l&#39;action principale que vous voulez obtenir de votre audience. Normalement, il s’agit d’un clic sur une URL. Vérifiez que celle-ci est claire et facile à trouver pour l’utilisateur.
* Pertinence ou valeur du contenu

### Étape 5 : conversion

Voici quelques facteurs importants concernant la conversion :

* Tous les éléments ci-dessus
* Transition de l&#39;e-mail via une URL vers une page de destination ou une page de vente
* Expérience relative à la page de destination
* Reconnaissance de la marque, perception et fidélité

### Impact potentiel sur le chiffre d’affaires

La conversion est essentielle, mais quelle est l&#39;alternative ? Votre stratégie de délivrabilité peut renforcer ou affaiblir votre programme de marketing par email. Le graphique ci-après montre la perte potentielle de chiffre d’affaires qu&#39;une politique de délivrabilité inadaptée peut entraîner sur votre programme marketing. Comme nous l&#39;avons montré, pour une entreprise qui a un taux de conversion de 2 % et un achat moyen de 100 $, chaque réduction de 10 % du placement dans la boîte de réception équivaut à une perte de chiffre d’affaires de près de 20 000 $. Souvenez-vous que ces chiffres sont uniques pour chaque expéditeur.

| Envoyés | Pourcentage | Délivrés | Pourcentage | Boîte de réception | Nombre non présent dans la boîte de réception | Taux de conversion | Nombre de pertes | moyen | Perte de |
|------|-----------|-----------|----------|-------|---------------------|-----------------|-----------------|----------|-----------|
|      | Diffusé |           | Boîte de réception |       |                     |                 | de conversions | Achat | chiffre d’affaires |
| 100 000 | 99 % | 99 000 | 100 % | 99 000 | - | 2 % | 0 | 100 USD | USD - |
| 100 000 | 99 % | 99 000 | 90 % | 89 100 | 9,900 | 2 % | 198 | 100 USD | 19 800 USD |
| 100 000 | 99 % | 99 000 | 80 % | 79 200 | 19 800 | 2 % | 396 | 100 USD | 39 600 USD |
| 100 000 | 99 % | 99 000 | 70 % | 69 300 | 29 700 | 2 % | 594 | 100 USD | 59 400 USD |
| 100 000 | 99 % | 99 000 | 60 % | 59 400 | 39 600 | 2 % | 792 | 100 USD | 79 200 |
| 100 000 | 99 % | 99 000 | 50 % | 49 500 | 49 500 | 2 % | 990 | 100 USD | 99 000 |
| 100 000 | 99 % | 99 000 | 40 % | 39 600 | 59 400 | 2 % | 1 188 | 100 USD | 118 800 USD |
| 100 000 | 99 % | 99 000 | 30 % | 29 700 | 69 300 | 2 % | 1 386 | 100 USD | 138 600 USD |
| 100 000 | 99 % | 99 000 | 20 % | 19 800 | 79 200 | 2 % | 1 584 | 100 USD | 158 400 |
