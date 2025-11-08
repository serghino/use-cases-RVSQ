# Objectif du Prototypage - Plateforme RVSQ

## 1.1 Objectif du prototypage

Le but du prototypage est de permettre aux **citoyens** de visualiser et d'expérimenter le **processus de recherche et de réservation de rendez-vous médicaux** sur la **Plateforme RVSQ (Rendez-Vous Santé Québec)**. L'objectif principal est de recueillir des **retours utilisateurs** concernant la **facilité d'utilisation**, la **convivialité** et l'**ergonomie** de l'interface de recherche.

Dans RVSQ, les aspects critiques identifiés sont les **mécanismes de recherche multi-critères**, les **propositions intelligentes en cas d'absence de résultats**, et la **navigation intuitive** entre les différentes étapes (recherche, consultation des résultats, réservation). Ces aspects sont critiques pour assurer une **adoption rapide** par les citoyens et réduire la **courbe d'apprentissage** nécessaire à l'utilisation autonome de la plateforme.

---

## 1.2 Cas d'utilisation ciblés pour le prototypage

L'objectif du prototype est de valider la partie centrale de RVSQ : le parcours recherche-réservation (RVSQ-UC-01 et RVSQ-UC-02). Ces deux cas d'utilisation forment le cœur de l'expérience citoyen et soulèvent de nombreuses questions qui doivent être clarifiées avant développement :
• Dans quel ordre présenter les critères de recherche ?
• Comment gérer l'affichage quand aucun rendez-vous n'est trouvé ?
• Quelle présentation adopter pour les disponibilités des professionnels ?
• Quand et comment proposer d'élargir les critères de recherche ?
• Comment assurer une transition fluide de la recherche vers la réservation ?
• Quels indicateurs visuels afficher durant les opérations ?
• …

Le prototype permettra d'identifier les zones d'incertitude et de recueillir les retours utilisateurs sur ce parcours critique, tout en donnant aux parties prenantes une vision concrète de la valeur principale de la plateforme.

### 1.2.1 RVSQ-UC-01 : Rechercher un rendez-vous
**Justification :** Ce cas d'utilisation constitue le **point d'entrée principal** de la plateforme et nécessite une attention particulière sur :
- L'**ergonomie des filtres de recherche** (type de consultation, spécialité, localisation, langue)
- La **facilité de compréhension** des options disponibles pour les citoyens
- La **clarté de l'affichage des résultats** avec les informations pertinentes (nom, distance, disponibilités)
- Les **suggestions intelligentes** lorsqu'aucun résultat n'est trouvé (élargir le rayon, modifier les critères)
- La **fluidité de la navigation** entre la saisie des critères et la consultation des résultats
- Le **retour visuel immédiat** pendant la recherche (indicateurs de chargement, messages informatifs)

**Aspects critiques à valider avec les utilisateurs :**
- **Convivialité :** La recherche est-elle intuitive ? Les utilisateurs trouvent-ils facilement ce qu'ils cherchent ?
- **Ergonomie :** Les filtres sont-ils bien positionnés ? La hiérarchie visuelle est-elle claire ?
- **Apprentissage :** Un nouvel utilisateur peut-il effectuer une recherche sans aide ? Combien de temps faut-il pour maîtriser l'outil ?
- **Retours visuels :** Les messages en cas d'absence de résultats sont-ils utiles ? Les suggestions alternatives sont-elles pertinentes ?


## 1.3 Bénéfices attendus du prototypage

Le prototypage permettra de :

1. **Recueillir des retours utilisateurs concrets** sur la facilité de recherche et de réservation de rendez-vous
2. **Évaluer l'ergonomie** de l'interface et identifier les points de friction dans le parcours utilisateur
3. **Tester la clarté** des messages et des propositions alternatives en cas d'absence de résultats
4. **Valider l'intuitivité** de la navigation entre les différentes étapes du processus
5. **Mesurer la courbe d'apprentissage** nécessaire pour une utilisation autonome de la plateforme
6. **Optimiser l'adoption** en ajustant l'interface selon les observations et retours des citoyens
7. **Affiner les propositions intelligentes** de recherche pour améliorer le taux de succès

---

## 1.4 Portée du prototype

Le prototype se concentrera sur les **interfaces de recherche et de réservation** pour le cas d'utilisation RVSQ-UC-01, en mettant l'accent sur :

- L'**ergonomie de l'écran de recherche** avec ses filtres et critères
- La **navigation intuitive** entre la recherche, les résultats et la réservation
- Les **retours visuels** pendant la recherche (états de chargement, indicateurs de progression)
- Les **messages et suggestions** en cas d'absence de résultats ou de recherche infructueuse
- Les **propositions alternatives** pour aider l'utilisateur à reformuler sa recherche (élargir rayon, modifier critères)
- La **présentation claire** des résultats (informations pertinentes, hiérarchie visuelle)
- La **cohérence visuelle** et la **simplicité d'utilisation** pour favoriser l'adoption rapide