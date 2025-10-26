# UC02: Simplifier l'expérience utilisateur

## Informations générales
- **ID**: UC02
- **Nom**: Simplifier l'expérience utilisateur
- **Besoin client associé**: B02
- **Caractéristiques**: CAR04, CAR05, CAR06
- **Acteur principal**: Citoyen
- **Acteurs secondaires**: Service d'authentification gouvernementale

## Description
Le citoyen bénéficie d'une expérience utilisateur simplifiée grâce à une authentification sécurisée, l'autocomplétion des formulaires et la sauvegarde de ses préférences personnelles.

## Prérequis
- Le service d'authentification gouvernementale est opérationnel
- Le citoyen possède un compte gouvernemental valide

## Postconditions
- Le citoyen est authentifié de manière sécurisée
- Les formulaires sont pré-remplis automatiquement
- Les préférences du citoyen sont sauvegardées
- L'expérience utilisateur est personnalisée

## Scénario nominal

### UC02.1: S'authentifier de manière sécurisée
1. Le citoyen accède à la plateforme RVSQ
2. Le système redirige vers le service d'authentification gouvernementale (CAR04)
3. Le citoyen entre ses identifiants gouvernementaux
4. Le service d'authentification valide les identifiants
5. Le système établit une session sécurisée
6. Le système récupère le profil du citoyen
7. Le système affiche la page d'accueil personnalisée

### UC02.2: Utiliser l'autocomplétion des formulaires
1. Le citoyen accède à la page de profil et sélectionne (Mes réservations)
2. Le système récupère les données personnelles sauvegardées
3. Le système préremplis automatiquement les champs (CAR05):
   - Code Postal
   - Adresse
   - Périmètre de recherche
4. Le citoyen vérifie les informations préremplies
5. Le citoyen modifie si nécessaire les informations
6. Le système valide les données du formulaire

### UC02.3: Gérer les préférences personnelles
1. Le citoyen accède à la section "Mes préférences"
2. Le système affiche les préférences actuelles
3. Le citoyen configure ses préférences (CAR06):
   - Médecin(s) de famille préféré(s)
   - Clinique(s) préférée(s)
   - Langue de communication (français, anglais)
   - Type de notifications (courriel, SMS, application)
   - Fréquence des rappels
   - Créneaux horaires préférés
4. Le citoyen sauvegarde ses préférences
5. Le système valide et enregistre les préférences de manière sécurisée
6. Le système confirme la sauvegarde
7. Le système applique les préférences aux futures interactions

### UC02.4: Consulter l'historique
1. Le citoyen accède à "Mon historique"
2. Le système affiche l'historique des rendez-vous passés
3. Le système affiche les rendez-vous à venir
4. Le citoyen peut consulter les détails de chaque rendez-vous

## Scénarios alternatifs

### A1: Première connexion du citoyen
**Point de divergence**: Étape UC02.1
1. Le citoyen se connecte pour la première fois
2. Le système détecte l'absence de profil
3. Le système lance un assistant de configuration initiale
4. Le système demande au citoyen de configurer ses préférences de base
5. Le système crée le profil du citoyen
6. Retour à UC02.3

### A2: Modification des données pré-remplies
**Point de divergence**: Étape UC02.2
1. Le citoyen modifie une ou plusieurs données pré-remplies
2. Le système demande confirmation pour mettre à jour le profil
3. Si accepté: le système met à jour les données pour futures utilisations
4. Si refusé: le système utilise les nouvelles données uniquement pour ce formulaire
5. Retour à UC02.2 étape 6

### A3: Préférences non définies
**Point de divergence**: Étape UC02.3
1. Le citoyen n'a pas encore défini de préférences
2. Le système affiche les valeurs par défaut
3. Le système suggère de configurer les préférences
4. Retour à UC02.3 étape 3

## Scénarios d'exception

### E1: Échec de l'authentification gouvernementale
**Point de divergence**: Étape UC02.1
1. Le service d'authentification gouvernementale est indisponible
2. Le système affiche un message d'erreur explicatif
3. Le système propose de réessayer plus tard
4. Le système envoie une notification aux administrateurs
5. Le cas d'utilisation est interrompu

### E2: Erreur de sauvegarde des préférences
**Point de divergence**: Étape UC02.3
1. Le système ne parvient pas à sauvegarder les préférences
2. Le système affiche un message d'erreur
3. Le système conserve les anciennes préférences
4. Le système propose de réessayer
5. Si échec persistant: le système enregistre l'incident pour investigation

### E3: Données personnelles corrompues
**Point de divergence**: Étape UC02.2
1. Les données stockées sont corrompues ou invalides
2. Le système détecte l'anomalie
3. Le système affiche les champs vides
4. Le système journalise l'incident
5. Le citoyen remplit manuellement le formulaire
6. Le système propose de mettre à jour le profil avec les nouvelles données

## Exigences non fonctionnelles
- **Sécurité**: 
  - Chiffrement des données personnelles au repos et en transit
  - Conformité avec les normes gouvernementales de sécurité
  - Session expirée après 15 minutes d'inactivité
- **Performance**: 
  - Authentification en moins de 5 secondes
  - Autocomplétion instantanée (< 500ms)
- **Utilisabilité**: 
  - Interface intuitive et accessible (WCAG 2.1 niveau AA)
  - Support multi-langues (français, anglais minimum)
- **Confidentialité**: 
  - Respect de la loi sur la protection des renseignements personnels
  - Consentement explicite pour la sauvegarde des données

## Points de traçabilité
- **Besoins**: B02
- **Caractéristiques**: CAR04, CAR05, CAR06
- **Systèmes**: Service d'authentification gouvernementale
