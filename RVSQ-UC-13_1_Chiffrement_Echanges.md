RVSQ-UC-13.1 : Chiffrement des échanges

## BRÈVE DESCRIPTION
Garantir le chiffrement en transit des communications entre RVSQ et les systèmes externes.

## FLUX D'ÉVÉNEMENTS

### Flux de Base
1. Initier la connexion.
2. Négocier TLS 1.3.
3. Échanger des données chiffrées.
4. Journaliser les métadonnées de sécurité.

### Flux Alternatifs
- **Certificat invalide** : refuser la connexion et consigner.
- **Protocole obsolète** : imposer la mise à niveau.

## EXIGENCES SPÉCIALES
1. TLS 1.3, PFS, HSTS.
2. Terminateurs redondants.
3. Conformité MSSS/RAMQ.

## PRÉ-CONDITIONS
1. Certificats valides.
2. Pare-feu/WAF configurés.
3. RVSQ disponible.

## POST-CONDITIONS
1. Échanges sécurisés.
2. Événements consignés.
3. Demandes non conformes bloquées.

## CARACTÉRISTIQUE ASSOCIÉE
CAR13 – Utiliser des protocoles sécurisés pour la récupération et l’échange de données
