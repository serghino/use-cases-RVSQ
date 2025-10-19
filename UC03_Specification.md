# UC03: Réduire la surcharge des secrétariats

## Informations générales
- **ID**: UC03
- **Nom**: Réduire la surcharge des secrétariats
- **Besoin client associé**: B03
- **Caractéristiques**: CAR07, CAR08
- **Acteur principal**: Adjoint administratif
- **Acteurs secondaires**: Médecin, Infirmière, DME (Dossier Médical Électronique), Services de messagerie

## Description
Les adjoints administratifs, médecins et infirmières bénéficient d'une automatisation de la gestion des disponibilités et des annulations, réduisant ainsi la charge de travail administrative des secrétariats.

## Prérequis
- Les cliniques/hôpitaux ont un système DME opérationnel
- L'intégration entre le DME et la plateforme RVSQ est configurée
- Les services de messagerie sont opérationnels
- Les professionnels de santé sont authentifiés

## Postconditions
- Les disponibilités sont publiées automatiquement dans la plateforme
- Les annulations sont synchronisées avec le DME
- Les citoyens et professionnels sont notifiés automatiquement
- La charge administrative des adjoints administratifs est réduite

## Scénario nominal

### UC03.1: Publier automatiquement les disponibilités
1. Le médecin/infirmière configure ses plages horaires dans le DME
2. Le DME détecte les nouvelles disponibilités
3. Le système RVSQ récupère automatiquement les disponibilités via l'intégration DME (CAR07)
4. Le système valide et formate les données reçues
5. Le système publie les créneaux disponibles sur la plateforme
6. Le système confirme la publication au professionnel
7. Les créneaux deviennent visibles pour les citoyens

### UC03.2: Gérer les annulations
1. L'adjoint administratif accède à la section "Gestion des rendez-vous"
2. Le système affiche la liste des rendez-vous planifiés
3. L'adjoint sélectionne un rendez-vous à annuler
4. Le système demande la raison de l'annulation
5. L'adjoint confirme l'annulation
6. Le système centralise l'annulation dans la plateforme (CAR08)
7. Le système synchronise l'annulation avec le DME
8. Le système envoie une notification au citoyen concerné
9. Le système libère le créneau horaire
10. Le créneau redevient disponible pour d'autres citoyens

### UC03.3: Consulter les réservations
1. L'adjoint administratif accède au tableau de bord
2. Le système affiche la liste des réservations du jour/semaine
3. L'adjoint peut filtrer par professionnel, date, ou statut
4. Le système affiche les détails des réservations sélectionnées
5. L'adjoint peut exporter la liste si nécessaire

### UC03.4: Modifier les plages horaires
1. Le médecin/infirmière accède à "Mes disponibilités"
2. Le système affiche les plages horaires actuelles
3. Le professionnel modifie manuellement une plage horaire
4. Le système vérifie qu'aucun rendez-vous n'est planifié sur cette plage
5. Le système met à jour les disponibilités
6. Le système synchronise avec le DME
7. Le système confirme la modification

## Scénarios alternatifs

### A1: Annulation par le citoyen
**Point de divergence**: Étape UC03.2
1. Le citoyen annule son rendez-vous via la plateforme
2. Le système enregistre l'annulation automatiquement
3. Le système synchronise avec le DME
4. Le système notifie l'adjoint administratif et le professionnel
5. Le créneau est automatiquement libéré
6. Fin du cas d'utilisation

### A2: Annulation d'urgence
**Point de divergence**: Étape UC03.2
1. L'adjoint indique qu'il s'agit d'une annulation d'urgence
2. Le système traite l'annulation en priorité
3. Le système envoie une notification immédiate au citoyen
4. Le système propose des créneaux alternatifs au citoyen
5. Retour à UC03.2 étape 9

### A3: Publication partielle des disponibilités
**Point de divergence**: Étape UC03.1
1. Le professionnel souhaite ne publier qu'une partie de ses disponibilités
2. Le professionnel sélectionne les créneaux spécifiques à publier
3. Le système publie uniquement les créneaux sélectionnés
4. Retour à UC03.1 étape 6

### A4: Modification avec rendez-vous existants
**Point de divergence**: Étape UC03.4
1. Le système détecte des rendez-vous sur la plage à modifier
2. Le système affiche un avertissement au professionnel
3. Le système propose de déplacer ou annuler les rendez-vous existants
4. Le professionnel choisit l'action à effectuer
5. Le système traite les rendez-vous affectés
6. Retour à UC03.4 étape 5

## Scénarios d'exception

### E1: Échec de synchronisation avec le DME
**Point de divergence**: Étape UC03.1 ou UC03.2
1. L'intégration avec le DME échoue
2. Le système affiche un message d'erreur
3. Le système enregistre l'opération en attente
4. Le système notifie l'administrateur système
5. Le système tente une nouvelle synchronisation automatiquement
6. Si échec persistant: mode manuel activé

### E2: Conflit de disponibilité
**Point de divergence**: Étape UC03.1
1. Le système détecte un conflit entre les données du DME et la plateforme
2. Le système journalise le conflit
3. Le système affiche une alerte à l'adjoint administratif
4. L'adjoint résout manuellement le conflit
5. Le système synchronise les données corrigées

### E3: Échec d'envoi de notification
**Point de divergence**: Étape UC03.2
1. L'envoi de la notification d'annulation échoue
2. Le système enregistre l'échec
3. Le système tente de renvoyer la notification (3 tentatives)
4. Si échec persistant: l'adjoint est notifié pour contact manuel (envoi d'email/SMS)
5. L'annulation reste effective dans le système

## Exigences non fonctionnelles
- **Performance**: 
  - Synchronisation DME en temps réel (< 30 secondes)
  - Publication des disponibilités en moins de 1 minute
- **Disponibilité**: 
  - Service de synchronisation disponible 24h/24
  - Mécanisme de file d'attente en cas d'indisponibilité temporaire
- **Fiabilité**: 
  - Système de retry automatique en cas d'échec
  - Journalisation complète de toutes les opérations
- **Sécurité**: 
  - Communication sécurisée avec les DME (HTTPS, API authentifiée)
  - Contrôle d'accès basé sur les rôles
- **Intégration**: 
  - Support de multiples formats DME standards (HL7, FHIR)
  - API RESTful pour l'intégration

## Points de traçabilité
- **Besoins**: B03
- **Caractéristiques**: CAR07, CAR08
- **Systèmes**: DME (Cliniques/Hôpitaux), Services de messagerie
