# Matrice de Traçabilité – Plateforme RVSQ

## 1. Vue d'ensemble

Ce document établit la traçabilité bidirectionnelle entre :
- **23 caractéristiques** métier et techniques (**CAR01–CAR23**)
- **5 sections** du survol du modèle de cas d'utilisation
- **Cas d'utilisation** planifiés ou existants (**RVSQ-UC-XX**)

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
| **CAR08** | Gestion automatisée des annulations | | ⚫ | ◐ | | |
| **CAR09** | Notifications multi-canaux (courriel, SMS, appels) | | ◐ | ⚫ | | |
| **CAR10** | Synchronisation temps réel DME ↔ Plateforme | ◐ | ⚫ | ◐ | | |
| **CAR11** | ⚠️ Service authentification gouvernementale (= CAR04) | | | | ⚫ | |
| **CAR12** | MFA / OTP (authentification forte) | | | | ⚫ | |
| **CAR13** | Protocoles sécurisés (TLS 1.3, échange de données) | | | | ⚫ | |
| **CAR14** | Journalisation / traçabilité des accès | | | | ⚫ | |
| **CAR15** | Contrôles d'accès basés sur les rôles (RBAC) | | | | ⚫ | |
| **CAR16** | Audits & tests de conformité | | | | ⚫ | |
| **CAR17** | Mode invité (recherche sans compte) | ⚫ | | | ◐ | |
| **CAR18** | Transition vers authentification pour réserver | ⚫ | | | ◐ | |
| **CAR19** | Service de téléconsultation (vidéo/audio) | | | | | ⚫ |
| **CAR20** | Clavardage sécurisé | | | | ◐ | ⚫ |
| **CAR21** | Alertes contextuelles soins rapides | | ◐ | ◐ | | ⚫ |
| **CAR22** | Moteur de recherche automatisé en continu | ⚫ | | ◐ | | |
| **CAR23** | Notifications instantanées (SMS, courriel, mobile) | | | ⚫ | | |

---

### Notes clés

- **Doublon** : CAR04 et CAR11 → fusionner en une seule exigence *« Authentification gouvernementale unifiée »*.
- **Section 4** (*Sécurité & Profil*) est **transversale** : elle encadre toutes les opérations des autres sections.
- **Section 3** (*Notifications*) dépend fortement des événements générés par les Sections 1, 2 et 5.
- Les **CAR09 à CAR23** ont étendu la couverture aux domaines Notifications, Sécurité et Téléconsultation.

---

### Section 1 – Recherche de rendez-vous

**CAR couvertes** : CAR01, CAR02, CAR05, CAR06 (◐), CAR10 (◐), CAR17, CAR18, CAR22  
**UC principaux** : RVSQ-UC-01 (Rechercher un professionnel) • RVSQ-UC-02 (Filtrer les résultats) • RVSQ-UC-22 (Recherche automatisée continue)  
**Dépendances** :
- 🔗 Section 2 (disponibilités temps réel)
- 🔗 Section 4 (authentification progressive CAR17→CAR18)
- 🔗 Section 3 (notifications issues recherche continue CAR22)

---

### Section 2 – Gestion des disponibilités

**CAR couvertes** : CAR07, CAR08, CAR10  
**UC principaux** : RVSQ-UC-10.1 (Réception DME) • RVSQ-UC-10.2 (Publication MAJ)  
**Dépendances** :
- 🔗 Section 1 (consolidation pour recherche)
- 🔗 Section 3 (déclenchement de notifications d'annulation/nouveau créneau)
- 🔗 Section 4 (sécurité des accès DME, RBAC)

---

### Section 3 – Notifications

**CAR couvertes** : CAR03, CAR08 (◐), CAR09, CAR21 (◐), CAR22 (◐), CAR23  
**UC principaux** : RVSQ-UC-09.1 (Notifier citoyens) • RVSQ-UC-09.2 (Notifier cliniques) • RVSQ-UC-23 (Alerter utilisateur)  
**Dépendances** :
- 🔗 Section 1 (déclencheurs de recherche continue)
- 🔗 Section 2 (événements de disponibilités)
- 🔗 Section 4 (préférences utilisateur CAR06)
- 🔗 Section 5 (rappels de téléconsultation)

---

### Section 4 – Authentification, Sécurité & Profil

**CAR couvertes** : CAR04, CAR05 (◐), CAR06, CAR11 (⚠️ doublon), CAR12, CAR13, CAR14, CAR15, CAR16, CAR17 (◐), CAR18 (◐)  
**UC principaux** :
- RVSQ-UC-13.1 (Chiffrement échanges)
- RVSQ-UC-13.2 (Authentification sécurisée)
- RVSQ-UC-13.3 (Vérification d'intégrité)
- RVSQ-UC-14.1 (Journaliser accès)
- RVSQ-UC-14.2 (Analyser anomalies)  
  **Dépendances** : Section transversale – encadre toutes les autres

---

### Section 5 – Téléconsultation

**CAR couvertes** : CAR19, CAR20, CAR21  
**UC principaux** : RVSQ-UC-20 (Clavardage sécurisé) • RVSQ-UC-19 (Session téléconsultation)  
**Dépendances** :
- 🔗 Section 2 (créneaux dédiés téléconsultation)
- 🔗 Section 3 (rappels session virtuelle)
- 🔗 Section 4 (authentification forte, chiffrement)

---

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
        │Téléconsult. │
        └─────────────┘
```
