# RVSQ-UC-14.1 – Journaliser les accès

## 1. BRÈVE DESCRIPTION
La **Plateforme RVSQ** journalise de manière exhaustive tous les accès et opérations sensibles afin d'assurer la traçabilité et la conformité réglementaire (Loi 25, MSSS/RAMQ).  
Chaque événement est enregistré, signé et horodaté de manière immuable pour garantir son intégrité et sa valeur probante.

## 2. ACTEURS IMPLIQUÉS
- **Acteur principal :** Plateforme RVSQ
- **Acteurs secondaires :** Administrateur système, Auditeur

## 3. FLUX D'ÉVÉNEMENTS
### 3.1 Flux nominal
1. Détecter une action sensible initiée par un utilisateur ou un service.
2. Capturer les champs essentiels (**qui**, **quoi**, **quand**, **où**).
3. Stocker les informations dans un journal immuable et horodaté (**NTP synchronisé**).
4. Rendre le journal accessible aux auditeurs autorisés via une interface sécurisée.
5. Archiver automatiquement les entrées selon la politique de rétention MSSS/RAMQ.

### 3.2 Flux alternatifs
- **A1 — Stockage indisponible :** utilisation d'une file d'attente locale puis réplication dès reprise.
- **A2 — Extraction ou audit demandé :** accès limité selon les rôles **RBAC**.

## 4. EXIGENCES SPÉCIALES
- **Intégrité :** immutabilité, signatures et horodatage cryptographique.
- **Rétention :** conformité MSSS/RAMQ (12 à 24 mois).
- **Accès :** réservé aux auditeurs autorisés via authentification forte.
- **Conformité :** Loi 25, MSSS/RAMQ.

## 5. PRÉCONDITIONS
- Mécanismes de journalisation actifs.
- Rôles d'audit définis.
- Plateforme RVSQ opérationnelle.

## 6. POSTCONDITIONS
- Journaux complets, consultables et archivés.
- Piste d'audit disponible.
- Alertes automatiques en cas d'événement critique.

## 7. POINTS D'EXTENSION
- **UC141.D – Extraction des journaux :** déclenché uniquement lorsqu'un auditeur ou administrateur demande une exportation.
- **UC14.2 :** Analyse et corrélation des anomalies.

## 8. CARACTÉRISTIQUE ASSOCIÉE
CAR14 – Journaliser et tracer tous les accès.

## 9. POINTS DE TRAÇABILITÉ
- CAR14 → UC14.1
- CAR13 → UC14.1 (signature et chiffrement des journaux)
