# 📊 Card Transactions Visualisation with Power BI

## 📝 Description

Ce rapport Power BI permet d’analyser les transactions bancaires effectuées **en ligne et en magasin** entre Janvier 2010 et Octobre 2019 par 2000 utilisateurs. Il offre une vue détaillée sur :

* Les tendances des transactions réalisées 
* Le suivi des transactions rejetées et leurs causes
* La répartition géographique des commerçants chez lesquels les transactions ont été réalisées
* Le profil démographique des utilisateurs de cartes (âge, score de crédit, salaire, etc.)
* L’analyse des comportements individuels via une fiche client
* Le suivi des clients endettés selon différentes tranches d'endettement

Ce tableau de bord peut être destiné à plusieurs équipes métiers :

* Les analystes des **tendances de transactions**, voires des ventes
* Les équipes **CRM et marketing** afin de connaître la démographie et le profil des détenteurs des cartes bancaires
* Les **conseillers bancaires** pour l’analyse individuelle des habitudes du client et la gestion des dettes

---

## 🔌 Sources de données

* 📂 **Fichiers Excel et Json** : user_datan transaction_data, cards_data, mcc_json
* 📥 Mode d’importation : **Import**
* 📅 Données mises à jour manuellement (sauf automatisation externe)

---

## 🔧 Préparation des données & Modélisation


### Transformations Power Query
* Nettoyage et enrichissement des données (filtrage, suppression des doublons et de colonne, correction des formats)
* Fusion de plusieurs sources Excel en tables cohérentes
* Creation de la table Ajout de colonnes temporelles pour faciliter l’analyse (année, trimestre, mois)
* Creation de la table "merchant" à partir du fichier "transaction_data": import d'un fichier ad-hoc et creation d'une table de correspondance pour les données manquantes, jointure de tables.

### Modélisation et calculs DAX

Nous avons choisi dune modélisation en flocon par choix même si le schéma en étoile est réputé pour avoir de meilleures performances et faciliter l'écriture des mesures DAX

* Création des relations entre les tables (transactions, clients, commerçants)
* Creation de tables calculées dont une bridge table pour éviter les relations N - N
* Mesures clés calculées en DAX pour les indicateurs métiers (ex : taux de réussite, montant moyen par transaction, total dépensé par client) _voir fichier liste de mesures DAX_
* Colonnes calculées pour segmenter les clients selon score de crédit, tranche d’âge, et état d’endettement
* Création de paramètre de champs et mise en place de KPI dynamiques pour piloter les visuels interactifs
  
![Semantic model.png](https://github.com/jmarielaure/Card-transactions-analysis-BI/blob/main/dashboard%20screenshot/Semantic%20model.png)
---

## 🧾 Pages du rapport

Un aperçu de chaque page mentionnée ci-dessous est disponible [ici](https://github.com/jmarielaure/Card-transactions-analysis-BI/tree/main/dashboard%20screenshot).


1. **Approuved transaction**  
   → Vue globale des volumes de transactions réussies et de leur évolution temporelle.
   Cette page permet aussi de visualiser certains KPI classiques tel que la valeur et le nombre de transaction ou encore le taux de transactions converties

2. **Declined Transactions**  
   → Analyse des transactions rejetées avec mise en évidence des causes.

3. **Merchants**  
   → Visualisation géographique des commerçants chez lesquels les achats ont été effectués.

4. **Demographics**  
   → Profil des utilisateurs : âge, score de crédit, salaire, statut de crédit.

5. **Client Profile**  
   → Analyse individuelle d’un client : tendances de dépenses, répartition par type d’achat, liste des transactions, etc.

6. **Debtors table (via sélection ou drill-through)**  
   → Focus sur les clients endettés avec filtrage par tranches (score, salaire, etc.) et possibilité d’explorer certaines informations dont le ratio detets vs revenu.

![(dashboard screenshot/rejected transactions page.png)](https://github.com/jmarielaure/Card-transactions-analysis-BI/blob/main/dashboard%20screenshot/rejected%20transactions%20page.png)
*Declined transactions page*  

---


## 🧮 Exemple de KPI & Mesures Clés

* 💳 Nombre total de transactions: plus de **13 095k transactions**  en 8 ans.
* ✅ Taux de transactions réussies vs échouées : **98 %** des transactions sont approuvées
* 📉 Taux de rejet & cause dominante: 2 % des transactions ont échoué, dont 62 % en raison d'un solde insuffisant.
* 🌍 Répartition des transactions par commerçants: la majorité des transactions ont eu lieu en Amérique du Nord, avec 50 % du volume total
* 👤 Nombre d’utilisateurs par tranche d’âge / score / revenu / etc. :  Le groupe majoritaire chez les utilisateurs sont les 45-54 ans, avec un _'credit score'_ supérieure à 710.
* 🧾 Montant moyen par transaction: environ 41 € par transaction hors ligne approuvée et 57 € par transaction en ligne approuvée
* 🕵️ Focus par client spécifique (total dépensé, catégtories de dépenses, liste des transactions réalisées)
* 🔴 Nombre de débiteurs par tranche: 95 % des utilisateurs ont une dette et pour 80 % d'entre eux cette dette est inférieure à 100 000 €.

---

## ⚠️ Limitations connues

* 📁 Mise à jour manuelle (pas de pipeline de rafraîchissement automatique) - à venir dans un prochain projet
* Certains éléments pourraient être fait en amont (colonnes ou tables calculés dans DAX). Toutefois un objectif personnel étant de davantage travailler avec DAX, des choix moins stratégiques ont été réalisés.
---

## 🔮 Améliorations futures

* Connexion automatisée à une base de données transactionnelle ou dans un environnement professionel au système traitant les transactions et données clients (ERP et CRM)
* Ajout d’un système d’alertes (ex. : pic anormal de rejets) si publication sur Power BI service
* Segmentation comportementale plus avancée
* Plus de visuels permettant d'identifier des corrélations entre des KPI

---

## 👥 Contributeur

* **Auteur** : jmarielaure - projet personnel
  

---
