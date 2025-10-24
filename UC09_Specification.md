# UC09 – Rechercher automatiquement des rendez-vous 24/24

## Informations générales
**ID :** UC09  
**Nom :** Rechercher automatiquement des rendez-vous 24/24  
**Besoin client associé :** B09  
**Caractéristiques :** CAR22, CAR23  
**Acteur principal :** Citoyen  
**Acteurs secondaires :** DME, Service de notification

## Description
Ce cas d’utilisation décrit comment la plateforme RVSQ permet au citoyen d’activer une recherche automatique et continue de rendez-vous médicaux selon ses critères (spécialité, localisation, disponibilité).  
Le système fonctionne 24h/24 et notifie le citoyen dès qu’un créneau correspondant se libère.

## Prérequis
- Le citoyen dispose d’un compte actif sur la plateforme  
- Les DME sont connectés et synchronisés avec le système  
- Les services de notification (SMS, courriel) sont opérationnels  

## Postconditions
- Le citoyen est automatiquement informé lorsqu’un créneau correspondant à ses critères devient disponible  
- Le système propose la réservation immédiate  
- Les DME sont mis à jour si le citoyen confirme  

## Scénario nominal
**UC09.1 :** Définir les critères de recherche  
1. Le citoyen accède à la fonction « recherche automatique »  
2. Il définit ses critères (spécialité, localisation, plages horaires, préférence de clinique)  
3. Le système enregistre la demande (CAR22)  

**UC09.2 :** Exécuter la recherche continue  
4. Le système interroge régulièrement les DME 24/24  
5. Lorsqu’un créneau correspond, il le réserve temporairement  

**UC09.3 :** Notifier le citoyen  
6. Le citoyen reçoit une notification (courriel, SMS, push mobile)  
7. Il peut confirmer la réservation depuis le message reçu (CAR23)  

**UC09.4 :** Confirmer ou ignorer  
8. Si le citoyen confirme, le rendez-vous est enregistré dans le DME  
9. Si aucun retour n’est reçu après un délai (ex. 10 min), la plage est libérée  

## Scénarios d’exception
**E1 :** Aucun créneau disponible  
- Le système conserve la recherche en attente et poursuit la surveillance.  

**E2 :** Erreur de communication avec un DME  
- Le système saute la source en erreur et continue la recherche sur les autres.  

**E3 :** Notifications non livrées  
- Le système relance l’envoi et journalise l’échec.  

## Exigences non fonctionnelles
- **Disponibilité :** Fonctionnement 24h/24, 7j/7  
- **Performance :** Délai de détection < 1 minute après libération d’un créneau  
- **Fiabilité :** Taux de réussite d’envoi des notifications ≥ 98 %  
- **Sécurité :** Transmission chiffrée des critères et notifications  

## Points de traçabilité
- **Besoins :** B09  
- **Caractéristiques :** CAR22, CAR23  
- **Systèmes :** DME, Service de notification