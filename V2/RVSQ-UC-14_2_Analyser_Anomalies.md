# RVSQ-UC-14.2 – Analyser les anomalies

## 1. BRÈVE DESCRIPTION
L'**Auditeur** ou l'**Administrateur système** analyse les journaux produits par la **Plateforme RVSQ** afin de détecter des événements anormaux, corréler les incidents et prévenir les abus.  
L'objectif est d'assurer une surveillance proactive de la sécurité, la conformité et la disponibilité de la plateforme.

## 2. ACTEURS IMPLIQUÉS
- **Acteur principal :** Auditeur
- **Acteurs secondaires :** Administrateur système, Plateforme RVSQ, MSSS/RAMQ

## 3. FLUX D'ÉVÉNEMENTS
### 3.1 Flux nominal
1. Agréger les journaux pertinents provenant des différents modules (authentification, DME, notifications).
2. Appliquer des règles de détection et des seuils d'alerte préconfigurés.
3. Corréler les événements entre systèmes (RVSQ, DME, SAG).
4. Générer des rapports d'anomalies avec niveau de criticité.
5. Notifier les parties prenantes internes et externes (Administrateur, MSSS/RAMQ).
6. Archiver les rapports et les résultats de corrélation.

### 3.2 Flux alternatifs
- **A1 — Faux positifs :** ajustement des règles et recalibrage automatique.
- **A2 — Volume élevé :** déclenchement d'une extension **UC142.E – Traitement différé** (échantillonnage ou priorisation automatique).
- **A3 — Anomalie critique :** déclenchement de l'extension **UC142.E – Protocole d'alerte renforcé** (alerte immédiate et isolement du service concerné).

## 4. EXIGENCES SPÉCIALES
- **Corrélation :** multi-sources et en temps réel.
- **Visualisation :** tableaux de bord de supervision dédiés.
- **Conservation :** des preuves et journaux pendant 12 mois minimum.
- **Conformité :** respect de la **Loi 25** et des normes **MSSS/RAMQ**.

## 5. PRÉCONDITIONS
- Journaux disponibles et intègres.
- Rôles d'audit et de supervision configurés.
- Outils d'analyse et d'observabilité actifs.

## 6. POSTCONDITIONS
- Anomalies détectées, tracées et notifiées.
- Rapports consolidés et archivés.
- Alertes transmises aux entités concernées.

## 7. POINTS D'EXTENSION
- **UC142.D – Traitement différé :** exécuté uniquement lors d'un volume de données trop élevé.
- **UC142.E – Protocole d'alerte renforcé :** exécuté uniquement lors d'une anomalie critique.
- **UC14.1 :** Source principale des journaux audités.

## 8. CARACTÉRISTIQUE ASSOCIÉE
CAR14 – Journaliser et tracer tous les accès.

## 9. POINTS DE TRAÇABILITÉ
- CAR14 → UC14.2
- CAR13 → UC14.2 (intégrité et chiffrement des journaux)
