# RVSQ-UC-04 : Annuler un rendez-vous

## BRÈVE DESCRIPTION
Ce cas d'utilisation décrit le processus permettant à un **citoyen** ou à un **professionnel de santé** d'annuler un rendez-vous confirmé via la **plateforme RVSQ**.  
L'annulation entraîne une mise à jour immédiate des disponibilités dans le système, notifie les parties concernées (citoyen, clinique, DME) et assure la cohérence des informations affichées dans les agendas et les interfaces publiques.

## FLUX D'ÉVÉNEMENTS

### Flux de Base

1. Le citoyen accède à la section **Mes rendez-vous** de son compte RVSQ.
    - Le professionnel accède à son **agenda clinique** synchronisé avec le DME via la plateforme RVSQ.
2. Le système affiche la liste des rendez-vous planifiés avec leurs détails (date, heure, type de consultation, statut).
3. L'utilisateur sélectionne le rendez-vous à annuler.
4. Le système demande une confirmation explicite de l'action d'annulation.
5. Après validation :
    - Le citoyen ou le professionnel confirme l'intention d'annuler.
    - Le système envoie une requête d'annulation au **DME** associé à la clinique.
6. Le DME traite la demande et confirme la suppression du rendez-vous.
7. Le système met à jour l'état du rendez-vous dans la base centrale RVSQ (statut = *Annulé*).
8. Les disponibilités correspondantes sont automatiquement réintégrées dans le moteur de recherche.
9. Le système déclenche l'envoi de notifications aux parties concernées :
    - Citoyen (confirmation d'annulation)
    - Clinique et professionnel (notification d'annulation)
10. L'événement est journalisé (horodatage, utilisateur, motif, statut).

---

### Flux Alternatifs

**5'. DME temporairement indisponible**
- À l'étape 5, si le DME ne répond pas :
    - Le système place la requête d'annulation dans une **file d'attente sécurisée**.
    - Une relance automatique est planifiée (exponentielle jusqu'à 3 tentatives).
    - Le citoyen reçoit une notification indiquant que la demande est en attente de validation.
    - Retour automatique à l'étape 6 après reprise du DME.

**6'. Annulation refusée par la clinique (ex. délai dépassé)**
- À l'étape 6, si le DME rejette la demande :
    - Le système affiche un message explicatif (délai ou politique interne).
    - Le citoyen peut contacter la clinique via un lien direct ou soumettre une demande manuelle d'annulation.
    - Le cas d'utilisation se termine.

**9'. Échec de notification**
- À l'étape 9, si l'envoi de notification échoue (courriel/SMS) :
    - Le système journalise l'erreur.
    - Le système effectue une **nouvelle tentative automatique** dans les 5 minutes.
    - Si l'échec persiste, une alerte est envoyée à l'administrateur système.
    - Le cas d'utilisation se poursuit jusqu'à l'étape 10.

---

## PRÉ-CONDITIONS

1. Le citoyen est authentifié et dispose d'un rendez-vous actif dans son profil.
2. Le professionnel est connecté à la plateforme via son DME.
3. Le DME et le service de messagerie sont disponibles.
4. Les politiques d'annulation (délai minimal, restrictions) sont configurées dans RVSQ.

---

## POST-CONDITIONS

1. Le rendez-vous est marqué comme **annulé** dans RVSQ et dans le DME.
2. Les créneaux libérés redeviennent disponibles dans les recherches publiques.
3. Les notifications ont été envoyées ou planifiées.
4. L'événement complet est archivé dans les journaux d'audit.

---

## CARACTÉRISTIQUES ASSOCIÉES

- **CAR08** – Gestion automatisée des annulations
- **CAR09** – Notifications multi-canaux et traçabilité
- **CAR14** – Journalisation des événements critiques

---

## REMARQUES COMPLÉMENTAIRES
- Le citoyen ne peut annuler que ses propres rendez-vous confirmés.
- Le professionnel peut annuler des rendez-vous directement depuis son **agenda clinique synchronisé**, ce qui met instantanément à jour la plateforme RVSQ.