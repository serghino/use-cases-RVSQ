RVSQ-UC-01 : Rechercher un rendez-vous

## BRÈVE DESCRIPTION
Ce cas d'utilisation permet à un citoyen de rechercher un rendez-vous médical en définissant ses besoins (type de consultation, spécialité) et en appliquant des critères de recherche et filtres avancés (localisation, langue, préférence de consultation) via un moteur de recherche centralisé et optimisé qui interroge l'ensemble des établissements connectés à la plateforme RVSQ.

## FLUX D'ÉVÉNEMENTS

### Flux de Base

1. Le citoyen accède à la plateforme RVSQ.
2. La plateforme affiche les filtres de recherche.
3. Le citoyen définit ses besoins et critères de recherche :
   - **Type de rendez-vous** : Consultation urgente, prioritaire ou de suivi
   - **Spécialité médicale** : Médecin généraliste, cardiologue, pédiatre, dermatologue, etc. (optionnel)
   - **Nom du professionnel ou de la clinique** : Recherche spécifique si désiré (optionnel)
4. Le citoyen configure les critères de localisation :
   - **Préférence pour la consultation** : En personne, virtuelle, ou les deux
   - **Code postal** et **rayon de recherche** (distance en km)
5. Le citoyen peut optionnellement appliquer des filtres avancés :
   - **Langue de service** : Français, anglais, espagnol, etc.
   - **Disponibilités** : Plages horaires spécifiques, dates précises
6. Le citoyen lance la recherche.
7. La plateforme interroge le système centralisé qui consolide les données de tous les DME des cliniques et hôpitaux connectés.
8. La plateforme affiche les résultats de recherche classés par pertinence, incluant :
   - Nom du professionnel
   - Spécialité
   - Établissement/clinique
   - Adresse et distance
   - Langues parlées
   - Prochaines disponibilités
   - Type de consultation disponible (présentiel/virtuel)
9. Le citoyen consulte les résultats.

### Flux Alternatifs

**1. Aucun résultat trouvé**
   - À l'étape 8, si aucun résultat ne correspond aux critères :
     - La plateforme affiche un message indiquant l'absence de résultats dans le système centralisé.
     - La plateforme affiche les critères de recherche appliqués.
     - La plateforme suggère de modifier les critères de recherche (élargir le rayon, retirer des filtres, changer de spécialité).
     - Le citoyen peut modifier ses critères et relancer la recherche.
     - Retour à l'étape 3.

**2. Modification des critères après affichage des résultats**
   - Après l'étape 9, le citoyen souhaite affiner ou modifier ses critères :
     - Le citoyen accède à la section de modification des critères.
     - La plateforme affiche les critères actuels.
     - Le citoyen modifie un ou plusieurs critères/filtres.
     - Retour à l'étape 6.

**3. Réinitialisation des critères de recherche**
   - À l'étape 3, 4 ou 5, le citoyen choisit de réinitialiser tous les critères :
     - La plateforme supprime tous les critères et filtres appliqués.
     - La plateforme affiche les champs de recherche vierges avec valeurs par défaut.
     - Retour à l'étape 3.

**4. Erreur de connexion au système centralisé**
   - À l'étape 7, si le système centralisé est temporairement inaccessible :
     - La plateforme affiche un message d'erreur technique.
     - La plateforme suggère de réessayer dans quelques instants.
     - Le cas d'utilisation se termine.

## EXIGENCES SPÉCIALES

1. **Performance** : Le moteur de recherche doit retourner les résultats en moins de 5 secondes pour 95% des requêtes.
2. **Temps de réponse des filtres** : L'application ou la modification de filtres doit rafraîchir les résultats en moins de 2 secondes.
3. **Disponibilité** : Le service de recherche centralisé doit être disponible 99.9% du temps.
4. **Accessibilité** : L'interface de recherche et les contrôles de filtrage doivent être conformes aux normes WCAG 2.1 niveau AA et utilisables au clavier.
5. **Centralisation** : Le moteur doit consolider les données provenant de tous les DME des établissements connectés en un point d'accès unique.
6. **Optimisation** : Le moteur de recherche doit utiliser des algorithmes de classement par pertinence pour présenter les résultats les plus appropriés en premier.
7. **Scalabilité** : Le système doit pouvoir gérer au moins 10 000 recherches simultanées.
8. **Précision géographique** : Le filtre de localisation doit supporter la géolocalisation automatique et la saisie manuelle du code postal avec une précision au kilomètre près.
9. **Persistance des filtres** : Les critères et filtres appliqués doivent rester actifs lors de la navigation entre les résultats.
10. **Exhaustivité des données** : Les listes de spécialités, langues et types d'établissements doivent être complètes et à jour selon les standards médicaux québécois.

## PRÉ-CONDITIONS

1. La plateforme RVSQ est accessible et opérationnelle.
2. Le système centralisé de recherche est fonctionnel.
3. Au moins un DME d'une clinique ou d'un hôpital est connecté au système centralisé.
4. Les données des professionnels de santé et leurs disponibilités sont disponibles dans le système centralisé.
5. Les métadonnées des professionnels (spécialité, langues, localisation, type de consultation) sont à jour dans le système centralisé.

## POST-CONDITIONS

1. Les résultats de recherche provenant du système centralisé sont affichés au citoyen.
2. Le système a journalisé la requête de recherche et les filtres utilisés.
3. Les résultats restent valides et consultables par le citoyen.
4. Les critères et filtres appliqués sont visibles et modifiables par le citoyen.

## POINTS D'EXTENSION

1. **Sauvegarde des préférences de recherche** : Si le citoyen est authentifié, il peut sauvegarder ses critères et filtres préférés pour les recherches futures.

## CARACTÉRISTIQUES ASSOCIÉES

**CAR01** – Offrir un moteur de recherche centralisé et optimisé  
**CAR02** – Fournir des filtres de recherche avancés (spécialité, langue, localisation)
