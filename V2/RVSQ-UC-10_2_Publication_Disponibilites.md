# RVSQ-UC-10.2 – Publication des mises à jour de disponibilités

## 1. BRÈVE DESCRIPTION
La **Plateforme RVSQ** publie en temps réel les disponibilités mises à jour afin qu'elles soient immédiatement visibles pour les citoyens et les professionnels de santé sur les interfaces de recherche et de gestion.  
Ce processus assure la cohérence entre l'index central, les caches et les vues consultées par les utilisateurs.

## 2. ACTEURS IMPLIQUÉS
- **Acteur principal :** Plateforme RVSQ
- **Acteurs secondaires :** Citoyen, Médecin

## 3. FLUX D'ÉVÉNEMENTS
### 3.1 Flux nominal
1. Détecter une modification validée dans l'index central (ex. nouveau créneau, annulation, mise à jour).
2. Mettre à jour les caches distribués et les vues de recherche.
3. Exposer les créneaux actualisés dans les interfaces du citoyen et du professionnel.
4. Journaliser la publication pour assurer la traçabilité et la supervision (CAR14).

### 3.2 Flux alternatifs
- **A1 — Cache indisponible :** basculer automatiquement en lecture directe de l'index principal (*mode dégradé*) ; journaliser la dégradation.
- **A2 — Latence excessive :** générer une alerte d'observabilité (CAR14) et notifier l'administrateur.
- **A3 — Erreur de cohérence détectée :** exclure temporairement la mise à jour et déclencher un recalcul différé (UC102.D).

## 4. EXIGENCES SPÉCIALES
- **Rafraîchissement :** propagation quasi temps réel (<2 secondes).
- **Observabilité :** exposition de métriques de latence, taux d'erreur et volume de mises à jour.
- **Cohérence :** forte lors de la réservation (synchronisation immédiate avec UC10.1).
- **Résilience :** basculement automatique en lecture directe en cas d'indisponibilité du cache.

## 5. PRÉCONDITIONS
- L'index central est à jour et validé.
- Les services de cache et de recherche sont opérationnels.

## 6. POSTCONDITIONS
- Les disponibilités actualisées sont visibles par les citoyens et les professionnels.
- Les opérations sont journalisées et corrélées à un identifiant d'événement.

## 7. POINTS D'EXTENSION
- **UC102.D – Recalcul différé :** exécuté uniquement lorsqu'une incohérence ou un échec de cache est détecté.
- UC14 : Journalisation et suivi d'anomalies.
- UC21 : Alerte contextuelle de soins rapides (notification déclenchée après mise à jour).

## 8. CARACTÉRISTIQUES CORRESPONDANTES
CAR10 – Synchroniser les disponibilités en temps réel avec les cliniques.  
CAR14 – Journalisation et traçabilité des mises à jour.

## 9. POINTS DE TRAÇABILITÉ
- CAR10 → UC10.2
- CAR14 → UC10.2
