# RVSQ-UC-14.1 – Journaliser les accès

## 1. BRÈVE DESCRIPTION
La **Plateforme RVSQ** journalise de manière exhaustive tous les accès et opérations sensibles afin d'assurer la traçabilité et la conformité réglementaire.

## 2. ACTEURS IMPLIQUÉS
- **Acteur principal :** Plateforme RVSQ
- **Acteurs secondaires :** Administrateur système, Auditeur

## 3. FLUX D'ÉVÉNEMENTS
### 3.1 Flux nominal
1. Détecter une action sensible initiée par un utilisateur ou un service.
2. Capturer les champs essentiels (qui, quoi, quand, où).
3. Stocker les informations dans un journal immuable et horodaté (NTP).
4. Rendre le journal accessible aux auditeurs autorisés.

### 3.2 Flux alternatifs
- **Stockage indisponible :** file d'attente locale, puis réplication dès reprise.
- **Demande d'extraction :** accès restreint selon les rôles RBAC.

## 4. EXIGENCES SPÉCIALES
- **Intégrité :** immutabilité, signatures, horodatage.
- **Rétention :** conformité MSSS/RAMQ.
- **Accès :** réservé aux auditeurs.

## 5. PRÉCONDITIONS
- Mécanismes de journalisation actifs.
- Rôles d'audit définis.
- RVSQ opérationnelle.

## 6. POSTCONDITIONS
- Journaux complets et consultables.
- Piste d'audit disponible.
- Alertes générées en cas d'événement critique.

## 7. CARACTÉRISTIQUE ASSOCIÉE
CAR14 – Journaliser et tracer tous les accès
