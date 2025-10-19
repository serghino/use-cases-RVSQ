# Use Case Documentation Workflow

>This repository provides a structured approach for documenting each use case with both a specification and a PlantUML diagram.

## 1. Specification Document

For each use case (e.g., UC01), create a Markdown file named `UC01_Specification.md`.

**Content to include:**
- **Title and ID** (e.g., UC01: Réserver un RDV)
- **Actors involved**
- **Preconditions**
- **Main scenario** (step-by-step)
- **Alternative scenarios**
- **Postconditions**

**Example:**
```markdown
# UC01: Réserver un RDV

## Acteurs
- Utilisateur
- Système de réservation

## Préconditions
- L'utilisateur est authentifié

## Scénario principal
1. L'utilisateur demande à réserver un RDV
2. Le système propose des créneaux disponibles
3. L'utilisateur sélectionne un créneau
4. Le système confirme la réservation

## Scénarios alternatifs
- Aucun créneau disponible
- L'utilisateur annule la demande

## Postconditions
- Un RDV est réservé
```

## 2. PlantUML Diagram

For each use case, create a PlantUML file named `UC01_Reserver_RDV.puml`.

**Content to include:**
- Actors and system boundaries
- Interactions (arrows for steps)
- Optionally, notes for alternative flows