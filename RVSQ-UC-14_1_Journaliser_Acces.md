RVSQ-UC-14.1 : Journaliser les accès

## BRÈVE DESCRIPTION
Journaliser de manière exhaustive les accès et opérations sensibles.

## FLUX D'ÉVÉNEMENTS

### Flux de Base
1. Détecter l’action sensible.
2. Capturer les champs (qui, quoi, quand, où).
3. Stocker dans un journal immuable.
4. Mettre à disposition pour audit.

### Flux Alternatifs
- **Stockage indisponible** : file d’attente puis réplication à la reprise.
- **Demande d’extraction** : accès réservé aux rôles autorisés.

## EXIGENCES SPÉCIALES
1. Intégrité (immutabilité, horodatage NTP).
2. Rétention conforme MSSS/RAMQ.
3. Accès restreint aux auditeurs.

## PRÉ-CONDITIONS
1. Mécanismes de journalisation actifs.
2. Rôles d’audit définis.
3. RVSQ opérationnelle.

## POST-CONDITIONS
1. Journaux complets et consultables.
2. Piste d’audit disponible.
3. Alertes en cas d’événement anormal.

## CARACTÉRISTIQUE ASSOCIÉE
CAR14 – Journaliser et tracer tous les accès
