# Travaux Pratiques sur Neo4j : Plongée dans l'Univers des Graphes

## Partie 1 : Fondamentaux de Neo4j et Cypher

### Objectifs
- Découvrir les principes de base des bases de données graphe.
- Se familiariser avec l'interface de Neo4j et le langage de requête Cypher.
- Créer et interroger votre première base de données graphe pour modéliser des relations simples.

### Étapes

1. **Introduction à Neo4j :**
   - **Lecture rapide :** Avant de plonger dans la pratique, prenez un moment pour lire une brève introduction sur Neo4j et les bases de données graphe. Comprenez les concepts de nœuds, de relations, de propriétés et d'étiquettes. Cette compréhension théorique est cruciale pour la suite !

2. **Installation de Neo4j Desktop :**
   - **Téléchargement et installation :** Rendez-vous sur le site officiel de Neo4j et téléchargez la dernière version de Neo4j Desktop pour votre système d'exploitation. Suivez les instructions d'installation pour mettre en place l'environnement sur votre machine.
   - **Découverte de l'interface :** Une fois installé, ouvrez Neo4j Desktop et familiarisez-vous avec l'interface. Explorez les différentes sections telles que les projets, les bases de données, et les plugins disponibles.

3. **Création de votre première base de données :**
   - **Création d'un projet :** Dans Neo4j Desktop, créez un nouveau projet en lui donnant le nom de votre choix, par exemple, "MonPremierProjetGraphe".
   - **Ajout d'une base de données :** À l'intérieur de votre projet, créez une nouvelle base de données graphe en mode local. Nommez-la de manière évocatrice, comme "DecouverteNeo4j".
   - **Lancement et exploration :** Lancez votre base de données et ouvrez Neo4j Browser, l'interface web pour interroger et visualiser les graphes.

4. **Premiers pas avec Cypher :**
   - **Syntaxe de base :** Avant de commencer à écrire des requêtes, familiarisez-vous avec la syntaxe de base de Cypher. Apprenez comment créer des nœuds (`CREATE`), établir des relations (`-[]->`), et interroger des données (`MATCH`).
   - **Création de données :** Essayez de créer quelques nœuds représentant des personnes, en leur attribuant des propriétés comme le nom et l'âge. Puis, créez des relations entre ces personnes pour simuler des connaissances ou des liens familiaux.
     ```cypher
     CREATE (Alice:Person {name: 'Alice', age: 24}),
            (Bob:Person {name: 'Bob', age: 27}),
            (Alice)-[:KNOWS]->(Bob)
     ```
   - **Interrogation :** Utilisez la commande `MATCH` pour retrouver et visualiser les données que vous avez créées. Apprenez à utiliser des filtres pour affiner vos recherches.
     ```cypher
     MATCH (n:Person) WHERE n.age > 25 RETURN n
     ```

5. **Exploration et visualisation :**
   - **Analyse des relations :** Expérimentez avec différentes requêtes pour explorer comment les nœuds sont connectés entre eux. Découvrez comment utiliser Cypher pour trouver des chemins, des nœuds intermédiaires, et analyser les réseaux de relations.
   - **Visualisation dans Neo4j Browser :** Utilisez les outils de visualisation pour mieux comprendre la structure de votre graphe. Apprenez à naviguer dans le graphe, à ajuster l'affichage, et à interpréter visuellement les relations entre les nœuds.

🎉 Vous avez maintenant une solide introduction aux bases de données graphe avec Neo4j et le langage Cypher. Vous êtes prêt à passer à la construction d'un réseau social dans la partie suivante de ce TP !