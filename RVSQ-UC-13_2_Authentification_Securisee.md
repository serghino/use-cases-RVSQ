# RVSQ-UC-13.2 – Authentification sécurisée

## 1. BRÈVE DESCRIPTION
Le **Service d’authentification gouvernementale** assure la vérification de l’identité des citoyens et des utilisateurs accédant à la **Plateforme RVSQ**, en établissant une session sécurisée et traçable selon les protocoles en vigueur.

## 2. ACTEURS IMPLIQUÉS
- **Acteur principal :** Service d’authentification gouvernementale
- **Acteurs secondaires :** Plateforme RVSQ, Citoyen, Administrateur système

## 3. FLUX D’ÉVÉNEMENTS
### 3.1 Flux nominal
1. Le citoyen tente d’accéder à la plateforme RVSQ.
2. La plateforme redirige vers le service d’authentification gouvernementale (SAG).
3. Le SAG vérifie les identifiants (MFA/OTP si activé).
4. Une session sécurisée est établie et un jeton d’accès est émis.
5. Le résultat d’authentification est transmis à RVSQ.
6. Les accès sont journalisés et corrélés (CAR14).

### 3.2 Flux alternatifs
- **Échec d’authentification :** le SAG retourne une erreur et la session est refusée.
- **Jeton expiré :** demande de reconnexion et nouvelle validation MFA.

## 4. EXIGENCES SPÉCIALES
- **Protocoles :** OAuth2 / OpenID Connect avec chiffrement TLS 1.3.
- **Conformité :** Loi 25 et politiques de sécurité MSSS/RAMQ.
- **Traçabilité :** corrélation des sessions avec journaux RVSQ.

## 5. PRÉCONDITIONS
- Service d’authentification disponible.
- RVSQ configurée pour les redirections sécurisées.

## 6. POSTCONDITIONS
- Session active et sécurisée.
- Historique d’accès mis à jour.

## 7. CARACTÉRISTIQUE ASSOCIÉE
CAR13 – Authentification sécurisée et traçable entre systèmes.
