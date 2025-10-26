RVSQ-UC-23 : Alerter l’utilisateur lors d’une disponibilité trouvée

## BRÈVE DESCRIPTION
Alerter immédiatement le citoyen lorsqu’un rendez-vous correspondant est détecté, via le canal préféré (SMS, courriel, application) et bascule si besoin.

## FLUX D'ÉVÉNEMENTS

### Flux de Base
1. Émettre l’événement « correspondance trouvée ».
2. Sélectionner le canal préféré.
3. Construire le message avec lien d’action.
4. Envoyer la notification.
5. Recevoir l’accusé et journaliser.

### Flux Alternatifs
- **Canal préféré indisponible** : basculer vers un canal de secours.
- **Politique anti-spam** : regrouper/étaler les envois.

## EXIGENCES SPÉCIALES
1. Délai bout en bout ≤ 30 s.
2. Accusé requis.
3. Messages accessibles et sûrs (liens signés).

## PRÉ-CONDITIONS
1. Préférences configurées.
2. Fournisseurs SMS/courriel/push intégrés.
3. RVSQ opérationnelle.

## POST-CONDITIONS
1. Citoyen alerté à temps.
2. Statuts tracés.
3. Lien mène au parcours de confirmation.

## CARACTÉRISTIQUE ASSOCIÉE
CAR23 – Envoyer des notifications instantanées (SMS, courriel, application mobile)
