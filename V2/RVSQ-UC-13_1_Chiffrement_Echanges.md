# RVSQ-UC-13.1 – Chiffrement des échanges

## 1. BRÈVE DESCRIPTION
L'**Administrateur système** configure et maintient le chiffrement des communications entre la **Plateforme RVSQ** et les systèmes externes (DME, Service d'authentification gouvernementale) afin d'assurer la **confidentialité**, **l'intégrité** et la **conformité** des données échangées.

## 2. ACTEURS IMPLIQUÉS
- **Acteur principal :** Administrateur système
- **Acteurs secondaires :** Plateforme RVSQ, DME, Service d'authentification gouvernementale

## 3. FLUX D'ÉVÉNEMENTS
### 3.1 Flux nominal
1. Configurer le protocole **TLS 1.3** et activer la **Perfect Forward Secrecy (PFS)**.
2. Activer **HSTS** sur les interfaces Web de la Plateforme RVSQ.
3. Tester la conformité avec les exigences du **MSSS/RAMQ**.
4. Vérifier la compatibilité avec les connecteurs **DME** et le **SAG**.
5. Journaliser les résultats de test et valider la configuration.

### 3.2 Flux alternatifs
- **A1 — Erreur de configuration TLS :** déclenchement de l'extension **UC131.E – Blocage connexion non conforme** (la plateforme bloque temporairement les connexions et alerte l'administrateur).
- **A2 — Certificat expiré :** déclenchement de l'extension **UC131.E – Renouvellement de certificat** (renouvellement automatique et journalisation).
- **A3 — Non-conformité MSSS/RAMQ détectée :** blocage et notification immédiate à l'administrateur système.

## 4. EXIGENCES SPÉCIALES
- **Sécurité :** TLS 1.3 + PFS obligatoire.
- **Traçabilité :** logs signés et horodatés.
- **Conformité :** respect des standards **MSSS/RAMQ** et de la **Loi 25**.

## 5. PRÉCONDITIONS
- Accès administrateur autorisé.
- Services externes intégrés et authentifiés.

## 6. POSTCONDITIONS
- Toutes les communications **RVSQ ↔ Systèmes externes** sont chiffrées et validées.
- Les résultats de vérification sont journalisés.

## 7. POINTS D'EXTENSION
- **UC131.E – Blocage connexion non conforme / Renouvellement certificat :** exécuté uniquement lors d'une erreur TLS, d'un certificat expiré ou d'une non-conformité détectée.
- **UC14.1 :** Journalisation des évènements de sécurité liés aux connexions rejetées.

## 8. CARACTÉRISTIQUE ASSOCIÉE
CAR13 – Protocoles sécurisés pour l'échange de données.

## 9. POINTS DE TRAÇABILITÉ
- CAR13 → UC13.1
- CAR14 → UC13.1
