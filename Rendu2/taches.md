# Rendu 2 - Projet final VitaCare

**Deadline : dimanche 31 mai 2026 à 23h55**  
**Format attendu : archive ZIP de 100 Mo maximum**

Le projet final doit être une application web dynamique exécutable et compréhensible par les enseignants, avec son code source, ses scripts SQL, ses ressources, sa configuration et ses instructions d'installation.

## 1. Initialisation et architecture du projet

- [ ] Créer l'arborescence annoncée : `frontend/`, `backend/`, `database/` et `docs/`.
- [ ] Initialiser l'application `React` et organiser les pages, composants, services API et styles.
- [ ] Mettre en place le backend `PHP` avec une structure claire pour les routes/API, les contrôles d'accès et la connexion à `MySQL`.
- [ ] Créer les scripts SQL de schéma et un jeu de données de démonstration.
- [ ] Ajouter une configuration documentée sans publier de secrets dans GitHub.

## 2. Authentification, rôles et sécurité

- [ ] Implémenter l'inscription, la connexion, la déconnexion et la gestion de session.
- [ ] Hasher les mots de passe et utiliser des requêtes préparées côté PHP.
- [ ] Implémenter les rôles et autorisations retenus dans le Rendu 1.
- [ ] Valider les données côté client et côté serveur.
- [ ] Protéger les opérations sensibles et tester les accès interdits selon le rôle.

## 3. Catalogue des services et activités

- [ ] Implémenter l'affichage dynamique des services et/ou programmes de bien-être.
- [ ] Implémenter une page détaillée pour consulter une offre et les informations utiles à la réservation.
- [ ] Ajouter les mécanismes retenus de recherche, filtre, tri ou catégorie.
- [ ] Permettre aux intervenants ou administrateurs de gérer les contenus qui leur sont autorisés.

## 4. Réservations et planification

- [ ] Implémenter la création et la consultation des disponibilités/créneaux.
- [ ] Implémenter le parcours de réservation jusqu'à la confirmation.
- [ ] Appliquer les contrôles de disponibilité et empêcher les doubles réservations.
- [ ] Gérer les statuts et les cas prévus : à venir, confirmée, annulée, terminée ou refusée selon votre modèle.
- [ ] Implémenter le panier ou récapitulatif de validation retenu, avec paiement simulé si ce parcours fait partie du périmètre final.

## 5. Activités, historique et notifications

- [ ] Implémenter l'inscription à une activité ou un programme avec contrôle de capacité et de date.
- [ ] Permettre la consultation des rendez-vous et activités passés et à venir.
- [ ] Conserver un historique cohérent des interactions essentielles.
- [ ] Implémenter les notifications choisies : confirmation, annulation, changement ou rappel, selon le périmètre défini.
- [ ] Vérifier la visibilité des historiques et notifications selon le rôle.

## 6. Tableau de bord et expérience utilisateur

- [ ] Implémenter le tableau de bord correspondant aux rôles retenus : réservations, activités, demandes ou indicateurs pertinents.
- [ ] Finaliser la navigation entre les pages principales.
- [ ] Adapter l'interface aux formats d'écran importants.
- [ ] Soigner les états de chargement, erreurs, formulaires vides et confirmations utilisateur.
- [ ] Vérifier que l'implémentation reste cohérente avec les wireframes et documenter les écarts justifiés.

## 7. Tests et qualité technique

- [ ] Tester les parcours principaux de bout en bout avec des comptes de démonstration pour chaque rôle.
- [ ] Tester les erreurs métier : créneau déjà réservé, activité complète, saisie invalide, accès interdit et session absente.
- [ ] Tester l'installation depuis une base de données vide en exécutant les scripts SQL fournis.
- [ ] Vérifier les vulnérabilités classiques abordables dans le cadre du projet : injection SQL, accès non autorisé, affichage de données sensibles et mots de passe.
- [ ] Nettoyer le code, les messages de debug, les fichiers temporaires et les secrets éventuels.

## 8. Documentation et éléments finaux

- [ ] Rédiger les instructions d'installation et d'exécution dans le `README.md` : prérequis, base SQL, configuration, lancement et comptes de démonstration.
- [ ] Fournir le modèle relationnel final et mettre à jour l'architecture finale.
- [ ] Fournir la répartition réelle du travail entre les membres.
- [ ] Rédiger le rapport de compromis techniques : fonctionnalités simplifiées/abandonnées, difficultés, décisions, limites et évolutions depuis la conception.
- [ ] Tenir un journal d'assistance par IA : outils, usages, réponses utiles ou incorrectes, corrections réalisées et limites observées.
- [ ] Rassembler les références et sources utilisées.

## 9. Présentation PowerPoint

- [ ] Préparer une page de garde et un sommaire.
- [ ] Présenter la répartition réelle du travail et le versioning Git.
- [ ] Inclure l'architecture finale, le modèle entité-association et le modèle relationnel final.
- [ ] Inclure les principaux wireframes, le storyboard et les spécifications fonctionnelles.
- [ ] Présenter le journal d'assistance par IA et le rapport de compromis techniques.
- [ ] Ajouter un bilan individuel, un bilan collectif et les références utilisées.

## 10. GitHub et remise finale

- [ ] Publier régulièrement des commits significatifs montrant l'évolution réelle du projet et les contributions de chaque membre.
- [ ] Vérifier que le lien GitHub fonctionne et fournir les accès nécessaires si le dépôt devient privé.
- [ ] Construire l'archive finale avec le code source, les scripts SQL, les ressources frontend, la configuration requise, la documentation et les livrables demandés.
- [ ] Exclure les secrets, fichiers inutiles et dépendances régénérables qui feraient dépasser la limite de taille, sauf si elles sont explicitement nécessaires à l'exécution demandée.
- [ ] Nommer l'archive au format `PJ_WEB_2026_Nom1_Nom2_Nom3_Nom4.zip`.
- [ ] Vérifier que l'archive fait moins de 100 Mo, s'ouvre correctement et permet une installation simple avant le dépôt à `23h55`.
