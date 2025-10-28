RVSQ-UC-09.1 : Notifier les citoyens

## BRÈVE DESCRIPTION
Envoyer automatiquement des notifications au citoyen lorsque des événements pertinents surviennent (ex. libération de créneau correspondant à ses critères).

## FLUX D'ÉVÉNEMENTS

### Flux de Base
1. Détecter l’événement (créneau libéré).
2. Identifier les citoyens inscrits correspondants.
3. Construire le message (contenu, langue, lien d’action).
4. Sélectionner le canal (courriel, SMS, notification mobile) selon les préférences.
5. Envoyer la notification via le service de messagerie.
6. Recevoir le statut d’envoi et journaliser.

### Flux Alternatifs
- **Aucun citoyen correspondant** : à l’étape 2, ne rien envoyer et journaliser.
- **Échec d’envoi** : à l’étape 5, appliquer les relances, puis alerter en cas d’échec définitif.

## EXIGENCES SPÉCIALES
1. Délai de déclenchement ≤ 30 s.
2. Politique de relance configurable.
3. Messages accessibles (liens clairs et sécurisés).
4. Journalisation complète des envois et statuts.

## PRÉ-CONDITIONS
1. Préférences citoyen enregistrées.
2. Intégrations courriel/SMS/app opérationnelles.
3. Plateforme RVSQ disponible.

## POST-CONDITIONS
1. Citoyens concernés notifiés.
2. Statuts d’envoi tracés.
3. Lien d’action mène au parcours de confirmation.

## CARACTÉRISTIQUE ASSOCIÉE
CAR09 – Déclencher des notifications automatiques (courriel, SMS, appels)
