# RVSQ-UC-13.2 – Authentification sécurisée

## 1. BRÈVE DESCRIPTION
Le **Service d'authentification gouvernementale (SAG)** valide l'identité des utilisateurs (citoyens, administrateurs) souhaitant accéder à la **Plateforme RVSQ**.  
Il assure une session **sécurisée, traçable et conforme** aux exigences du MSSS/RAMQ.

## 2. ACTEURS IMPLIQUÉS
- **Acteur principal :** Service d'authentification gouvernementale
- **Acteurs secondaires :** Plateforme RVSQ, Citoyen, Administrateur système

## 3. FLUX D'ÉVÉNEMENTS
### 3.1 Flux nominal
1. Le citoyen accède à la plateforme RVSQ.
2. La plateforme redirige vers le **SAG**.
3. Le SAG vérifie les identifiants (MFA/OTP si activé).
4. Une session sécurisée est créée et un jeton d'accès est émis.
5. Le résultat est renvoyé à RVSQ.
6. Les accès sont journalisés (**CAR14**).

### 3.2 Flux alternatifs
- **A1 — Échec d'authentification :** retour d'erreur et blocage de session.
- **A2 — Jeton expiré :** déclenchement de l'extension **UC132.D – Revalidation MFA** (nouvelle vérification d'identité).
- **A3 — Changement d'appareil :** revalidation obligatoire via MFA avant établissement d'une nouvelle session.

## 4. EXIGENCES SPÉCIALES
- **Protocoles :** OAuth2 / OpenID Connect sous TLS 1.3.
- **Conformité :** Loi 25, politiques **MSSS/RAMQ**.
- **Traçabilité :** corrélation sessions ↔ journaux RVSQ.

## 5. PRÉCONDITIONS
- Service d'authentification disponible.
- Plateforme RVSQ configurée pour redirection sécurisée.

## 6. POSTCONDITIONS
- Session active et sécurisée.
- Historique d'accès mis à jour.

## 7. POINTS D'EXTENSION
- **UC132.D – Revalidation MFA / Jeton expiré :** exécuté uniquement lors de l'expiration du jeton ou d'un changement d'appareil.
- **UC14.1 :** Journalisation des tentatives échouées et anomalies d'accès.

## 8. CARACTÉRISTIQUE ASSOCIÉE
CAR13 – Authentification sécurisée et traçable entre systèmes.

## 9. POINTS DE TRAÇABILITÉ
- CAR13 → UC13.2
- CAR14 → UC13.2
