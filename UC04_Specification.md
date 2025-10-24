# UC04 – Optimiser l’utilisation des plages horaires

## Informations générales
**ID :** UC04  
**Nom :** Optimiser l’utilisation des plages horaires  
**Besoin client associé :** B04  
**Caractéristiques :** CAR09, CAR10  
**Acteur principal :** Clinique  
**Acteurs secondaires :** Citoyen, Service de messagerie, DME (Dossier Médical Électronique)

## Description
Ce cas d’utilisation décrit la manière dont la plateforme aide les cliniques à optimiser l’utilisation des plages horaires vacantes grâce à un système proactif de notifications automatisées (courriel, SMS, appels).

## Prérequis
- Les cliniques ont publié leurs disponibilités dans le système  
- Les notifications (SMS, courriels) sont configurées  
- Le DME est synchronisé avec la plateforme

## Postconditions
- Les plages vacantes sont automatiquement proposées à des patients en attente  
- Le patient reçoit une notification et peut confirmer son rendez-vous  
- Le calendrier de la clinique est mis à jour en temps réel

## Scénario nominal
**UC04.1 :** Détecter une plage vacante  
1. Le système surveille les plages horaires disponibles dans le DME  
2. Lorsqu’une annulation est détectée, la plage devient disponible  

**UC04.2 :** Identifier les patients correspondants  
3. Le système recherche les patients inscrits sur la liste d’attente correspondant aux critères (spécialité, localisation, disponibilité)  

**UC04.3 :** Envoyer les notifications  
4. Le système envoie des notifications automatiques (CAR09) par courriel, SMS ou appel  
5. Les patients intéressés peuvent confirmer directement leur disponibilité  

**UC04.4 :** Réserver automatiquement  
6. Le premier patient à confirmer voit la plage automatiquement réservée  
7. Le DME est mis à jour en temps réel (CAR10)  
8. Les autres notifications sont annulées

## Scénarios d’exception
**E1 :** Aucun patient ne répond  
- La plage reste disponible et le système relance la notification après un délai configuré.  

**E2 :** Erreur de synchronisation avec le DME  
- Le système signale l’erreur et suspend la notification jusqu’à la résolution.  

## Exigences non fonctionnelles
- **Performance :** Détection des plages vacantes en moins de 5 secondes  
- **Disponibilité :** Service 24h/24  
- **Fiabilité :** Taux de succès des notifications ≥ 99 %  
- **Sécurité :** Chiffrement des échanges entre la plateforme et les cliniques  

## Points de traçabilité
- **Besoins :** B04  
- **Caractéristiques :** CAR09, CAR10  
- **Systèmes :** DME, Service de messagerie