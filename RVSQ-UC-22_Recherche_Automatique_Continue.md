# RVSQ-UC-22 – Recherche automatique continue

## 1. BRÈVE DESCRIPTION
La **Plateforme RVSQ** exécute en continu un moteur de recherche selon les critères enregistrés par le **citoyen** afin de détecter des créneaux libres et d'en réserver temporairement.

## 2. ACTEURS IMPLIQUÉS
- **Acteur principal :** Plateforme RVSQ
- **Acteurs secondaires :** Citoyen, DME

## 3. FLUX D'ÉVÉNEMENTS
### 3.1 Flux nominal
1. Lire les critères de recherche enregistrés.
2. Interroger les DME à intervalles définis.
3. Détecter une correspondance.
4. Réserver temporairement le créneau trouvé.
5. Notifier le citoyen.
6. Journaliser l'exécution.

### 3.2 Flux alternatifs
- **Aucun résultat :** poursuivre la surveillance.
- **Quota DME atteint :** appliquer un backoff exponentiel.

## 4. EXIGENCES SPÉCIALES
- Disponibilité 24/24.
- Délai de détection < 60 secondes.
- Respect des quotas API DME.

## 5. PRÉCONDITIONS
- Critères enregistrés.
- DME intégrés et accessibles.

## 6. POSTCONDITIONS
- Notification envoyée si correspondance trouvée.

## 7. CARACTÉRISTIQUE ASSOCIÉE
CAR22 – Moteur de recherche automatisé en continu.
