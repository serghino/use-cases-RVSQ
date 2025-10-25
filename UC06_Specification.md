# UC06 – Garantir la sécurité et la transparence des données

## Informations générales
**ID :** UC06  
**Nom :** Garantir la sécurité et la transparence des données  
**Besoin client associé :** B06  
**Caractéristiques :** CAR13, CAR14, CAR15, CAR16  
**Acteur principal :** Citoyen  
**Acteurs secondaires :** Service d’authentification, Clinique, MSSS/RAMQ

## Description
Ce cas d’utilisation décrit comment la plateforme assure la sécurité, la confidentialité et la traçabilité des données médicales et personnelles des utilisateurs, tout en respectant les normes MSSS/RAMQ et les standards gouvernementaux de cybersécurité.

## Prérequis
- Le service d’authentification gouvernementale est opérationnel  
- Les mécanismes de chiffrement et d’audit sont configurés  
- Les cliniques sont intégrées au système avec des rôles et droits d’accès définis  

## Postconditions
- Les données sont échangées via des protocoles sécurisés  
- Les accès et actions sont tracés et audités  
- Le citoyen peut consulter l’historique d’accès à ses données  

## Scénario nominal
**UC06.1 :** Authentifier l’utilisateur  
1. Le citoyen tente d’accéder à la plateforme RVSQ  
2. Le système demande une authentification multifacteur  
3. Le service d’authentification valide l’identité (CAR13)  

**UC06.2 :** Accéder aux données sécurisées  
4. Le citoyen accède à ses informations médicales via une connexion chiffrée  
5. Le système applique les contrôles d’accès basés sur les rôles (CAR15)  

**UC06.3 :** Journaliser et tracer les accès  
6. Chaque action effectuée (consultation, modification, transmission) est journalisée (CAR14)  
7. Les journaux sont stockés de manière sécurisée et non modifiable  

**UC06.4 :** Auditer et contrôler la conformité  
8. Des audits réguliers sont réalisés automatiquement (CAR16)  
9. Le citoyen peut consulter la liste des accès récents à ses données  

## Scénarios d’exception
**E1 :** Échec d’authentification  
- Le système bloque l’accès et notifie l’utilisateur d’une tentative échouée.  

**E2 :** Anomalie détectée dans les journaux d’accès  
- Le système déclenche une alerte de sécurité et suspend temporairement l’accès.  

## Exigences non fonctionnelles
- **Sécurité :** Authentification multifacteur, chiffrement AES-256  
- **Traçabilité :** Journalisation complète de toutes les actions  
- **Disponibilité :** 99,9 %  
- **Conformité :** Respect des normes MSSS/RAMQ et ISO/IEC 27001  

## Points de traçabilité
- **Besoins :** B06  
- **Caractéristiques :** CAR13, CAR14, CAR15, CAR16  
- **Systèmes :** Service d’authentification, MSSS/RAMQ, DME  

---