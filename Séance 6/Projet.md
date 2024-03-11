# Projet TP : Création d'un Mini Réseau Social avec Neo4j

## Contexte
Vous allez endosser le rôle de développeur de bases de données pour concevoir un mini réseau social. Ce projet vous permettra de mettre en pratique vos compétences en modélisation de données et en interrogation de bases de données graphe avec Neo4j.

## Objectifs
- Modéliser les utilisateurs et leurs relations dans un réseau social.
- Utiliser le langage Cypher pour manipuler et interroger votre base de données.
- Appliquer vos connaissances pour créer un modèle de données flexible et évolutif.

## Instructions

### Étape 1 : Modélisation des Utilisateurs
1. **Initialisation :** Lancez votre base de données Neo4j et accédez à Neo4j Browser.
2. **Création des utilisateurs :** Définissez un ensemble d'au moins 10 utilisateurs, en leur attribuant des propriétés variées (nom, âge, ville...). Laissez libre cours à votre créativité pour les propriétés, mais assurez-vous qu'elles soient pertinentes pour un réseau social.

### Étape 2 : Établissement des Relations
1. **Relations d'amitié :** Modélisez des relations `FRIENDS_WITH` entre les utilisateurs. Choisissez vous-même qui est ami avec qui, en gardant à l'esprit la structure d'un réseau social réel.
2. **Intérêts :** Introduisez des nœuds `Interest` pour représenter les centres d'intérêt. Liez les utilisateurs à leurs intérêts avec des relations `INTERESTED_IN`. La spécificité et le nombre d'intérêts sont à votre discrétion.

### Étape 3 : Exploration de la Base de Données
1. **Requêtes Cypher :** Formulez des requêtes pour explorer votre réseau. Par exemple, identifiez les utilisateurs par ville, trouvez les amis d'un utilisateur spécifique, ou découvrez les intérêts communs entre amis.
2. **Analyse du réseau :** Utilisez Cypher pour analyser la structure de votre réseau. Qui sont les utilisateurs les plus connectés ? Quels intérêts sont les plus populaires ?

### Bonus
1. **Groupes :** Ajoutez une nouvelle dimension à votre réseau en créant des groupes. Les utilisateurs peuvent rejoindre des groupes selon leurs intérêts ou activités.
2. **Événements :** Modélisez des événements auxquels les utilisateurs peuvent participer. Cela peut inclure des rencontres, des conférences, ou des activités de groupe.

## Livrable
Votre livrable sera une base de données Neo4j contenant :
- Un ensemble d'utilisateurs avec leurs propriétés.
- Des relations d'amitié entre ces utilisateurs.
- Des intérêts et la liaison entre utilisateurs et leurs intérêts.
- **Pour le bonus :** Des groupes et événements, ainsi que la participation des utilisateurs à ces derniers.

Vous devrez également fournir un document (ou un ensemble de captures d'écran) montrant :
- La structure de votre base de données (modèle de données).
- Des exemples de requêtes Cypher utilisées pour interroger la base de données, accompagnées de leurs résultats.
- Une brève analyse de votre réseau social basée sur les requêtes effectuées.

### Conseils
- Soyez créatifs dans la modélisation de votre réseau social. Réfléchissez aux types de relations, d'intérêts, de groupes, et d'événements qui pourraient exister dans un réseau social réel.
- Testez différentes requêtes Cypher pour explorer en profondeur votre base de données. C'est en expérimentant que vous découvrirez les puissantes capacités d'interrogation de Neo4j.
- Documentez bien vos découvertes et analyses. Ce travail de documentation sera précieux pour montrer votre capacité à comprendre et à analyser des données complexes.

🚀 Bonne chance et amusez-vous bien avec Neo4j !