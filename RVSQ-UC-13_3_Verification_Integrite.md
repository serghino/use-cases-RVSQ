RVSQ-UC-13.3 : Vérification d’intégrité

## BRÈVE DESCRIPTION
Vérifier l’intégrité des messages et données échangés entre RVSQ et les systèmes intégrés.

## FLUX D'ÉVÉNEMENTS

### Flux de Base
1. Recevoir un message externe.
2. Valider la signature et l’empreinte.
3. Rejeter et consigner toute altération détectée.
4. Accepter et traiter les contenus intègres.

### Flux Alternatifs
- **Signature invalide** : refuser le message, journaliser, alerter.
- **Horodatage expiré** : appliquer la politique de rejet/renvoi.

## EXIGENCES SPÉCIALES
1. Signatures numériques et horodatage.
2. Journaux inviolables.
3. Conformité sécurité.

## PRÉ-CONDITIONS
1. Clés et certificats à jour.
2. Politique d’horodatage appliquée.
3. RVSQ opérationnelle.

## POST-CONDITIONS
1. Messages validés.
2. Altérations bloquées.
3. Traçabilité complète.

## CARACTÉRISTIQUE ASSOCIÉE
CAR13 – Utiliser des protocoles sécurisés pour la récupération et l’échange de données
