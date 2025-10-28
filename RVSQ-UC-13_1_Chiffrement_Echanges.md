# RVSQ-UC-13.1 – Chiffrement des échanges

## 1. BRÈVE DESCRIPTION
L'**Administrateur système** configure et maintient le chiffrement des communications entre la **Plateforme RVSQ** et les systèmes externes (DME, service d'authentification gouvernementale) afin d'assurer la confidentialité et l'intégrité des données échangées.

## 2. ACTEURS IMPLIQUÉS
- **Acteur principal :** Administrateur système
- **Acteurs secondaires :** Plateforme RVSQ, DME, Service d'authentification gouvernementale

## 3. FLUX D'ÉVÉNEMENTS
### 3.1 Flux nominal
1. Configurer le protocole TLS 1.3 et activer la Perfect Forward Secrecy (PFS).
2. Activer HSTS sur les interfaces Web de la plateforme RVSQ.
3. Tester la conformité avec les exigences du MSSS/RAMQ.
4. Vérifier la compatibilité avec les connecteurs DME.
5. Journaliser les résultats de test et valider la configuration.

### 3.2 Flux alternatifs
- **Erreur de configuration TLS :** la plateforme bloque les connexions non conformes et notifie l'administrateur.
- **Certificat expiré :** alerte automatique et renouvellement programmé.

## 4. EXIGENCES SPÉCIALES
- **Sécurité :** TLS 1.3 + PFS obligatoire.
- **Traçabilité :** logs signés et horodatés.
- **Conformité :** respect des standards MSSS/RAMQ et Loi 25.

## 5. PRÉCONDITIONS
- Accès administrateur autorisé.
- Services externes intégrés.

## 6. POSTCONDITIONS
- Toutes les communications RVSQ ↔ systèmes externes sont chiffrées et vérifiées.

## 7. CARACTÉRISTIQUE ASSOCIÉE
CAR13 – Protocoles sécurisés pour l'échange de données.
