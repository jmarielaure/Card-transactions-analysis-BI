# 📊 Card Transactions Visualisation with Power BI

## 📝 Description

Ce rapport Power BI permet d’analyser les transactions par carte bancaire effectuées **en ligne et en physique** sur une période donnée. Il offre une vue détaillée sur :

* Les tendances des transactions réalisées 
* Le suivi des transactions rejetées et leurs causes
* La répartition géographique des commerçants chez lesquels les transactions ont été réalisées
* Le profil démographique des utilisateurs de cartes (âge, score de crédit, salaire, etc.)
* L’analyse des comportements individuels via une fiche client
* Le suivi des clients endettés selon différentes tranches d'endettement

Ce tableau de bord est destiné à plusieurs équipes métiers :

* Les analystes des **tendances de transaction**
* Les équipes **CRM et marketing** pour la segmentation des clients
* Les **conseillers bancaires** pour l’analyse individuelle et la gestion des dettes

---

## 🔌 Sources de données

* 📂 **Fichiers Excel et Json** : user_datan transaction_data, cards_data, mcc_json
* 📥 Mode d’importation : **Import**
* 📅 Données mises à jour manuellement (sauf automatisation externe)

---

## 🔧 Préparation des données & Modélisation

Nous avons choisi dune modélisation en flocon par choix même si le schéma en étoile est réputé pour avoir de meilleurs performance et faciliter l'écriture des mesures DAX

### Transformations Power Query
* Nettoyage et enrichissement des données (filtrage, suppression des doublons et de colonne, correction des formats)
* Fusion de plusieurs sources Excel en tables cohérentes
* Creation de la table Ajout de colonnes temporelles pour faciliter l’analyse (année, trimestre, mois)

### Modélisation et calculs DAX
* Création des relations entre les tables (transactions, clients, commerçants)
* Creation de tables calculées dont une bridge table pour éviter les relations N - N
* Mesures clés calculées en DAX pour les indicateurs métiers (ex : taux de réussite, montant moyen par transaction, total dépensé par client)
* Colonnes calculées pour segmenter les clients selon score de crédit, tranche d’âge, et état d’endettement
* Création de paramètre de champs et mise en place de KPI dynamiques pour piloter les visuels interactifs
* Utilisation des fonctions DAX avancées pour les analyses temporelles (YTD, variations mensuelles)

---

## 🧾 Pages du rapport

1. **Approuved transaction**  
   → Vue globale des volumes de transactions réussies et de leur évolution temporelle.
   Cette page permet aussi de visualiser certains KPI classiques tel que la valeur et le nombre de transaction ou encore le taux de transactions converties

3. **Declined Transactions**  
   → Analyse des transactions rejetées avec mise en évidence des causes.

4. **Merchant Map**  
   → Visualisation géographique des commerçants chez lesquels les achats ont été effectués.

5. **Demographic**  
   → Profil des utilisateurs : âge, score de crédit, salaire, statut de crédit.

6. **Client Profile**  
   → Analyse individuelle d’un client : tendances de dépenses, répartition par type d’achat, liste des transactions, etc.

7. **Debtors (via sélection ou drill-through) **  
   → Focus sur les clients endettés avec filtrage par tranches (score, salaire, etc.) et possibilité d’explorer leurs comportements.

---

## 🧮 KPI & Mesures Clés

* 💳 Nombre total de transactions
* ✅ Taux de transactions réussies vs échouées
* 📉 Taux de rejet & cause dominante
* 🌍 Répartition des commerçants
* 👤 Nombre d’utilisateurs par tranche d’âge / score / revenu
* 🧾 Montant moyen par transaction
* 🕵️ Focus client (total dépensé, fréquence, types de marchands)
* 🔴 Nombre de débiteurs par tranche

---

## 🛠️ Utilisation

* Ouvrir le fichier `.pbix` avec **Power BI Desktop** (dernière version conseillée)
* Naviguer via le menu de pages
* Utiliser les **filtres contextuels et les slicers** pour explorer les données
* Utiliser les **drill-through** pour aller d’une vue globale vers une vue individuelle (ex. : Client Profile, Debtors)

---

## ⚠️ Limitations connues

* 📁 Mise à jour manuelle (pas de pipeline de rafraîchissement automatique)
* 📊 Données Excel → risque d’erreurs si format modifié
* 📉 Performances à surveiller si le volume de données augmente fortement

---

## 🔮 Améliorations futures

* Connexion automatisée à une base de données transactionnelle
* Ajout d’un système d’alertes (ex. : pic anormal de rejets)
* Dashboard mobile optimisé
* Segmentation comportementale plus avancée

---

## 👥 Contributeur

* **Auteur** : *(à compléter avec ton nom ou ton pseudo)*  
* **Rôle** : Création du rapport, modélisation des données, design des pages Power BI

---
