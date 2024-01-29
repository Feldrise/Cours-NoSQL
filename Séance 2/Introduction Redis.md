# Introduction à Redis

## Partie 1: Théorie 
**Durée estimée :** 1 heure 30 minutes

### Objectifs
- Explorer en profondeur les caractéristiques et fonctionnalités de Redis
- Comprendre les principes de fonctionnement de Redis de manière interactive

### Contenu
Redis, abréviation de "REmote DIctionary Server", est plus qu'un simple outil de stockage de données en mémoire. C'est une solution polyvalente qui peut révolutionner la manière dont les applications gèrent les données. 

#### 1. **Architecture et Performance de Redis**
   - **En Mémoire :** Redis stocke l'intégralité de ses données en mémoire, ce qui réduit considérablement le temps d'accès aux données par rapport aux bases de données basées sur le stockage disque. 
     - **Interactivité :** Discutons de la différence de vitesse entre la mémoire et le disque. Quels sont les avantages de la vitesse de Redis pour des applications en temps réel ?
   - **Modèle Single-Threaded :** Redis utilise un modèle single-threaded. Cela signifie qu'il traite une commande à la fois, mais à une vitesse incroyable.
     - **Interactivité :** Réfléchissons à comment cette conception affecte la performance et la simplicité de Redis. Pourquoi est-ce bénéfique pour certaines applications ?

#### 2. **Structures de Données Riches**
   - Redis offre une variété de structures de données, comme les strings, lists, sets, sorted sets, hashes, streams, et plus.
   - Chaque structure de données a ses cas d'utilisation spécifiques et offre une flexibilité incroyable.
     - **Interactivité :** Analysons ensemble des scénarios d'utilisation pour chaque type de structure de données. Par exemple, quand utiliseriez-vous un set plutôt qu'une list ?

#### 3. **Persistance et Durabilité**
   - **Snapshots et Journaux de Transactions :** Redis offre des options de persistance, comme RDB (snapshots périodiques) et AOF (Append Only File pour enregistrer chaque opération).
     - **Interactivité :** Discutons des avantages et inconvénients de chaque méthode de persistance. Quel scénario nécessiterait l'utilisation de RDB et dans quel cas préférer AOF ?

#### 4. **Scalabilité et Haute Disponibilité**
   - **Réplication et Partitionnement :** Redis supporte la réplication master-slave et le partitionnement de données pour une meilleure scalabilité.
   - **Redis Cluster :** Pour une haute disponibilité et une partitionnement automatique des données.
     - **Interactivité :** Imaginons une architecture Redis pour une application e-commerce à fort trafic. Comment configureriez-vous les réplicas et les clusters ?

#### 5. **Cas d'Utilisation et Scénarios Réels**
   - **Cache :** Utilisation de Redis comme système de cache pour améliorer les performances des applications.
   - **Gestion des Sessions :** Idéal pour gérer les sessions utilisateur dans des applications web.
   - **Systèmes de File d'Attente :** Utilisé dans les systèmes de messagerie et de file d'attente.
     - **Interactivité :** Choisissons un scénario, par exemple une application de médias sociaux, et explorons comment Redis pourrait être utilisé dans ce contexte.

## Partie 2: Exemples Pratiques
**Durée estimée :** 2 heures 30 minutes

### Objectifs
- Mettre en pratique les connaissances théoriques acquises sur Redis
- Apprendre à interagir avec Redis en utilisant des commandes de base

### Étapes

#### Étape 1: Installation de Redis
- Téléchargez et installez Redis sur votre machine (instructions disponibles sur le site officiel de Redis).
- Lancez le serveur Redis et testez sa connexion.

#### Étape 2: Interaction de Base avec Redis
- Connectez-vous au serveur Redis via la ligne de commande.
- Exécutez quelques commandes de base :
  - Créer une clé avec une chaîne de caractères: `SET maCle "Bonjour Redis"`
  - Récupérer la valeur d'une clé: `GET maCle`
  - Supprimer une clé: `DEL maCle`

#### Étape 3: Travailler avec des Structures de Données Complexes
- Listes : Utilisez `LPUSH` et `RPUSH` pour ajouter des éléments, et `LRANGE` pour les récupérer.
- Sets : Expérimentez avec `SADD`, `SMEMBERS`, et `SISMEMBER`.
- Hashs : Créez et manipulez des hash avec `HSET`, `HGETALL`, et `HDEL`.

---

Cela devrait offrir une introduction solide à Redis, combinant théorie et pratique. N'oubliez pas de vous amuser et d'explorer les possibilités offertes par Redis. Bonne chance ! 🌟