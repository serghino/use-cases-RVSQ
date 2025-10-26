# Matrice de Traçabilité – Plateforme RVSQ

## 1. Vue d'ensemble

Ce document établit la traçabilité bidirectionnelle entre :
- **23 caractéristiques** métier et techniques (CAR01–CAR23)
- **5 sections** du survol du modèle de cas d'utilisation
- **Cas d'utilisation** planifiés ou existants (RVSQ-UC-XX)

---

## 2. Légende

| Symbole | Signification |
|---------|---------------|
| ⚫ | Relation principale (la caractéristique est au cœur de cette section/UC) |
| ◐ | Relation secondaire/contributive (la caractéristique impacte partiellement) |
| ⚠️ | Doublon identifié (à fusionner) |
| 🔗 | Dépendance forte avec autre section/CAR |

---

## 3. Matrice CAR × Sections du Survol

| CAR | Description | Section 1<br>Recherche | Section 2<br>Disponibilités | Section 3<br>Notifications | Section 4<br>Sécurité & Profil | Section 5<br>Télécons. |
|-----|-------------|:---:|:---:|:---:|:---:|:---:|
| **CAR01** | Moteur de recherche centralisé et optimisé | ⚫ | ◐ | | | |
| **CAR02** | Filtres avancés (spécialité, langue, localisation) | ⚫ | | | | |
| **CAR03** | Confirmation et rappels automatiques | | | ⚫ | | |
| **CAR04** | Connexion via authentification gouvernementale | | | | ⚫ | |
| **CAR05** | Autocomplétion sécurisée | ⚫ | | | ◐ | |
| **CAR06** | Sauvegarde préférences (médecin, clinique, langue, notifs) | ◐ | | ◐ | ⚫ | |
| **CAR07** | Intégration DME pour publier disponibilités | | ⚫ | | ◐ | |
| **CAR08** | Gestion automatisée annulations | | ⚫ | ◐ | | |
| **CAR09** | Notifications multi-canaux (courriel, SMS, appels) | | | ⚫ | | |
| **CAR10** | Synchronisation temps réel disponibilités | ◐ | ⚫ | | | |
| **CAR11** | ⚠️ Service authentification gouvernementale (= CAR04) | | | | ⚫ | |
| **CAR12** | MFA / OTP | | | | ⚫ | |
| **CAR13** | Protocoles sécurisés (transport & échange) | | | | ⚫ | |
| **CAR14** | Journalisation / traçabilité accès | | | | ⚫ | |
| **CAR15** | Contrôles d'accès basés rôles (RBAC) | | | | ⚫ | |
| **CAR16** | Audits & tests conformité | | | | ⚫ | |
| **CAR17** | Mode invité (recherche sans compte) | ⚫ | | | ◐ | |
| **CAR18** | Transition authentification pour réserver | ⚫ | | | ◐ | |
| **CAR19** | Service téléconsultation (vidéo/audio) | | | | | ⚫ |
| **CAR20** | Clavardage sécurisé | | | | ◐ | ⚫ |
| **CAR21** | Alertes contextuelles soins rapides | | ◐ | ◐ | | ⚫ |
| **CAR22** | Moteur recherche automatisé continu | ⚫ | | ◐ | | |
| **CAR23** | Notifications instantanées (SMS, courriel, mobile) | | | ⚫ | | |

### Notes clés

- **Doublon** : CAR04 et CAR11 → **Action** : Fusionner en une seule exigence « Authentification gouvernementale unifiée ».
- **Section 4** (Sécurité & Profil) est transversale : elle encadre toutes les opérations des autres sections.
- **Section 3** (Notifications) dépend fortement des événements générés par Sections 1, 2 et 5.

---

### Section 1 – Recherche de rendez-vous

**CAR couvertes** : CAR01, CAR02, CAR05, CAR06 (◐), CAR10 (◐), CAR17, CAR18, CAR22  
**UC principaux** : RVSQ-UC-01  
**Dépendances** :
- 🔗 Section 2 (disponibilités temps réel)
- 🔗 Section 4 (authentification progressive CAR17→CAR18)
- 🔗 Section 3 (notifications issues recherche continue CAR22)

---

### Section 2 – Gestion des disponibilités

**CAR couvertes** : CAR07, CAR08, CAR10  
**UC principaux** : RVSQ-UC-03 (à créer)  
**Dépendances** :
- 🔗 Section 1 (consolidation pour recherche)
- 🔗 Section 3 (déclenchement notifications annulation/nouveau créneau)
- 🔗 Section 4 (sécurité accès DME, RBAC)

---

### Section 3 – Notifications

**CAR couvertes** : CAR03, CAR08 (◐), CAR09, CAR21 (◐), CAR22 (◐), CAR23  
**UC principaux** : RVSQ-UC-04 (à créer)  
**Dépendances** :
- 🔗 Section 1 (déclencheurs recherche continue)
- 🔗 Section 2 (événements disponibilités)
- 🔗 Section 4 (préférences utilisateur CAR06)
- 🔗 Section 5 (rappels téléconsultation)

---

### Section 4 – Authentification, Sécurité & Profil

**CAR couvertes** : CAR04, CAR05 (◐), CAR06, CAR11 (⚠️ doublon), CAR12, CAR13, CAR14, CAR15, CAR16, CAR17 (◐), CAR18 (◐)  
**UC principaux** : RVSQ-UC-05 (à créer)  
**Dépendances** : Section transversale – encadre toutes les autres

---

### Section 5 – Téléconsultation

**CAR couvertes** : CAR19, CAR20, CAR21  
**UC principaux** : RVSQ-UC-06 (à créer)  
**Dépendances** :
- 🔗 Section 2 (créneaux dédiés téléconsultation)
- 🔗 Section 3 (rappels session virtuelle)
- 🔗 Section 4 (authentification forte, chiffrement)


## 7. Dépendances Inter-Sections (Graphe)

```
┌─────────────┐
│  Section 1  │──┐
│  Recherche  │  │
└─────────────┘  │
       │         │
       ↓         ↓
┌─────────────┐  ┌─────────────┐
│  Section 2  │→ │  Section 3  │
│Disponibilités│  │Notifications│
└─────────────┘  └─────────────┘
       ↑               ↑
       │               │
       └───────┬───────┘
               │
        ┌─────────────┐
        │  Section 4  │ (Transversale)
        │Sécurité/ID  │
        └─────────────┘
               ↑
               │
        ┌─────────────┐
        │  Section 5  │
        │  Télécons.  │
        └─────────────┘
```