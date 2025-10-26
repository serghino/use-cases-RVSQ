RVSQ-UC-01 : Rechercher un professionnel de santé

## BRÈVE DESCRIPTION
Ce cas d'utilisation permet à un citoyen de rechercher un professionnel de santé ou une clinique via un moteur de recherche centralisé et optimisé qui interroge l'ensemble des établissements connectés à la plateforme RVSQ.

## FLUX D'ÉVÉNEMENTS

### Flux de Base

1. Le citoyen accède à la plateforme RVSQ.
2. La plateforme affiche la page d'accueil avec le moteur de recherche centralisé.
3. Le citoyen saisit un critère de recherche :
   - Nom du professionnel
   - Type de spécialité médicale
   - Nom de la clinique ou établissement
4. Le citoyen lance la recherche.
5. La plateforme interroge le système centralisé qui consolide les données de tous les DME des cliniques et hôpitaux connectés.
6. La plateforme affiche les résultats de recherche classés par pertinence, incluant :
   - Nom du professionnel
   - Spécialité
   - Établissement/clinique
   - Adresse
   - Prochaines disponibilités
7. Le citoyen consulte les résultats.

### Flux Alternatifs

**1. Aucun résultat trouvé**
   - À l'étape 6, si aucun résultat ne correspond aux critères :
     - La plateforme affiche un message indiquant l'absence de résultats dans le système centralisé.
     - La plateforme suggère de modifier les critères de recherche ou de réessayer ultérieurement.
     - Le citoyen peut modifier ses critères et relancer la recherche.
     - Retour à l'étape 3.

**2. Erreur de connexion au système centralisé**
   - À l'étape 5, si le système centralisé est temporairement inaccessible :
     - La plateforme affiche un message d'erreur technique.
     - La plateforme suggère de réessayer dans quelques instants.
     - Le cas d'utilisation se termine.

## EXIGENCES SPÉCIALES

1. **Performance** : Le moteur de recherche doit retourner les résultats en moins de 3 secondes pour 95% des requêtes, même lors de l'interrogation de multiples sources de données.
2. **Disponibilité** : Le service de recherche centralisé doit être disponible 99.9% du temps.
3. **Accessibilité** : L'interface de recherche doit être conforme aux normes WCAG 2.1 niveau AA.
4. **Centralisation** : Le moteur doit consolider les données provenant de tous les DME des établissements connectés en un point d'accès unique.
5. **Optimisation** : Le moteur de recherche doit utiliser des algorithmes de classement par pertinence pour présenter les résultats les plus appropriés en premier.
6. **Scalabilité** : Le système doit pouvoir gérer au moins 10 000 recherches simultanées.

## PRÉ-CONDITIONS

1. La plateforme RVSQ est accessible et opérationnelle.
2. Le système centralisé de recherche est fonctionnel.
3. Au moins un DME d'une clinique ou d'un hôpital est connecté au système centralisé.
4. Les données des professionnels de santé sont disponibles dans le système centralisé.

## POST-CONDITIONS

1. Les résultats de recherche provenant du système centralisé sont affichés au citoyen.
2. Le système a journalisé la requête de recherche (pour analyse et amélioration du moteur).
3. Les résultats restent valides et consultables par le citoyen.

## CARACTÉRISTIQUE ASSOCIÉE

**CAR01** – Offrir un moteur de recherche centralisé et optimisé
