# RVSQ-UC-14.2 – Analyser les anomalies

## 1. BRÈVE DESCRIPTION
L'**Auditeur** ou l'**Administrateur système** analyse les journaux produits par la **Plateforme RVSQ** pour détecter des événements anormaux et prévenir les abus.

## 2. ACTEURS IMPLIQUÉS
- **Acteur principal :** Auditeur / Administrateur système
- **Acteurs secondaires :** Plateforme RVSQ, MSSS/RAMQ (notification externe)

## 3. FLUX D'ÉVÉNEMENTS
### 3.1 Flux nominal
1. Agréger les journaux pertinents depuis les différentes sources.
2. Appliquer des règles de détection et seuils d'alerte.
3. Générer des rapports d'anomalies.
4. Notifier les parties prenantes (RVSQ, MSSS/RAMQ).

### 3.2 Flux alternatifs
- **Faux positif :** ajustement des règles et seuils.
- **Volume élevé :** échantillonnage ou priorisation automatique.

## 4. EXIGENCES SPÉCIALES
- **Corrélation :** multi-sources et temps réel.
- **Tableaux de bord :** dédiés à la supervision et l'audit.
- **Conservation :** des preuves 12 mois minimum.

## 5. PRÉCONDITIONS
- Journaux disponibles et intègres.
- Rôles d'audit configurés.
- Outils d'analyse opérationnels.

## 6. POSTCONDITIONS
- Anomalies détectées et tracées.
- Alertes envoyées.
- Rapports archivés.

## 7. CARACTÉRISTIQUE ASSOCIÉE
CAR14 – Journaliser et tracer tous les accès
