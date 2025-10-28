# RVSQ-UC-10.2 – Publication des mises à jour de disponibilités

## 1. BRÈVE DESCRIPTION
La **Plateforme RVSQ** publie les disponibilités mises à jour afin qu'elles soient immédiatement visibles pour les citoyens et les professionnels de santé sur l'interface de recherche.

## 2. ACTEURS IMPLIQUÉS
- **Acteur principal :** Plateforme RVSQ
- **Acteurs secondaires :** Citoyen, Médecin

## 3. FLUX D'ÉVÉNEMENTS
### 3.1 Flux nominal
1. Détecter une modification validée dans l'index central.
2. Mettre à jour les caches et vues de recherche.
3. Exposer les créneaux actualisés sur l'interface.
4. Journaliser la publication.

### 3.2 Flux alternatifs
- **Cache indisponible :** basculer en lecture directe avec dégradation maîtrisée.
- **Latence excessive :** générer une alerte d'observabilité.

## 4. EXIGENCES SPÉCIALES
- **Rafraîchissement :** quasi temps réel.
- **Observabilité :** métriques de latence/erreur.
- **Cohérence :** forte lors de la réservation.

## 5. PRÉCONDITIONS
- Index central à jour.
- Infrastructure de cache opérationnelle.

## 6. POSTCONDITIONS
- Disponibilités visibles immédiatement.
- Piste d'audit complète.

## 7. CARACTÉRISTIQUE ASSOCIÉE
CAR10 – Synchroniser les disponibilités en temps réel avec les cliniques
