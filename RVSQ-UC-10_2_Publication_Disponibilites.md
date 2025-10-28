RVSQ-UC-10.2 : Publication des mises à jour

## BRÈVE DESCRIPTION
Publier les disponibilités mises à jour afin qu’elles soient visibles immédiatement côté recherche RVSQ.

## FLUX D'ÉVÉNEMENTS

### Flux de Base
1. Détecter une modification validée dans l’index.
2. Mettre à jour les vues et caches de recherche.
3. Exposer l’état à jour aux utilisateurs.
4. Journaliser la publication.

### Flux Alternatifs
- **Cache indisponible** : basculer en lecture directe avec dégradation maîtrisée.
- **Latence excessive** : déclencher une alerte.

## EXIGENCES SPÉCIALES
1. Rafraîchissement quasi temps réel.
2. Observabilité (métriques de latence/erreur).
3. Cohérence forte lors de la réservation.

## PRÉ-CONDITIONS
1. Index central à jour.
2. Infrastructure de cache opérationnelle.
3. RVSQ disponible.

## POST-CONDITIONS
1. Disponibilités visibles immédiatement.
2. Piste d’audit de publication.
3. Expérience utilisateur fluide.

## CARACTÉRISTIQUE ASSOCIÉE
CAR10 – Synchroniser les disponibilités en temps réel avec les cliniques
