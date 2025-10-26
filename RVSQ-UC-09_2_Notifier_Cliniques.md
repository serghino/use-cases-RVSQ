RVSQ-UC-09.2 : Notifier les cliniques

## BRÈVE DESCRIPTION
Informer automatiquement les cliniques lors d’événements opérationnels (ex. annulation, modification critique) afin de faciliter la gestion des plages.

## FLUX D'ÉVÉNEMENTS

### Flux de Base
1. Détecter l’événement affectant la clinique.
2. Identifier les destinataires (boîte générique, tableau d’affichage DME).
3. Construire le message opérationnel.
4. Sélectionner le canal configuré (courriel institutionnel, webhook DME).
5. Envoyer la notification et journaliser le statut.

### Flux Alternatifs
- **Aucun destinataire configuré** : à l’étape 2, journaliser et créer une alerte de configuration.
- **Webhook indisponible** : à l’étape 4, basculer vers le courriel.

## EXIGENCES SPÉCIALES
1. Délai d’envoi ≤ 60 s.
2. Redondance des canaux (webhook + courriel).
3. Conformité rédactionnelle (format institutionnel).

## PRÉ-CONDITIONS
1. Contacts cliniques configurés.
2. Intégrations DME actives.
3. Plateforme RVSQ disponible.

## POST-CONDITIONS
1. Cliniques informées en temps utile.
2. Piste d’audit disponible.
3. Actions correctives possibles.

## CARACTÉRISTIQUE ASSOCIÉE
CAR09 – Déclencher des notifications automatiques (courriel, SMS, appels)
