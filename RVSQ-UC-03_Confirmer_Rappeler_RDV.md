RVSQ-UC-03 : Envoyer automatiquement une confirmation et des rappels

## BRÈVE DESCRIPTION
Ce cas d'utilisation décrit comment le système envoie automatiquement une confirmation de rendez-vous au citoyen après une réservation et déclenche des rappels automatiques si le citoyen n'a pas confirmé sa présence avant la date du rendez-vous.

## FLUX D'ÉVÉNEMENTS

### Flux de Base

1. Le système détecte qu'un rendez-vous a été réservé par un citoyen.
2. Le système récupère les informations du rendez-vous :
   - Nom et coordonnées du citoyen
   - Date et heure du rendez-vous
   - Nom du professionnel de santé
   - Établissement/clinique
   - Type de consultation (en personne ou virtuelle)
3. Le système génère un message de confirmation incluant :
   - Détails du rendez-vous
   - Instructions (adresse, lien de téléconsultation, etc.)
   - Lien pour confirmer la présence
   - Lien pour annuler ou modifier le rendez-vous
4. Le système envoie la confirmation au citoyen via les canaux configurés :
   - Courriel
   - SMS
   - Notification dans l'application mobile (si applicable)
5. Le système enregistre l'envoi de la confirmation avec horodatage.
6. Le système programme des rappels automatiques selon le calendrier :
   - Premier rappel : 7 jours avant le rendez-vous
   - Deuxième rappel : 24 heures avant le rendez-vous
7. Le système surveille si le citoyen a confirmé sa présence.

### Flux Alternatifs

**1. Citoyen confirme sa présence**
   - Après l'étape 5, le citoyen clique sur le lien de confirmation :
     - Le système enregistre la confirmation de présence.
     - Le système envoie un accusé de réception au citoyen.
     - Le système n'envoie plus de rappels (sauf le rappel final 24h avant).
     - Le cas d'utilisation se termine.

**2. Absence de confirmation - Envoi du premier rappel**
   - À l'étape 6, 7 jours avant le rendez-vous, si le citoyen n'a pas confirmé :
     - Le système génère un message de rappel demandant la confirmation.
     - Le système envoie le rappel via les mêmes canaux (courriel, SMS).
     - Le système enregistre l'envoi du rappel avec horodatage.
     - Continuer à surveiller la confirmation.

**3. Absence de confirmation - Envoi du deuxième rappel**
   - À l'étape 6, 24 heures avant le rendez-vous, si le citoyen n'a toujours pas confirmé :
     - Le système génère un message de rappel urgent.
     - Le système envoie le rappel via tous les canaux disponibles.
     - Le système envoie une alerte à l'adjoint pour contact manuel (envoi d'email/SMS) de l'absence de confirmation.
     - Le système enregistre l'envoi du rappel avec horodatage.

**4. Échec d'envoi de la confirmation**
   - À l'étape 4, si l'envoi échoue (courriel invalide, numéro incorrect) :
     - Le système enregistre l'échec avec le motif.
     - Le système tente de renvoyer via un canal alternatif.
     - Le système alerte l'administrateur ou l'adjoint de l'échec.
     - Si tous les canaux échouent, le système génère une alerte critique.

**5. Citoyen annule le rendez-vous**
   - Après l'étape 5, le citoyen clique sur le lien d'annulation :
     - Le système annule le rendez-vous (appeler RVSQ-UC-XX : Annuler un rendez-vous).
     - Le système arrête tous les rappels programmés.
     - Le cas d'utilisation se termine.

## EXIGENCES SPÉCIALES

1. **Automatisation complète** : Le système doit fonctionner de manière autonome sans intervention humaine.
2. **Fiabilité** : Le taux de réussite d'envoi doit être supérieur à 99%.
3. **Délai d'envoi** : La confirmation doit être envoyée dans les 5 minutes suivant la réservation.
4. **Multi-canal** : Support obligatoire pour courriel et SMS au minimum.
5. **Traçabilité** : Tous les envois doivent être journalisés avec horodatage et statut de livraison.
6. **Personnalisation** : Les messages doivent être personnalisés avec les informations du citoyen et du rendez-vous.
7. **Accessibilité** : Les messages doivent être clairs, dans la langue préférée du citoyen, et accessibles.
8. **Sécurité** : Les liens de confirmation/annulation doivent être sécurisés et à usage unique.

## PRÉ-CONDITIONS

1. Un rendez-vous a été réservé dans le système.
2. Les coordonnées du citoyen (courriel, téléphone) sont disponibles et valides.
3. Le service de messagerie (courriel, SMS) est opérationnel.
4. Les informations du rendez-vous sont complètes dans le système.

## POST-CONDITIONS

1. Une confirmation de rendez-vous a été envoyée au citoyen.
2. L'envoi de la confirmation est journalisé dans le système.
3. Des rappels automatiques sont programmés selon le calendrier défini.
4. Le système surveille l'état de confirmation du citoyen.

## POINTS D'EXTENSION

1. **Annulation de rendez-vous** : Si le citoyen clique sur le lien d'annulation, appeler RVSQ-UC-XX : Annuler un rendez-vous.

## CARACTÉRISTIQUE ASSOCIÉE

**CAR03** – Envoyer automatiquement une confirmation et des rappels
