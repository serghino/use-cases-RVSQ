# UC01: Réserver rapidement et efficacement un rendez-vous

## Informations générales
- **ID**: UC01
- **Nom**: Réserver rapidement et efficacement un rendez-vous
- **Besoin client associé**: B01
- **Caractéristiques**: CAR01, CAR02, CAR03
- **Acteur principal**: Citoyen
- **Acteurs secondaires**: Invité, Service d'authentification, DME, Services de messagerie

## Description
Le citoyen souhaite prendre un rendez-vous médical de manière rapide et efficace via la plateforme RVSQ.

## Prérequis
- Les cliniques ont publié leurs disponibilités dans le système
- Le service d'authentification gouvernementale est opérationnel
- Les services de messagerie sont configurés

## Postconditions
- Le rendez-vous est confirmé et enregistré
- Le citoyen reçoit une confirmation
- La clinique est notifiée de la réservation
- Des rappels automatiques sont programmés

## Scénario nominal

### UC01.1: Rechercher un professionnel
1. Le citoyen accède à la plateforme RVSQ
2. Le système demande l'authentification du citoyen
3. Le citoyen s'authentifie via le service d'authentification gouvernementale
4. Le système affiche le moteur de recherche centralisé (CAR01)
5. Le citoyen saisit ses critères de recherche (spécialité, localisation)
6. Le système consulte les disponibilités des DME
7. Le système affiche la liste des professionnels disponibles

### UC01.2: Filtrer les résultats
1. Le citoyen applique des filtres avancés (CAR02):
   - Spécialité médicale
   - Langue de consultation
   - Localisation géographique
   - Créneaux horaires préférés
2. Le système met à jour la liste des résultats
3. Le système trie les résultats par pertinence

### UC01.3: Sélectionner un créneau
1. Le citoyen sélectionne un professionnel
2. Le système affiche les créneaux disponibles en temps réel
3. Le citoyen choisit un créneau horaire
4. Le système réserve temporairement le créneau (5 minutes)

### UC01.4: Confirmer la réservation
1. Le citoyen confirme les détails du rendez-vous
2. Le système valide et enregistre la réservation
3. Le système libère les autres créneaux temporaires

### UC01.5: Recevoir confirmation
1. Le système génère une confirmation de rendez-vous (CAR03)
2. Le système envoie la confirmation par courriel/SMS
3. Le système programme des rappels automatiques
4. Le système met à jour les disponibilités dans les DME

## Scénarios d'exception

### E1: Échec d'authentification
**Point de divergence**: Étape UC01.1
1. L'authentification gouvernementale échoue
2. Le système affiche un message d'erreur
3. Le système propose de réessayer ou de contacter le support
4. Le citoyen ne peut pas accéder aux fonctionnalités de réservation

### E2: Système DME indisponible
**Point de divergence**: Étape UC01.1
1. Les DME ne répondent pas
2. Le système affiche un message d'indisponibilité temporaire
3. Le système propose d'être notifié quand le service sera rétabli
4. Le cas d'utilisation est interrompu

## Exigences non fonctionnelles
- **Performance**: Recherche en moins de 3 secondes
- **Disponibilité**: Service disponible 24h/24, 7j/7
- **Sécurité**: Authentification multifacteur obligatoire pour la confirmation
- **Utilisabilité**: Interface intuitive accessible sur mobile et ordinateur

## Points de traçabilité
- **Besoins**: B01
- **Caractéristiques**: CAR01, CAR02, CAR03
- **Systèmes**: Service d'authentification, DME, Services de messagerie