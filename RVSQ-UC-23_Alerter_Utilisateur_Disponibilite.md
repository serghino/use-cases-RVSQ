# RVSQ-UC-23 – Alerter l'utilisateur lors d'une disponibilité trouvée

## 1. BRÈVE DESCRIPTION
La **Plateforme RVSQ** alerte le **citoyen** lorsqu'une correspondance est détectée, via le canal préféré (SMS, courriel, notification mobile).

## 2. ACTEURS IMPLIQUÉS
- **Acteur principal :** Plateforme RVSQ
- **Acteurs secondaires :** Citoyen, Service de messagerie

## 3. FLUX D'ÉVÉNEMENTS
### 3.1 Flux nominal
1. Détecter un événement « correspondance trouvée ».
2. Identifier les préférences de notification.
3. Construire le message (contenu, lien de confirmation).
4. Sélectionner le canal optimal.
5. Envoyer le message.
6. Journaliser l'accusé.

### 3.2 Flux alternatifs
- **Canal préféré indisponible :** basculer vers un autre canal.
- **Politique anti-spam :** regrouper les envois.

## 4. EXIGENCES SPÉCIALES
- Délai d'envoi ≤ 30 secondes.
- Sécurité des messages (liens signés).
- Confirmation du statut d'envoi.

## 5. PRÉCONDITIONS
- Citoyen enregistré et préférences définies.

## 6. POSTCONDITIONS
- Citoyen alerté et lien de confirmation fonctionnel.

## 7. CARACTÉRISTIQUE ASSOCIÉE
CAR23 – Notifications instantanées (SMS, courriel, application mobile).
