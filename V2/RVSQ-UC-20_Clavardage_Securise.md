# RVSQ-UC-20 – Clavardage sécurisé

## 1. BRÈVE DESCRIPTION
Le **Citoyen** et le **Professionnel de santé** échangent via un canal de **clavardage sécurisé** géré par la **Plateforme RVSQ**.  
Les communications sont **chiffrées**, **supervisées** et **journalisées** conformément aux exigences de confidentialité et de traçabilité du **MSSS/RAMQ** et de la **Loi 25**.

## 2. ACTEURS IMPLIQUÉS
- **Acteurs principaux :** Citoyen, Professionnel de santé
- **Acteurs secondaires :** Plateforme RVSQ, Service de messagerie sécurisé

## 3. FLUX D'ÉVÉNEMENTS
### 3.1 Flux nominal
1. Le **Citoyen** initie une session de clavardage.
2. Le **Professionnel de santé** est notifié et accepte la session.
3. La **Plateforme RVSQ** authentifie les participants.
4. Le canal chiffré est établi (**TLS 1.3 + PFS**).
5. Les messages sont échangés et journalisés (métadonnées uniquement).
6. La session est clôturée ou archivée à la fin de l'échange.

### 3.2 Flux alternatifs
- **A1 — Déconnexion d'un participant :** déclenchement de l'extension **UC20.E – Reconnexion sécurisée** (pause temporaire de la session, reprise après authentification).
- **A2 — Contenu inapproprié détecté :** déclenchement de l'extension **UC20.E – Clôture automatique et rapport de modération** (la session est fermée et un rapport est transmis à l'administrateur).

## 4. EXIGENCES SPÉCIALES
- **Chiffrement de bout en bout :** clés éphémères, renouvelées à chaque session.
- **Rétention :** conforme à la **Loi 25** – seules les métadonnées sont conservées.
- **Notifications :** en temps réel via le **service de messagerie sécurisé**.
- **Traçabilité :** journalisation des connexions, déconnexions et actions système.

## 5. PRÉCONDITIONS
- Identités vérifiées et authentifiées.
- Application mobile ou Web disponible.
- Service de messagerie opérationnel.

## 6. POSTCONDITIONS
- Session sécurisée terminée, archivée ou clôturée pour cause de modération.
- Journal d'audit mis à jour.

## 7. POINTS D'EXTENSION
- **UC20.E – Reconnexion sécurisée :** exécuté uniquement lors d'une déconnexion non volontaire.
- **UC20.E – Clôture automatique et rapport de modération :** exécuté uniquement lors d'un contenu inapproprié ou non conforme.
- **UC14.1 :** journalisation des événements de session.

## 8. CARACTÉRISTIQUE ASSOCIÉE
CAR20 – Clavardage sécurisé avec un professionnel de santé.

## 9. POINTS DE TRAÇABILITÉ
- CAR20 → UC20
- CAR13 → UC20 (chiffrement et intégrité des échanges)
- CAR14 → UC20 (traçabilité et journalisation)
