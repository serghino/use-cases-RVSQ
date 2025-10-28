# RVSQ-UC-23 – Alerter l'utilisateur lors d'une disponibilité trouvée

## 1. BRÈVE DESCRIPTION
La **Plateforme RVSQ** alerte le **Citoyen** dès qu'une correspondance de créneau est détectée par le moteur de recherche automatisé (UC22).  
L'alerte est transmise via le canal de communication préféré du citoyen (**SMS**, **courriel** ou **notification mobile**) dans un délai inférieur à 30 secondes.

## 2. ACTEURS IMPLIQUÉS
- **Acteur principal :** Plateforme RVSQ
- **Acteurs secondaires :** Citoyen, Service de messagerie

## 3. FLUX D'ÉVÉNEMENTS
### 3.1 Flux nominal
1. Détecter un **événement “correspondance trouvée”** transmis par le moteur UC22.
2. Identifier les **préférences de notification** du citoyen.
3. Construire le **message** (contenu, lien de confirmation, contexte).
4. Sélectionner le **canal optimal** (SMS, courriel, notification mobile).
5. Envoyer le message via le **service de messagerie**.
6. Recevoir et **journaliser l'accusé d'envoi**.

### 3.2 Flux alternatifs
- **A1 — Canal préféré indisponible :** déclenchement de l'extension **UC23.E – Fallback de canal** (bascule vers le canal secondaire configuré).
- **A2 — Politique anti-spam active :** déclenchement de l'extension **UC23.E – Regroupement des notifications** (les envois multiples sont regroupés en un seul message).

## 4. EXIGENCES SPÉCIALES
- **Performance :** délai d'envoi ≤ 30 secondes après détection.
- **Sécurité :** liens de confirmation signés numériquement.
- **Disponibilité :** 24 h/24, 7 j/7.
- **Traçabilité :** journalisation complète des tentatives d'envoi.
- **Conformité :** Loi 25 (protection des renseignements personnels).

## 5. PRÉCONDITIONS
- Citoyen enregistré et préférences de notification configurées.
- Service de messagerie opérationnel.

## 6. POSTCONDITIONS
- Citoyen alerté avec succès via un canal valide.
- Journal d'envoi mis à jour et corrélé à UC22.

## 7. POINTS D'EXTENSION
- **UC23.E – Fallback de canal :** exécuté uniquement lorsque le canal préféré est indisponible.
- **UC23.E – Regroupement des notifications :** exécuté lorsque la politique anti-spam est active.
- **UC14.1 :** journalisation des envois (CAR14).

## 8. CARACTÉRISTIQUE ASSOCIÉE
CAR23 – Notifications instantanées (SMS, courriel, application mobile).

## 9. POINTS DE TRAÇABILITÉ
- CAR23 → UC23
- CAR09 → UC23 (multi-canaux de notification)
- CAR14 → UC23 (journalisation et conformité)
