RVSQ-UC-01 : Rechercher un rendez-vous

## BRÈVE DESCRIPTION
Permettre à un citoyen de trouver un rendez-vous médical en indiquant le type de consultation et, au besoin, une spécialité. Il peut ajouter quelques filtres simples (localisation, langue, mode de consultation : en personne ou virtuel, distance). Le moteur de recherche centralisé interroge les établissements et professionnels connectés à la plateforme RVSQ et affiche les disponibilités pertinentes.

## FLUX D'ÉVÉNEMENTS

### Flux de Base

1. Le citoyen accède à la plateforme RVSQ.
2. Le système affiche les filtres de recherche.
3. Le citoyen définit ses besoins et critères de recherche :
   - **Type de rendez-vous** : Consultation urgente, prioritaire ou de suivi
   - **Spécialité médicale** : Médecin généraliste, cardiologue, pédiatre, dermatologue, etc. (optionnel)
   - **Nom du professionnel ou de la clinique** : Recherche spécifique si désiré (optionnel)
4. Le citoyen configure les critères de localisation :
   - **Préférence pour la consultation** : En personne, virtuelle, ou les deux
   - **Code postal** et **rayon de recherche** (distance en km)
5. Le citoyen peut optionnellement appliquer des filtres avancés :
   - **Langue de service** : Français, anglais.
   - **Disponibilités** : Plages horaires spécifiques, dates précises
6. Le citoyen lance la recherche.
7. Le système interroge l'API DME centralisé.
8. Le système affiche les résultats de recherche classés par pertinence, incluant :
   - Nom du professionnel
   - Spécialité
   - Établissement/clinique
   - Adresse et distance
   - Langues parlées
   - Prochaines disponibilités
   - Type de consultation disponible (présentiel/virtuel)
9. Le citoyen consulte les résultats.

### Flux Alternatifs

**8'. Aucun résultat trouvé**
   - À l'étape 8, si aucun résultat ne correspond aux critères :
     - Le système affiche un message indiquant l'absence de résultats dans l'API DME centralisé.
     - Le système affiche les critères de recherche appliqués.
     - Le système suggère de modifier les critères de recherche (élargir le rayon, retirer des filtres, changer de spécialité).
     - Le citoyen peut modifier ses critères et relancer la recherche.
     - Retour à l'étape 3.

**9'. Modification des critères après affichage des résultats**
   - Après l'étape 9, le citoyen souhaite affiner ou modifier ses critères :∫
     - Le citoyen accède à la section de modification des critères.
     - Le système affiche les critères actuels.
     - Le citoyen modifie un ou plusieurs critères/filtres.
     - Retour à l'étape 6.

**7'. Erreur de connexion à l'API DME centralisé**
   - À l'étape 7, si l'API DME est temporairement inaccessible :
     - Le système affiche un message d'erreur technique.
     - Le système suggère de réessayer dans quelques instants.
     - Le cas d'utilisation se termine.

## PRÉ-CONDITIONS

1. L'utilisateur doit etre authentifié.
2. L'API DME est fonctionnelle.

## POST-CONDITIONS

1. Les résultats de recherche sont affichés au citoyen.
2. Les critères et filtres appliqués sont visibles et modifiables par le citoyen.
