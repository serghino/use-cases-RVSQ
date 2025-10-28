# RVSQ-UC-09.2 – Notifier les cliniques

## 1. BRÈVE DESCRIPTION
La **Plateforme RVSQ** informe automatiquement les cliniques/DME des nouvelles réservations, modifications ou annulations de rendez-vous.

## 2. ACTEURS IMPLIQUÉS
- **Acteur principal :** Plateforme RVSQ
- **Acteurs secondaires :** Cliniques / Hôpitaux (DME), Service de messagerie

## 3. FLUX D'ÉVÉNEMENTS
### 3.1 Flux nominal
1. Détecter la création/modification/annulation d'un rendez-vous.
2. Identifier la clinique/DME destinataire.
3. Construire le message (payload API + résumé lisible).
4. Transmettre au DME (API REST sécurisée) et, au besoin, via service de messagerie.
5. Recevoir l'accusé de réception et journaliser.

### 3.2 Flux alternatifs
- **A1 — DME non joignable :** relances avec backoff ; si échec, journalisation et alerte.
- **A2 — Données incohérentes :** rejet et notification à l'administrateur.

## 4. EXIGENCES SPÉCIALES
- **Sécurité :** TLS 1.3 (mutuel) + certificats X.509 (CAR13).
- **Traçabilité :** logs complets (CAR14).

## 5. PRÉ/POSTCONDITIONS
- **Pré :** DME intégré et canal configuré.
- **Post :** notification confirmée ou échec consigné.

## 6. CARACTÉRISTIQUES CORRESPONDANTES
CAR09, CAR13, CAR14

## 7. TRAÇABILITÉ
- CAR09 → UC09.2
