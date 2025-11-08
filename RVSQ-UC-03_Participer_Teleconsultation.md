RVSQ-UC-03 : Participer à une téléconsultation

## BRÈVE DESCRIPTION
Permettre à un citoyen de participer à une téléconsultation avec un professionnel de santé via la plateforme RVSQ. Le citoyen accède à la consultation virtuelle à l'heure prévue, se connecte à la plateforme de téléconsultation intégrée, et communique avec le professionnel en temps réel par vidéo, audio et messagerie instantanée.

## FLUX D'ÉVÉNEMENTS

### Flux de Base
1. Le système affiche la liste des rendez-vous du jour.
2. Le citoyen sélectionne le rendez-vous de téléconsultation prévu.
3. Le système affiche les détails du rendez-vous et un bouton "Rejoindre la téléconsultation".
4. Le citoyen clique sur "Rejoindre la téléconsultation".
5. Le système établit la connexion avec la plateforme de téléconsultation.
6. Le système affiche la salle d'attente virtuelle avec un message indiquant que le professionnel va bientôt rejoindre.
7. Le professionnel de santé rejoint la téléconsultation.
8. Le système établit la connexion vidéo/audio entre le citoyen et le professionnel.
9. Le professionnel ou le citoyen termine la consultation.
10. Le système met fin à la connexion vidéo/audio.
11. Le système affiche un message de fin de consultation.
12. Le système enregistre les métadonnées de la consultation (durée, participants, date/heure).

### Flux Alternatifs

**5'. Erreur de connexion à la plateforme de téléconsultation**
   - À l'étape 5, si la connexion échoue :
     - Le système affiche un message d'erreur de connexion.
     - Le système vérifie la connexion Internet du citoyen.
     - Le système propose de réessayer ou de contacter le support technique.
     - Si le citoyen choisit de réessayer, retour à l'étape 4.
     - Sinon, le cas d'utilisation se termine.

**6'. Le professionnel ne rejoint pas la consultation**
   - À l'étape 6, si le professionnel ne rejoint pas après 5 minutes :
     - Le système affiche un message d'attente prolongée.
     - Le système propose au citoyen de :
       - Continuer à attendre
       - Quitter la consultation
     - Si le citoyen quitte, le cas d'utilisation se termine.

**8'. Déconnexion pendant la consultation**
   - À l'étape 8, si la connexion est interrompue :
     - Le système tente automatiquement de rétablir la connexion.
     - Le système affiche un message "Reconnexion en cours...".
     - Si la reconnexion réussit dans les 30 secondes, la consultation reprend.
     - Si la reconnexion échoue, le système affiche un message d'erreur.
     - Le système enregistre l'interruption dans les journaux.
     - Le citoyen peut réessayer de rejoindre la consultation (retour à l'étape 4).

**4'. Tentative de connexion avant l'heure prévue**
   - À l'étape 4, si le citoyen tente de rejoindre plus de 15 minutes avant l'heure :
     - Le système affiche un message indiquant l'heure de début de la consultation.
     - Le système affiche un compte à rebours jusqu'à l'ouverture de la salle d'attente.
     - Le bouton "Rejoindre la téléconsultation" reste désactivé.
     - Le cas d'utilisation se termine.

## PRÉ-CONDITIONS

1. L'utilisateur doit être authentifié.
2. Le citoyen a réservé un rendez-vous de type "virtuel" (RVSQ-UC-02).
3. La plateforme de téléconsultation est fonctionnelle.
4. Le citoyen dispose d'un appareil avec caméra, microphone et connexion Internet.

## POST-CONDITIONS

1. La téléconsultation a eu lieu entre le citoyen et le professionnel.
2. Les métadonnées de la consultation sont enregistrées dans le système.
3. Le citoyen et le professionnel peuvent accéder à l'historique de la consultation.
