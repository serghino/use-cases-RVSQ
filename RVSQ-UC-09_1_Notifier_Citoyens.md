# RVSQ-UC-09.1 – Notifier les citoyens

## 1. BRÈVE DESCRIPTION
La **Plateforme RVSQ** envoie automatiquement des notifications multi-canaux (courriel, SMS, notification mobile) aux citoyens éligibles lorsqu’un événement survient (créneau libéré, confirmation, annulation).

## 2. ACTEURS IMPLIQUÉS
- **Acteur principal :** Plateforme RVSQ
- **Acteurs secondaires :** DME, Service de messagerie, Citoyen

## 3. FLUX D’ÉVÉNEMENTS
### 3.1 Flux nominal
1. Détecter l’événement (créneau libéré).
2. Identifier les citoyens inscrits correspondants.
3. Construire le message (contenu, langue, lien d’action).
4. Sélectionner le canal (courriel, SMS, notification mobile) selon les préférences.
5. Envoyer la notification via le service de messagerie.
6. Recevoir le statut d’envoi et journaliser.

### 3.2 Flux alternatifs
- **A1 — Service de messagerie indisponible :** backoff exponentiel ; si échec, journalisation (CAR14) et alerte.
- **A2 — Aucune préférence :** envoi par défaut par courriel.

## 4. EXIGENCES SPÉCIALES
- **Sécurité :** TLS 1.3 + PFS ; chiffrement du contenu (CAR13).
- **Traçabilité :** journalisation complète (CAR14).
- **Disponibilité :** 24/7.
- **Conformité :** Loi 25 (protection des renseignements personnels).

## 5. PRÉCONDITIONS
- Préférences de notification configurées.
- DME et service de messagerie accessibles.

## 6. POSTCONDITIONS
- Notification transmise/consignée.
- Journal d’envoi archivé.

## 7. POINTS D’EXTENSION
- UC23 : Notifications instantanées.

## 8. CARACTÉRISTIQUES CORRESPONDANTES
CAR09, CAR13, CAR14

## 9. POINTS DE TRAÇABILITÉ
- CAR09 → UC09.1
