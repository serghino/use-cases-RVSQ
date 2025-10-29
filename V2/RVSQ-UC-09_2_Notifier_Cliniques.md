# RVSQ-UC-09.2 – Notifier les cliniques

## 1. BRÈVE DESCRIPTION
La **Plateforme RVSQ** informe automatiquement les cliniques et leurs DME des nouvelles réservations, modifications ou annulations de rendez-vous.  
Cette notification s'effectue via des canaux sécurisés (API REST ou service de messagerie), garantissant la synchronisation en temps réel entre les systèmes.

## 2. ACTEURS IMPLIQUÉS
- **Acteur principal :** Plateforme RVSQ
- **Acteurs secondaires :** Cliniques / Hôpitaux (DME), Service de messagerie

## 3. FLUX D'ÉVÉNEMENTS
### 3.1 Flux nominal
1. Détecter la création, la modification ou l'annulation d'un rendez-vous.
2. Identifier la clinique ou le DME destinataire.
3. Construire le message de notification (payload JSON + résumé lisible).
4. Transmettre la notification au DME via API REST sécurisée.
5. Si le DME ne supporte pas l'API, utiliser le **service de messagerie** comme canal secondaire.
6. Recevoir l'accusé de réception et journaliser la transaction.

### 3.2 Flux alternatifs
- **A1 — DME non joignable :** plusieurs tentatives avec **backoff exponentiel** ; si l'échec persiste, journalisation et alerte à l'administrateur.
- **A2 — Données incohérentes :** rejet, journalisation et notification à l'administrateur.
- **A3 — Canal secondaire (messagerie) :** utilisation automatique du service de messagerie lorsque le DME est indisponible.

## 4. EXIGENCES SPÉCIALES
- **Sécurité :** TLS 1.3 mutuel + certificats X.509 (CAR13).
- **Traçabilité :** journalisation complète (CAR14).
- **Disponibilité :** fonctionnement 24/7 avec relance automatique.
- **Conformité :** Loi 25 – Protection des renseignements personnels.

## 5. PRÉCONDITIONS
- Le DME est intégré et accessible.
- Les canaux de communication sont configurés et authentifiés.

## 6. POSTCONDITIONS
- La clinique a reçu la notification ou l'échec est consigné.
- Le journal d'envoi est archivé pour audit.

## 7. POINTS D'EXTENSION
- **UC092.D – Relancer en cas d'échec :** exécuté uniquement lorsqu'une erreur réseau ou un timeout est détecté.
- **UC092.E – Utiliser service de messagerie :** exécuté si l'API DME n'est pas disponible.
- UC10 : Synchronisation des disponibilités en temps réel.
- UC14 : Journalisation et analyse d'anomalies.

## 8. CARACTÉRISTIQUES CORRESPONDANTES
CAR09, CAR13, CAR14

## 9. POINTS DE TRAÇABILITÉ
- CAR09 → UC09.2
- CAR13 → UC09.2
- CAR14 → UC09.2
