# Travaux Pratiques : Intégration de MongoDB dans une Application Express

## Objectif
Créer une API simple avec Express.js et intégrer MongoDB pour gérer les données.

## Prérequis
- Node.js et npm installés sur votre machine.
- MongoDB installé localement ou avoir un cluster MongoDB Atlas.
- Connaissances de base en JavaScript et Node.js.

## Partie 1: Configuration de l'Environnement
**Durée estimée :** 30 minutes

### Étapes
1. **Création du Projet :**
   - Créez un nouveau dossier pour votre projet : `mkdir monAppMongoDB`
   - Allez dans le dossier : `cd monAppMongoDB`
   - Initialisez un nouveau projet Node.js : `npm init -y`

2. **Installation des Dépendances :**
   - Installez Express et le pilote MongoDB : `npm install express mongodb`
   - Installez Nodemon pour le rechargement automatique (facultatif) : `npm install --save-dev nodemon`

3. **Configuration de Nodemon :**
   - Dans `package.json`, ajoutez un script de démarrage :
     ```json
     "scripts": {
       "start": "nodemon app.js"
     }
     ```

## Partie 2: Création de l'API Express
**Durée estimée :** 1 heure

### Étapes
1. **Mise en Place de l'Application Express :**
   - Créez un fichier `app.js`.
   - Initialisez Express :
     ```javascript
     const express = require('express');
     const app = express();
     app.use(express.json());
     const port = 3000;

     app.listen(port, () => {
       console.log(`Serveur lancé sur http://localhost:${port}`);
     });
     ```

2. **Configuration de la Connexion MongoDB :**
   - Ajoutez le code suivant pour connecter MongoDB :
     ```javascript
     const { MongoClient } = require('mongodb');
     const uri = "votre_uri_mongodb";
     const client = new MongoClient(uri, { useNewUrlParser: true, useUnifiedTopology: true });

     client.connect(err => {
       if (err) {
         console.error('Erreur de connexion à MongoDB', err);
         process.exit(1);
       }
       console.log('Connecté à la base de données MongoDB');
       // Vous pouvez commencer à utiliser MongoDB ici
     });
     ```

## Partie 3: Création des Routes de l'API
**Durée estimée :** 1 heure 30 minutes

### Étapes
1. **Création d'une Route pour Ajouter des Données :**
   - Ajoutez une route POST pour ajouter des données à MongoDB.
     ```javascript
     app.post('/ajouter', async (req, res) => {
       try {
         const collection = client.db("test").collection("documents");
         const result = await collection.insertOne(req.body);
         res.status(201).send(result);
       } catch (error) {
         res.status(500).send(error.message);
       }
     });
     ```

2. **Création d'une Route pour Lire des Données :**
   - Ajoutez une route GET pour lire des données.
     ```javascript
     app.get('/lire', async (req, res) => {
       try {
         const collection = client.db("test").collection("documents");
         const result = await collection.find({}).toArray();
         res.status(200).send(result);
       } catch (error) {
         res.status(500).send(error.message);
       }
     });
     ```

## Partie 4: Test de l'API
**Durée estimée :** 30 minutes

### Étapes
1. **Démarrage de l'API :**
   - Exécutez votre API : `npm start`

2. **Test de l'API :**
   - Utilisez un outil comme Postman ou cURL pour tester les routes POST et GET.
   - Envoyez des requêtes POST pour ajouter des données.
   - Envoyez des requêtes GET pour lire les données ajoutées.

## Conclusion
Vous avez maintenant une API Express fonctionnelle intégrée avec MongoDB ! Vous pouvez étendre cette API pour inclure plus de fonctionnalités comme la mise à jour et la suppression de données.