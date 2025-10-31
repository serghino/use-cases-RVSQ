# RVSQ-UC-06 : S'authentifier via le Service d'Authentification Gouvernementale (SAG)

## BRÈVE DESCRIPTION
Ce cas d'utilisation décrit le processus d'authentification d'un **citoyen** sur la **plateforme RVSQ** via le **Service d'Authentification Gouvernementale (SAG)**.  
L'objectif est d'assurer une connexion **sécurisée**, **centralisée** et **traçable**, tout en garantissant la **confidentialité** et la **protection des données personnelles** conformément à la **Loi 25** et aux politiques du **MSSS/RAMQ**.

---

## FLUX D'ÉVÉNEMENTS

### Flux de Base

1. Le citoyen accède à la page de connexion de la **plateforme RVSQ**.
2. Le système redirige automatiquement vers le **Service d'Authentification Gouvernementale (SAG)**.
3. Le **SAG** affiche le formulaire d'identification officiel et demande :
    - un **identifiant unique** (ex. clicSÉQUR, RAMQ, etc.),
    - un **facteur secondaire d'authentification (MFA)**, si requis.
4. Le citoyen saisit ses informations d'authentification.
5. Le **SAG** valide les identifiants et applique les contrôles de sécurité :
    - Vérification de la validité du compte,
    - Validation du MFA (si applicable).
6. Si la validation réussit, le **SAG** émet un **jeton d'accès sécurisé** (OAuth2 / OpenID Connect).
7. La **plateforme RVSQ** reçoit ce jeton, vérifie sa signature et sa validité.
8. Le système crée une **session sécurisée** pour le citoyen et charge son espace personnel.
9. L'événement de connexion est **journalisé**.

---

### Flux Alternatifs

**4'. Identifiants incorrects**
- À l'étape 4, si les identifiants sont invalides :
    - Le **SAG** affiche un message d'erreur.
    - Aucune session n'est créée.
    - Le citoyen peut réessayer.

**5'. Échec MFA (authentification multifacteur)**
- À l'étape 5, si la vérification MFA échoue :
    - Le **SAG** interrompt le processus.
    - Le citoyen est invité à réessayer.
    - L'événement est journalisé comme tentative échouée.

**6'. Jeton expiré ou invalide**
- À l'étape 6, si le jeton est expiré ou non valide :
    - La **plateforme RVSQ** refuse l'accès.
    - Le citoyen est redirigé vers la page de connexion pour renouveler la session.

**7'. Erreur du service SAG**
- À l'étape 7, si le **SAG** est temporairement indisponible :
    - Le système affiche un message d'erreur technique.
    - Le citoyen est invité à réessayer ultérieurement.

**9'. Échec de journalisation**
- Si la journalisation échoue :
    - L'événement est stocké temporairement et répliqué dès reprise du service.

---

## PRÉ-CONDITIONS

1. Le **SAG** est disponible et fonctionnel.
2. La **plateforme RVSQ** est configurée pour la redirection et la validation des jetons OAuth2.
3. Le citoyen dispose d'un compte valide auprès du **SAG**.
4. La communication entre RVSQ et le SAG est chiffrée (**TLS 1.3**).

---

## POST-CONDITIONS

1. Le citoyen est **authentifié** et dispose d'une **session active**.
2. Le **jeton d'accès** est valide et lié à son identité.
3. L'événement d'authentification est **journalisé**.
4. Le citoyen peut accéder à ses rendez-vous et informations personnelles.

---

## CARACTÉRISTIQUES ASSOCIÉES

- **CAR11** – Intégration du Service d'authentification gouvernementale.
- **CAR13** – Sécurisation des échanges d'authentification.
- **CAR14** – Journalisation et traçabilité des connexions.

---

## POINTS DE TRAÇABILITÉ

- CAR11 → UC06
- CAR13 → UC06
- CAR14 → UC06
