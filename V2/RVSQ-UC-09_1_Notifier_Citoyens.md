# RVSQ-UC-09.1 – Notifier les citoyens

## 1. BRÈVE DESCRIPTION
La **Plateforme RVSQ** envoie automatiquement des notifications multi-canaux (courriel, SMS, notification mobile) aux **citoyens éligibles** lorsqu'un événement se produit dans le système, tel qu'un **créneau libéré, une confirmation ou une annulation**.  
Ce mécanisme garantit que les citoyens sont informés en temps réel des changements relatifs à leurs rendez-vous médicaux.

## 2. ACTEURS IMPLIQUÉS
- **Acteur principal :** Plateforme RVSQ
- **Acteurs secondaires :** DME, Service de messagerie, Citoyen

## 3. FLUX D'ÉVÉNEMENTS
### 3.1 Flux nominal
1. Détecter un événement déclencheur (créneau libéré, annulation ou confirmation).
2. Identifier les citoyens concernés en fonction de leurs préférences enregistrées.
3. Construire dynamiquement le message à transmettre (contenu, langue, lien d'action).
4. Sélectionner le canal optimal (courriel, SMS, notification mobile) selon les préférences utilisateur.
5. Envoyer la notification via le **service de messagerie sécurisé**.
6. Recevoir le statut d'envoi et journaliser les informations pertinentes (date, canal, statut).

### 3.2 Flux alternatifs
- **A1 — Service de messagerie indisponible :** appliquer une stratégie de *backoff exponentiel* ; si l'échec persiste, journalisation (CAR14) et envoi d'une alerte administrateur.
- **A2 — Aucune préférence utilisateur définie :** effectuer un envoi par défaut via **courriel**.
- **A3 — DME non accessible :** reporter la notification et générer un message d'erreur interne.

## 4. EXIGENCES SPÉCIALES
- **Sécurité :** Communication via **TLS 1.3** avec **Perfect Forward Secrecy (PFS)** ; chiffrement du contenu (CAR13).
- **Traçabilité :** Journalisation complète des événements et des canaux utilisés (CAR14).
- **Disponibilité :** Service disponible **24 h/24, 7 j/7**.
- **Conformité :** Respect de la **Loi 25** sur la protection des renseignements personnels.
- **Performance :** Notification envoyée en moins de **30 secondes** après détection d'un événement.

## 5. PRÉCONDITIONS
- Les préférences de notification du citoyen sont configurées et valides.
- Les services DME et de messagerie sont accessibles.
- L'événement déclencheur (libération de créneau, confirmation, annulation) a été enregistré.

## 6. POSTCONDITIONS
- Les notifications ont été transmises avec succès ou consignées en cas d'échec.
- Un journal d'envoi complet est archivé.
- Les citoyens reçoivent les mises à jour selon leurs canaux préférés.

## 7. POINTS D'EXTENSION
- **UC091.D – Sélectionner canal :** exécuté uniquement si plusieurs canaux sont configurés dans les préférences du citoyen.
- **UC23 :** Notifications instantanées.
- Extension possible vers les **applications mobiles RVSQ** pour prise en charge des *push notifications*.

## 8. CARACTÉRISTIQUES CORRESPONDANTES
CAR09 – Notifications multi-canaux  
CAR13 – Sécurisation des échanges  
CAR14 – Journalisation et traçabilité des accès

## 9. POINTS DE TRAÇABILITÉ
- CAR09 → UC09.1
- CAR13 → UC13.1 (chiffrement des échanges)
- CAR14 → UC14.1 (journalisation des accès)
