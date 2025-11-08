RVSQ-UC-02 : Réserver un rendez-vous

## BRÈVE DESCRIPTION
Permettre à un citoyen de réserver un rendez-vous médical après avoir consulté les disponibilités via la recherche. Le citoyen sélectionne une plage horaire disponible, confirme ses informations personnelles, et le système enregistre la réservation. Une confirmation est envoyée au citoyen et au professionnel de santé concerné.

## FLUX D'ÉVÉNEMENTS

### Flux de Base

1. Le citoyen sélectionne un professionnel ou une clinique parmi les résultats.
2. Le système affiche les détails du professionnel/clinique et les disponibilités.
3. Le citoyen sélectionne une plage horaire disponible.
4. Le citoyen vérifie et complète les informations.
5. Le citoyen clique sur "Confirmer la réservation".
6. Le système enregistre la réservation.
7. Le système affiche une confirmation de réservation avec :
    - Numéro de confirmation
    - Récapitulatif complet du rendez-vous
    - Instructions spécifiques (si applicable)
8. Le système envoie une notification de confirmation au citoyen (selon ses préférences).
9. Le système envoie une notification au professionnel/clinique de la nouvelle réservation.

### Flux Alternatifs

**5'. Informations personnelles incomplètes**
   - À l'étape 5, si des informations obligatoires sont manquantes :
     - Le système affiche un message indiquant les champs requis.
     - Le citoyen complète les informations manquantes.
     - Retour à l'étape 5.

**7'. Erreur lors de l'enregistrement**
   - À l'étape 7, si le système rencontre une erreur :
     - Le système affiche un message d'erreur technique.
     - Le système propose de réessayer ou de contacter le support.
     - Si le citoyen choisit de réessayer, retour à l'étape 5.
     - Sinon, le cas d'utilisation se termine.

**8'. Échec de l'envoi de notification au citoyen**
   - À l'étape 8, si l'envoi de la notification au citoyen échoue :
     - Le système enregistre l'échec dans les journaux.
     - La réservation reste valide.
     - Le citoyen peut consulter sa réservation dans son profil.
     - Le système programme une nouvelle tentative d'envoi automatique.

**9'. Échec de l'envoi de notification au professionnel/clinique**
   - À l'étape 9, si l'envoi de la notification au professionnel/clinique échoue :
     - Le système enregistre l'échec dans les journaux.
     - La réservation reste valide.
     - Le système programme une nouvelle tentative d'envoi automatique.
     - Le cas d'utilisation se termine.


## PRÉ-CONDITIONS

1. L'utilisateur doit être authentifié.
2. Le citoyen a effectué une recherche de rendez-vous (RVSQ-UC-01).
3. Des résultats de recherche avec des disponibilités sont affichés.
4. L'API DME est fonctionnelle.

## POST-CONDITIONS

1. La réservation est enregistrée dans le système.
2. Un numéro de confirmation unique est généré.
3. Le citoyen reçoit une confirmation de réservation.
4. Le professionnel/clinique est notifié de la nouvelle réservation.
5. La plage horaire n'est plus disponible pour d'autres citoyens.
