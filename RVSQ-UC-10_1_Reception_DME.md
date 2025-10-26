RVSQ-UC-10.1 : Réception des événements DME

## BRÈVE DESCRIPTION
Réceptionner, valider et intégrer les notifications de disponibilités envoyées par les DME.

## FLUX D'ÉVÉNEMENTS

### Flux de Base
1. Recevoir un événement de disponibilité.
2. Valider l’authenticité et le schéma.
3. Intégrer l’événement dans l’index central.
4. Journaliser l’opération.

### Flux Alternatifs
- **Conflit détecté** : appliquer les règles de résolution.
- **Source indisponible** : plan de reprise (backoff), marquer l’horodatage de dernière synchro.

## EXIGENCES SPÉCIALES
1. Propagation ≤ 5 s.
2. Disponibilité ≥ 99,9 %.
3. Journalisation détaillée.

## PRÉ-CONDITIONS
1. Connecteurs DME configurés.
2. API alignées.
3. RVSQ opérationnelle.

## POST-CONDITIONS
1. Index à jour.
2. Traçabilité des événements.
3. Recherche reflétant l’état réel.

## CARACTÉRISTIQUE ASSOCIÉE
CAR10 – Synchroniser les disponibilités en temps réel avec les cliniques
