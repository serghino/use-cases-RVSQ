# RVSQ-UC-10.1 – Réception des événements DME

## 1. BRÈVE DESCRIPTION
La **Plateforme RVSQ** réceptionne, valide et intègre les notifications de disponibilités envoyées par les DME afin d'assurer la synchronisation en temps réel des créneaux médicaux.  
Ce processus garantit que les citoyens voient des disponibilités à jour et que les cliniques disposent d'une vision cohérente du calendrier global.

## 2. ACTEURS IMPLIQUÉS
- **Acteur principal :** Plateforme RVSQ
- **Acteurs secondaires :** DME, Administrateur système

## 3. FLUX D'ÉVÉNEMENTS
### 3.1 Flux nominal
1. Recevoir un événement de disponibilité transmis par le DME (via webhook ou API REST).
2. Valider l'authenticité et le schéma de la donnée (signature, certificat, structure JSON).
3. Intégrer l'événement validé dans l'index central de RVSQ.
4. Mettre à jour les plages horaires correspondantes et notifier les modules internes (UC10.2).
5. Journaliser l'opération complète pour traçabilité et audit.

### 3.2 Flux alternatifs
- **A1 — Conflit détecté :** appliquer les règles de résolution de conflit (horodatage, version la plus récente).
- **A2 — Source indisponible :** déclencher un plan de reprise automatique (backoff exponentiel) et enregistrer la dernière synchronisation réussie.
- **A3 — Données corrompues :** rejet de l'événement et envoi d'un rapport à l'administrateur.

## 4. EXIGENCES SPÉCIALES
- **Performance :** propagation ≤ 5 secondes.
- **Disponibilité :** ≥ 99,9 %.
- **Journalisation :** détaillée, corrélée et horodatée (CAR14).
- **Sécurité :** canal chiffré TLS 1.3 + authentification mutuelle (CAR13).
- **Conformité :** Loi 25 (protection des renseignements personnels).

## 5. PRÉCONDITIONS
- Les connecteurs DME sont configurés et actifs.
- L'API d'intégration est alignée avec les spécifications RVSQ.
- La plateforme RVSQ est opérationnelle.

## 6. POSTCONDITIONS
- Les disponibilités du DME sont intégrées dans l'index central.
- Le journal de synchronisation contient la transaction complète.
- Les modules dépendants (recherche, notification) sont mis à jour.

## 7. POINTS D'EXTENSION
- **UC101.D – Relancer en cas d'échec :** déclenché uniquement lorsque le DME est injoignable ou qu'une erreur réseau survient.
- UC10.2 : Publication des disponibilités consolidées.
- UC14 : Journalisation et analyse d'anomalies.

## 8. CARACTÉRISTIQUES CORRESPONDANTES
CAR10 – Synchroniser les disponibilités en temps réel avec les cliniques.  
CAR13 – Sécuriser les échanges avec les DME.  
CAR14 – Journaliser les accès et événements système.

## 9. POINTS DE TRAÇABILITÉ
- CAR10 → UC10.1
- CAR13 → UC10.1
- CAR14 → UC10.1
