# RVSQ-UC-05 : Gérer ses préférences

## BRÈVE DESCRIPTION
Permettre à un **citoyen** de définir, modifier et sauvegarder ses **préférences personnelles** sur la **plateforme RVSQ** afin d'adapter son expérience et d'automatiser certains comportements du système.  
Ces préférences concernent notamment la langue, les canaux de notification, le mode de consultation et les cliniques favorites.

## FLUX D'ÉVÉNEMENTS

### Flux de Base

1. Le citoyen accède à la plateforme RVSQ et ouvre la section **Mes préférences**.
2. Le système affiche les préférences actuellement enregistrées :
    - **Langue d'affichage** (français, anglais)
    - **Mode de consultation préféré** (présentiel, virtuel ou les deux)
    - **Canaux de notification** (courriel, SMS, notification mobile)
    - **Professionnel ou clinique favori** (optionnel)
3. Le citoyen modifie un ou plusieurs paramètres selon ses besoins.
4. Le système valide les données saisies (format, cohérence, contraintes).
5. Le citoyen confirme la mise à jour.
6. Le système enregistre les modifications dans la base de données centrale.
7. Le système applique immédiatement les nouvelles préférences aux modules dépendants (notifications, recherche automatique, etc.).
8. Une confirmation visuelle s'affiche et une notification est envoyée au citoyen.
9. L'événement est journalisé pour assurer la traçabilité.

---

### Flux Alternatifs

**4'. Erreur de validation**
- À l'étape 4, si certaines données ne respectent pas les contraintes (ex. champ manquant, format invalide) :
    - Le système met en évidence les champs incorrects.
    - Un message d'erreur explicite s'affiche.
    - Le citoyen corrige les informations.
    - Retour à l'étape 3.

**6'. Service de sauvegarde indisponible**
- À l'étape 6, si la base de données ou le service de stockage est temporairement inaccessible :
    - Le système enregistre les modifications dans une file d'attente locale.
    - Une tentative automatique de synchronisation sera effectuée dès que le service redevient disponible.
    - Le citoyen est informé que la mise à jour sera appliquée ultérieurement.

**8'. Notification différée**
- À l'étape 8, si le service de messagerie est momentanément indisponible :
    - Le système journalise l'échec d'envoi.
    - Une relance automatique de la notification est planifiée.
    - L'opération principale (sauvegarde des préférences) reste considérée comme réussie.

**9'. Échec de journalisation**
- À l'étape 9, si la journalisation échoue (ex. surcharge temporaire du service de logs) :
    - Le système conserve les événements dans un buffer temporaire.
    - Les entrées seront répliquées dès la reprise du service.
    - Une alerte technique interne est générée.

---

## PRÉ-CONDITIONS

1. Le citoyen est **authentifié** et dispose d'un profil actif.
2. Le service de gestion des préférences est **opérationnel**.
3. Le service de messagerie et la base de données sont accessibles.

---

## POST-CONDITIONS

1. Les préférences mises à jour sont enregistrées et immédiatement actives.
2. Les modules de notification et de recherche utilisent les nouvelles valeurs.
3. Un journal d'audit complet est conservé pour toute modification.

---

## CARACTÉRISTIQUES ASSOCIÉES

- **CAR06** – Sauvegarder les préférences personnelles (langue, filtres, notifications)
- **CAR09** – Gérer les canaux de notification et leurs priorités
- **CAR14** – Assurer la traçabilité et la journalisation des modifications

---

## POINTS DE TRAÇABILITÉ

- CAR06 → UC05
- CAR09 → UC05
- CAR14 → UC05
