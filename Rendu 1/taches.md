# Rendu 1 - Conception et justification technique

**Deadline : jeudi 28 mai 2026 à 23h55**  
**Format attendu : archive ZIP de 100 Mo maximum**

Ce rendu doit montrer que l'équipe a défini une vision cohérente de VitaCare avant le développement. La stack déjà annoncée dans le dépôt est `React` pour le frontend, `PHP` pour le backend et `MySQL` pour la base de données.

## 1. Cadrage du projet

- [ ] [FARES] Définir le positionnement précis de VitaCare : contexte de santé ou bien-être, public cible et besoin principal.
- [ ] [FARES] Choisir les rôles utilisateurs et leurs droits : utilisateur/client, intervenant/professionnel et administrateur/superviseur, à adapter si nécessaire.
- [ ] [FARES] Lister les parcours prioritaires à livrer : consulter un service, réserver un créneau, s'inscrire à une activité, suivre ses réservations et recevoir des notifications.
- [ ] [FARES] Définir les règles métier importantes : disponibilités, annulation, capacité d'une activité, validation d'une réservation et paiement simulé.
- [ ] [FARES] Identifier un périmètre réaliste pour la deadline du projet final et indiquer les fonctionnalités secondaires facultatives.

## 2. Wireframes des interfaces principales

- [ ] [JOSHUA] Réaliser le wireframe de la page d'accueil et de la navigation générale.
- [ ] [JOSHUA] Réaliser les écrans d'inscription, connexion et profil selon les rôles.
- [ ] [JOSHUA] Réaliser le catalogue des services/activités avec recherche, filtre ou tri.
- [ ] [JOSHUA] Réaliser une fiche service/intervenant avec disponibilités.
- [ ] [JOSHUA] Réaliser le parcours de réservation : choix du créneau, panier/récapitulatif et confirmation.
- [ ] [JOSHUA] Réaliser l'espace utilisateur : rendez-vous passés/à venir, activités et notifications.
- [ ] [JOSHUA] Réaliser un espace intervenant ou administration : gestion des services, créneaux, inscriptions et tableau de bord.
- [ ] [JOSHUA] Vérifier que les wireframes indiquent les actions, navigations et adaptations essentielles aux écrans mobiles.

## 3. Storyboard des parcours utilisateurs

- [ ] [THOMAS] Illustrer le parcours d'un utilisateur qui recherche puis réserve un service.
- [ ] [THOMAS] Illustrer le parcours d'inscription à une activité de bien-être avec gestion de la capacité.
- [ ] [THOMAS] Illustrer le parcours d'un intervenant qui crée ou gère ses disponibilités.
- [ ] [THOMAS] Illustrer le parcours de supervision/administration retenu par l'équipe.
- [ ] [THOMAS] Faire apparaître les états importants : connexion requise, réservation confirmée/refusée, annulation et notification.

## 4. Modèle de données

- [ ] [ZAKI] Produire le modèle entité-association (MCD/MEA) avec entités, attributs principaux, clés primaires, associations et cardinalités.
- [ ] [ZAKI] Modéliser au minimum les notions retenues parmi : utilisateurs, rôles, intervenants, services, activités, disponibilités, réservations, inscriptions, notifications et panier/validation.
- [ ] [ZAKI] Prévoir les statuts nécessaires : réservation, activité, notification et validation/paiement simulé.
- [ ] [ZAKI] Expliquer comment le modèle évite les incohérences importantes, par exemple la double réservation ou le dépassement de capacité.

## 5. Architecture et choix techniques

- [ ] [THOMAS] Dessiner un schéma simple des échanges entre frontend `React`, API/backend `PHP` et base `MySQL`.
- [ ] [THOMAS] Définir l'arborescence cible du dépôt : `frontend/`, `backend/`, `database/` et `docs/`.
- [ ] [THOMAS] Préciser les mécanismes envisagés pour l'authentification, les sessions, les autorisations selon le rôle et les validations client/serveur.
- [ ] [ZAKI] Décrire les mesures minimales de sécurité : mots de passe hashés, requêtes préparées, contrôle des entrées, protection des routes et gestion des erreurs.
- [ ] [THOMAS] Justifier les principaux compromis techniques et fonctionnels retenus.

## 6. Spécifications fonctionnelles

- [ ] [FARES] Rédiger le document de spécifications fonctionnelles.
- [ ] [FARES] Présenter le contexte, le public cible, les rôles et permissions.
- [ ] [FARES] Décrire les fonctionnalités retenues : navigation, comptes, catalogue, réservations, activités, historique, notifications, tableau de bord et panier/validation si inclus.
- [ ] [FARES] Indiquer les contraintes techniques, la stack et les choix d'architecture.
- [ ] [FARES] Définir les critères d'acceptation des parcours prioritaires.
- [ ] [FARES] Ajouter les références utilisées et déclarer l'utilisation d'outils d'intelligence artificielle.

## 7. Organisation de l'équipe et dépôt GitHub

- [ ] [FARES] Confirmer ou ajuster la répartition prévisionnelle indiquée dans le README : Zaki (BDD/backend), Joshua (frontend/wireframes), Thomas (architecture/storyboard), Fares (spécifications/coordination).
- [ ] [FARES] Découper le travail en tâches attribuées et dater les prochains points d'avancement.
- [ ] [TOUS] Utiliser des branches ou commits lisibles et publier plusieurs commits significatifs par membre.
- [ ] [THOMAS] Ajouter les documents de conception dans le dépôt afin de rendre la progression visible.

## 8. Contrôle avant remise

- [ ] [FARES] Vérifier que l'archive contient les wireframes, le storyboard, le modèle entité-association, le schéma d'architecture, les spécifications et la répartition du travail.
- [ ] [FARES] Vérifier la cohérence entre interfaces, parcours, modèle de données et architecture.
- [ ] [FARES] Vérifier que les sources et l'utilisation de l'IA sont citées.
- [ ] [FARES] Nommer l'archive au format `PJ_WEB_2026_Nom1_Nom2_Nom3_Nom4.zip`.
- [ ] [FARES] Confirmer que l'archive fait moins de 100 Mo et qu'elle est déposée avant `23h55`.
