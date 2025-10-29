# RVSQ-UC-13.3 – Vérification d'intégrité

## 1. BRÈVE DESCRIPTION
La **Plateforme RVSQ** valide systématiquement l'intégrité des messages reçus des systèmes externes (DME, service de messagerie) afin d'assurer la fiabilité et la non-altération des données.

## 2. ACTEURS IMPLIQUÉS
- **Acteur principal :** Plateforme RVSQ
- **Acteurs secondaires :** DME, Service de messagerie

## 3. FLUX D'ÉVÉNEMENTS
### 3.1 Flux nominal
1. Recevoir un message signé depuis un système externe.
2. Vérifier la signature numérique et l'empreinte **SHA-256**.
3. Comparer les horodatages et la source d'origine.
4. Accepter le message valide et consigner la vérification.

### 3.2 Flux alternatifs
- **A1 — Altération détectée :** rejet du message et alerte à l'administrateur.
- **A2 — Signature invalide :** tentative de revalidation automatique, sinon rejet.

## 4. EXIGENCES SPÉCIALES
- **Intégrité :** validation cryptographique systématique.
- **Traçabilité :** journaux d'intégrité archivés 12 mois.
- **Conformité :** Loi 25 + CAR13.

## 5. PRÉCONDITIONS
- Certificats de confiance enregistrés.
- Mécanisme de signature actif côté DME/messagerie.

## 6. POSTCONDITIONS
- Données validées et archivées.
- Alertes déclenchées en cas d'altération.

## 7. POINTS D'EXTENSION
- **UC133.D – Revalidation automatique :** exécutée uniquement lorsqu'une signature invalide est détectée.
- UC14 : Journalisation et analyse des anomalies.

## 8. CARACTÉRISTIQUE ASSOCIÉE
CAR13 – Vérification d'intégrité et traçabilité des échanges.

## 9. POINTS DE TRAÇABILITÉ
- CAR13 → UC13.3
- CAR14 → UC13.3
