# RVSQ-UC-13.3 – Vérification d’intégrité

## 1. BRÈVE DESCRIPTION
La **Plateforme RVSQ** garantit l’intégrité des messages échangés avec les systèmes externes (DME, service de messagerie) en validant les signatures, empreintes et horodatages afin de prévenir toute altération des données.

## 2. ACTEURS IMPLIQUÉS
- **Acteur principal :** Plateforme RVSQ
- **Acteurs secondaires :** DME, Service de messagerie

## 3. FLUX D’ÉVÉNEMENTS
### 3.1 Flux nominal
1. Recevoir un message signé depuis un système externe.
2. Vérifier la signature numérique et l’empreinte SHA256.
3. Comparer les horodatages et la source d’origine.
4. Accepter le message s’il est valide et consigner la vérification.

### 3.2 Flux alternatifs
- **Altération détectée :** rejet du message et notification à l’administrateur.
- **Signature invalide :** tentative de revalidation ou rejet.

## 4. EXIGENCES SPÉCIALES
- **Intégrité :** validation cryptographique systématique.
- **Traçabilité :** logs d’intégrité archivés 12 mois.
- **Conformité :** alignement avec CAR13 et Loi 25.

## 5. PRÉCONDITIONS
- Certificats de confiance enregistrés.
- Mécanisme de signature actif côté DME et messagerie.

## 6. POSTCONDITIONS
- Données validées et sécurisées.
- Alertes émises en cas d’altération.

## 7. CARACTÉRISTIQUE ASSOCIÉE
CAR13 – Vérification d’intégrité et traçabilité des échanges.
