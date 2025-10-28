# RVSQ-UC-20 – Clavardage sécurisé

## 1. BRÈVE DESCRIPTION
Le **Citoyen** et le **Professionnel de santé** échangent via un canal de clavardage sécurisé géré par la **Plateforme RVSQ**. Les communications sont chiffrées, supervisées et journalisées conformément aux exigences de confidentialité.

## 2. ACTEURS IMPLIQUÉS
- **Acteurs principaux :** Citoyen, Professionnel de santé
- **Acteurs secondaires :** Plateforme RVSQ, Service de messagerie sécurisé

## 3. FLUX D'ÉVÉNEMENTS
### 3.1 Flux nominal
1. Le citoyen initie une session de clavardage.
2. Le professionnel de santé est notifié et accepte la session.
3. La plateforme RVSQ authentifie les participants.
4. Le canal chiffré est établi (TLS 1.3 + PFS).
5. Les messages sont échangés et journalisés (métadonnées uniquement).

### 3.2 Flux alternatifs
- **Déconnexion d'un participant :** la session est mise en pause.
- **Contenu inapproprié :** modération automatique et clôture.

## 4. EXIGENCES SPÉCIALES
- Chiffrement de bout en bout.
- Rétention conforme à la Loi 25.
- Notifications en temps réel.

## 5. PRÉCONDITIONS
- Identités vérifiées.
- Application mobile ou web disponible.

## 6. POSTCONDITIONS
- Session sécurisée terminée ou archivée.

## 7. CARACTÉRISTIQUE ASSOCIÉE
CAR20 – Clavardage sécurisé avec un professionnel de santé.
