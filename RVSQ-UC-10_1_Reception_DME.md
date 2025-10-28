# RVSQ-UC-10.1 – Réception des événements DME

## 1. BRÈVE DESCRIPTION
La **Plateforme RVSQ** réceptionne, valide et intègre les notifications de disponibilités envoyées par les DME afin d'assurer la synchronisation en temps réel des créneaux médicaux.

## 2. ACTEURS IMPLIQUÉS
- **Acteur principal :** Plateforme RVSQ
- **Acteurs secondaires :** DME, Administrateur système

## 3. FLUX D'ÉVÉNEMENTS
### 3.1 Flux nominal
1. Recevoir un événement de disponibilité transmis par le DME.
2. Valider l'authenticité et le schéma de la donnée.
3. Intégrer l'événement dans l'index central de RVSQ.
4. Journaliser l'opération pour traçabilité.

### 3.2 Flux alternatifs
- **Conflit détecté :** appliquer les règles de résolution définies.
- **Source indisponible :** appliquer un plan de reprise (backoff) et marquer l'horodatage de dernière synchronisation.

## 4. EXIGENCES SPÉCIALES
- **Performance :** propagation ≤ 5 secondes.
- **Disponibilité :** ≥ 99,9 %.
- **Journalisation :** détaillée et corrélée (CAR14).

## 5. PRÉCONDITIONS
- Connecteurs DME configurés.
- API alignées et authentifiées.
- RVSQ opérationnelle.

## 6. POSTCONDITIONS
- Index à jour et cohérent.
- Traçabilité assurée.

## 7. CARACTÉRISTIQUE ASSOCIÉE
CAR10 – Synchroniser les disponibilités en temps réel avec les cliniques
