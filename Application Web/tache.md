# Tâches de développement — Application Web VitaCare
 
> Liste exhaustive de tout ce qu'il y a à **coder** pour l'application web.
> Les éléments de conception (wireframes, MCD, schéma d'architecture, rapports, PPT) ne figurent **pas** ici.
> Contraintes techniques imposées : **HTML, CSS, JavaScript, React, PHP, MySQL** avec séparation frontend/backend, validations client **et** serveur, gestion des sessions, protection contre les vulnérabilités web classiques.
 
---
 
## 0. Mise en place du projet
 
- [ ] Initialiser le projet **React** (frontend) avec sa structure de dossiers (`components`, `pages`, `services`, `hooks`, `assets`, etc.)
- [ ] Initialiser le projet **PHP** (backend) avec une structure claire (`api/`, `config/`, `models/`, `controllers/`, `middlewares/`, `utils/`)
- [ ] Configurer un fichier `.env` (ou équivalent) pour les paramètres sensibles (DB, secrets) — **ne pas committer**
- [ ] Configurer la connexion PHP ↔ MySQL en **PDO** avec gestion des erreurs
- [ ] Configurer les en-têtes **CORS** côté PHP pour autoriser le frontend
- [ ] Écrire le `README.md` avec instructions d'installation et de lancement
- [ ] Lister les dépendances (`package.json`, `composer.json` si utilisé)
---
 
## 1. Base de données (MySQL)
 
- [ ] Écrire le **script SQL de création** de la base (`schema.sql`)
- [ ] Tables minimum à prévoir :
  - `utilisateurs` (avec rôle : client, intervenant, admin/superviseur)
  - `services` / `consultations`
  - `intervenants` (lien utilisateur ↔ services proposés)
  - `categories` de services
  - `creneaux` / disponibilités
  - `reservations` / rendez-vous
  - `activites` / programmes
  - `inscriptions_activites` (avec gestion de la capacité)
  - `notifications`
  - `historique_interactions`
  - `panier` / `lignes_panier`
  - `paiements_simules`
- [ ] Définir les **clés primaires, clés étrangères, contraintes UNIQUE et NOT NULL**
- [ ] Ajouter les **index** sur les colonnes fréquemment recherchées (email, date_creneau, etc.)
- [ ] Écrire un script de **jeu de données de test** (`seed.sql`) avec utilisateurs, services, créneaux, activités
- [ ] Utiliser systématiquement des **transactions SQL** pour les opérations critiques (réservation, panier, capacité d'activité)
---
 
## 2. Authentification & gestion des utilisateurs
 
### Backend
- [ ] Endpoint **inscription** (`POST /register`) avec validation des champs
- [ ] Endpoint **connexion** (`POST /login`) avec vérification mot de passe
- [ ] Endpoint **déconnexion** (`POST /logout`) qui détruit la session
- [ ] Endpoint **profil utilisateur** (`GET /me`)
- [ ] Endpoint **modification du profil** (`PUT /me`)
- [ ] **Hachage des mots de passe** avec `password_hash()` (bcrypt) et vérification avec `password_verify()`
- [ ] **Gestion des sessions PHP** (cookies `HttpOnly`, `Secure`, `SameSite`) ou alternative type token
- [ ] **Middleware d'authentification** vérifiant la session sur les routes protégées
- [ ] **Middleware d'autorisation** vérifiant le rôle (client / intervenant / admin)
### Frontend
- [ ] Page **inscription** avec formulaire validé
- [ ] Page **connexion**
- [ ] Composant gérant l'**état d'authentification global** (Context React, ou équivalent)
- [ ] Bouton **déconnexion**
- [ ] Page **mon profil** (consultation + édition)
- [ ] **Routes protégées** côté React (redirection si non connecté)
- [ ] **Affichage conditionnel** des composants selon le rôle de l'utilisateur
---
 
## 3. Navigation et structure générale (frontend)
 
- [ ] Configurer le **routeur** (React Router)
- [ ] Composant **Header** / barre de navigation (avec recherche, notifications, accès profil)
- [ ] Composant **Sidebar** (menu latéral selon rôle)
- [ ] Composant **Footer**
- [ ] Composant **Layout** principal englobant les pages
- [ ] Page **Accueil** (présentation de la plateforme + accès rapide)
- [ ] Page **404 / Not Found**
- [ ] Page **erreur 403** (accès refusé)
- [ ] Rendre l'interface **responsive** (desktop, tablette, mobile) avec CSS
- [ ] **Feedbacks UI** : états de chargement (loaders), messages d'erreur, messages de succès, toasts
---
 
## 4. Catalogue des services
 
### Backend
- [ ] `GET /services` — liste paginée des services
- [ ] `GET /services/{id}` — détail d'un service
- [ ] `GET /services?categorie=…&prix_min=…&prix_max=…&duree=…&intervenant=…` — filtres
- [ ] `GET /services?search=…` — recherche textuelle (nom, description, intervenant)
- [ ] `GET /services?sort=…` — tri (popularité, prix, note)
- [ ] `GET /categories` — liste des catégories
- [ ] `POST /services` — création (réservé intervenant/admin)
- [ ] `PUT /services/{id}` — modification
- [ ] `DELETE /services/{id}` — suppression
- [ ] Endpoint **recommandations** simples (`GET /services/recommandations`)
### Frontend
- [ ] Page **catalogue** avec grille de services
- [ ] **Barre de recherche** fonctionnelle (avec debounce)
- [ ] Panneau de **filtres** (catégorie, prix, durée, lieu, disponibilité)
- [ ] **Tri** des résultats
- [ ] **Pagination** ou scroll infini
- [ ] **Carte de service** (vignette, titre, intervenant, durée, prix, note)
- [ ] Page **détail service** (description complète, intervenant, avis, bouton réserver)
- [ ] Section **recommandé pour vous**
- [ ] Système de **favoris** (ajout / retrait / page favoris)
- [ ] Formulaire de **création/édition** de service (côté intervenant/admin)
---
 
## 5. Réservations et planification
 
### Backend
- [ ] `GET /services/{id}/creneaux?date=…` — créneaux disponibles pour une date donnée
- [ ] `POST /reservations` — créer une réservation
- [ ] `GET /reservations` — mes réservations (passées et à venir)
- [ ] `GET /reservations/{id}` — détail
- [ ] `PUT /reservations/{id}/annuler` — annulation
- [ ] `PUT /reservations/{id}/confirmer` — confirmation (côté intervenant)
- [ ] **Verrouillage / transaction SQL** pour éviter les réservations simultanées sur le même créneau
- [ ] **Vérification stricte côté serveur** que le créneau est libre avant validation
- [ ] **Règles métier à coder** : délai minimum avant rendez-vous, délai d'annulation gratuite, etc. (à définir par l'équipe puis implémenter)
### Frontend
- [ ] **Composant calendrier** (sélection d'une date)
- [ ] Affichage des **créneaux disponibles** pour la date choisie
- [ ] Indication visuelle : disponible / peu de places / complet / indisponible
- [ ] **Wizard de réservation multi-étapes** (choix service → date/heure → infos → confirmation)
- [ ] **Barre de progression** entre les étapes
- [ ] **Récapitulatif** de réservation
- [ ] Page **mes réservations** (filtres : à venir / passées / annulées)
- [ ] Bouton **annuler une réservation** avec confirmation
- [ ] Affichage des **informations importantes** (politique d'annulation, etc.)
---
 
## 6. Activités et programmes de bien-être
 
### Backend
- [ ] `GET /activites` — liste des activités
- [ ] `GET /activites/{id}` — détail
- [ ] `GET /activites?categorie=…&date=…` — filtres
- [ ] `POST /activites` — création (intervenant/admin)
- [ ] `PUT /activites/{id}` — modification
- [ ] `DELETE /activites/{id}` — annulation
- [ ] `POST /activites/{id}/inscription` — s'inscrire
- [ ] `DELETE /activites/{id}/inscription` — se désinscrire
- [ ] `GET /mes-inscriptions` — mes activités
- [ ] **Contrôle de la capacité maximale** côté serveur (avec transaction)
- [ ] **Contrôle des règles temporelles** (date limite d'inscription, date limite d'annulation)
- [ ] Empêcher les **doubles inscriptions** à une même activité
### Frontend
- [ ] Page **activités & programmes** avec filtres (nutrition, relaxation, sport, prévention…)
- [ ] **Carte d'activité** (image, titre, date, heure, lieu, places restantes, tarif)
- [ ] Page **détail activité** (description, intervenant, règles, calendrier)
- [ ] Bouton **s'inscrire** (désactivé si complet ou délai dépassé)
- [ ] Bouton **se désinscrire**
- [ ] Affichage des **règles et conditions** (annulation, places limitées…)
- [ ] Page **mes inscriptions**
- [ ] Section **programmes en cours** avec barre de progression
---
 
## 7. Suivi des consultations et historique
 
### Backend
- [ ] `GET /historique` — historique complet (rendez-vous + activités + interactions)
- [ ] `GET /historique?periode=…&type=…` — filtré
- [ ] `GET /historique/export` — export PDF (optionnel mais demandé dans la figure)
- [ ] **Conservation cohérente** des données même après annulation (statut, pas suppression)
- [ ] **Contrôle de visibilité** : un utilisateur ne voit que son propre historique
### Frontend
- [ ] Page **suivi & historique** avec onglets (vue d'ensemble, rendez-vous, activités, interactions, documents)
- [ ] **Filtres** par période et par statut (à venir / passé / annulé)
- [ ] Tableau / liste des **rendez-vous prochains**
- [ ] Tableau / liste des **activités récentes**
- [ ] **Historique des interactions** (messages, modifications)
- [ ] Résumé statistique (nombre de rendez-vous, d'activités, etc.)
- [ ] Bouton **télécharger le rapport** (PDF)
---
 
## 8. Notifications
 
### Backend
- [ ] `GET /notifications` — liste des notifications utilisateur
- [ ] `GET /notifications?lu=false` — uniquement non lues
- [ ] `PUT /notifications/{id}/lue` — marquer comme lue
- [ ] `PUT /notifications/lues` — marquer toutes comme lues
- [ ] `DELETE /notifications/{id}` — supprimer
- [ ] **Génération automatique** de notifications sur événements :
  - Confirmation de rendez-vous
  - Rappel de rendez-vous
  - Nouvelle disponibilité
  - Inscription confirmée
  - Modification d'activité
  - Message d'un intervenant
  - Annulation
- [ ] Catégorisation des notifications (réservation / activité / système / message)
### Frontend
- [ ] **Icône cloche** dans le header avec **badge du nombre de non lues**
- [ ] **Dropdown** d'aperçu rapide
- [ ] Page **notifications** complète avec onglets (Toutes / Non lues / par catégorie)
- [ ] **Carte de notification** (icône, titre, contenu, date relative type "il y a 10 min")
- [ ] Bouton **marquer comme lue / supprimer**
- [ ] **Panneau de détail** d'une notification
- [ ] **Rafraîchissement** régulier (polling) ou rechargement à l'ouverture
---
 
## 9. Tableau de bord et supervision
 
### Backend
- [ ] `GET /dashboard/stats` — indicateurs clés (réservations totales, utilisateurs actifs, activités réalisées, demandes en attente, satisfaction)
- [ ] `GET /dashboard/reservations-par-statut` — agrégat
- [ ] `GET /dashboard/activites-a-venir`
- [ ] `GET /dashboard/demandes-en-attente`
- [ ] **Restriction d'accès** au tableau de bord selon le rôle (admin / intervenant)
- [ ] Filtrage par **période** (mois courant, période sélectionnée)
### Frontend
- [ ] Page **tableau de bord** réservée aux rôles superviseurs
- [ ] **Cartes d'indicateurs** (total, évolution par rapport à la période précédente)
- [ ] **Graphique** (camembert / barres) pour les réservations par statut
- [ ] **Liste des activités à venir**
- [ ] **Liste des demandes en attente** avec actions rapides
- [ ] **Sélecteur de période**
- [ ] Bouton **exporter le rapport**
- [ ] Vue spécifique pour l'**intervenant** (ses propres réservations / activités)
---
 
## 10. Panier de réservations et validation
 
### Backend
- [ ] `GET /panier` — contenu du panier
- [ ] `POST /panier` — ajouter un élément (service ou activité)
- [ ] `DELETE /panier/{id}` — retirer
- [ ] `DELETE /panier` — vider
- [ ] `POST /panier/valider` — valider et créer toutes les réservations/inscriptions
- [ ] **Vérifications avant validation** :
  - Disponibilité encore valide pour chaque élément
  - Conditions respectées (capacité, délai)
  - Aucune limite dépassée
  - Cohérence des dates
- [ ] **Transaction SQL globale** pour valider tout ou rien
- [ ] **Simulation de paiement** : enregistrer un statut "payé (simulé)" avec un identifiant fictif
- [ ] Génération automatique des **notifications** liées
### Frontend
- [ ] Bouton **ajouter au panier** sur services et activités
- [ ] Icône **panier** dans le header avec compteur
- [ ] Page **panier** : liste des éléments avec image, titre, date, prix, bouton suppression
- [ ] **Récapitulatif de commande** (total, nombre d'éléments)
- [ ] **Formulaire de paiement simulé** (carte fictive — clairement indiqué comme simulation)
- [ ] Bouton **valider et payer (simulation)**
- [ ] Affichage des **vérifications effectuées** (disponibilités confirmées, conditions respectées…)
- [ ] **Message clair** indiquant que le paiement est simulé
- [ ] Page de **confirmation** après validation
- [ ] **Gestion des erreurs** (créneau pris entre temps, capacité dépassée, etc.)
---
 
## 11. Sécurité (transversal, à appliquer partout)
 
- [ ] **Requêtes préparées PDO** systématiquement (anti **injection SQL**)
- [ ] **Échappement** des sorties HTML côté React (par défaut) et `htmlspecialchars()` côté PHP si du HTML est renvoyé (anti **XSS**)
- [ ] **Validation côté client** (formulaires React) pour le confort utilisateur
- [ ] **Validation côté serveur** (PHP) systématique — ne jamais faire confiance au client
- [ ] **Hachage des mots de passe** avec `password_hash()` — jamais en clair
- [ ] **Tokens CSRF** sur les actions sensibles (ou en-tête custom si API)
- [ ] **Cookies de session** sécurisés (`HttpOnly`, `Secure`, `SameSite=Lax` ou `Strict`)
- [ ] **Régénération de l'ID de session** après connexion
- [ ] **Contrôle d'autorisation** sur **chaque** endpoint protégé (pas seulement authentification)
- [ ] **Vérification de propriété** : un user ne peut modifier/voir que ses propres données
- [ ] **Limitation des informations** renvoyées (ne jamais renvoyer le hash du mot de passe, etc.)
- [ ] **Messages d'erreur génériques** côté front (pas de fuite d'info type "email inconnu")
- [ ] **Gestion centralisée des erreurs** côté backend (codes HTTP appropriés : 400, 401, 403, 404, 409, 500)
---
 
## 12. Validations spécifiques à coder
 
- [ ] **Email** : format valide + unicité en base
- [ ] **Mot de passe** : longueur minimum, complexité (à définir)
- [ ] **Dates** : pas dans le passé pour une réservation
- [ ] **Créneaux** : appartiennent bien aux disponibilités du service
- [ ] **Capacité d'activité** : ne pas dépasser la limite
- [ ] **Double réservation** : un user ne peut pas réserver deux créneaux qui se chevauchent
- [ ] **Champs obligatoires** sur tous les formulaires
- [ ] **Longueurs maximales** des champs textes (cohérence avec la BDD)
- [ ] **Types** des données (entier, date, énumération…)
---
 
## 13. Qualité de code
 
- [ ] **Code structuré** en composants/fonctions réutilisables
- [ ] **Nommage cohérent** (français ou anglais — choisir et s'y tenir)
- [ ] **Commentaires** sur les parties complexes (règles métier notamment)
- [ ] **Pas de code mort** ni de `console.log` / `var_dump` oubliés
- [ ] **Gestion des erreurs** (try/catch) côté backend comme frontend
- [ ] Fichier **`.gitignore`** correct (`node_modules`, `.env`, fichiers IDE, vendor…)
- [ ] **Commits réguliers et significatifs** sur GitHub (pas de gros commits monolithiques en fin de projet)
---
 
## Rappel des deadlines (lié au code)
 
- **31 mai 2026 à 23h55** — Projet final : code source complet + scripts SQL + ressources + fichiers de config + dépendances + instructions d'installation, le tout exécutable facilement.
- Le **dépôt GitHub** doit refléter une progression réelle et la participation de tous les membres.
