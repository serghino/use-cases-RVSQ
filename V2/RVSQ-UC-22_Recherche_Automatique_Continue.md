# RVSQ-UC-22 – Recherche automatique continue

## 1. BRÈVE DESCRIPTION
La **Plateforme RVSQ** exécute en continu un **moteur de recherche automatisé** selon les critères enregistrés par le **Citoyen**, afin de détecter des créneaux médicaux libres et d'en effectuer la réservation temporaire.  
Ce processus fonctionne de manière asynchrone, même lorsque l'utilisateur n'est pas connecté.

## 2. ACTEURS IMPLIQUÉS
- **Acteur principal :** Plateforme RVSQ
- **Acteurs secondaires :** Citoyen, DME

## 3. FLUX D'ÉVÉNEMENTS
### 3.1 Flux nominal
1. Lire les **critères de recherche enregistrés** dans le profil citoyen.
2. Interroger les **DME** à intervalles prédéfinis.
3. Détecter une **correspondance** avec un créneau disponible.
4. **Réserver temporairement** le créneau trouvé (verrouillage 5 minutes).
5. **Notifier le citoyen** de la disponibilité détectée (UC23).
6. **Journaliser** l'exécution et la notification associée.

### 3.2 Flux alternatifs
- **A1 — Aucun résultat trouvé :** déclenchement de l'extension **UC22.E – Surveillance continue** (maintien de l'écoute et replanification du cycle).
- **A2 — Quota DME atteint :** déclenchement de l'extension **UC22.E – Backoff exponentiel** (ralentissement progressif des appels API).

## 4. EXIGENCES SPÉCIALES
- **Disponibilité :** 24 h/24 et 7 j/7.
- **Délai de détection :** < 60 secondes entre deux cycles.
- **Respect :** des quotas API DME (RFC 6585).
- **Traçabilité :** journalisation de chaque itération et résultat.

## 5. PRÉCONDITIONS
- Critères enregistrés par le citoyen.
- DME intégrés et accessibles.
- Authentification préalable réussie (CAR13).

## 6. POSTCONDITIONS
- Notification envoyée au citoyen si correspondance détectée.
- Entrée de journal créée pour chaque cycle.

## 7. POINTS D'EXTENSION
- **UC22.D – Backoff exponentiel :** exécuté lors d'un dépassement de quota API.
- **UC22.E – Surveillance continue :** exécuté en cas d'absence de résultat sur plusieurs cycles.
- **UC23 :** Notification instantanée liée à une disponibilité détectée.

## 8. CARACTÉRISTIQUE ASSOCIÉE
CAR22 – Moteur de recherche automatisé en continu.

## 9. POINTS DE TRAÇABILITÉ
- CAR22 → UC22
- CAR09 → UC22 (notification multi-canaux)
- CAR13 → UC22 (authentification et sécurité de la session)
