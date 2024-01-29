# Liste des Requêtes pour le Mini-Jeu "Trouvez la Requête Rapide"

## Index et Requêtes

### 1. Index sur le champ `age` dans une collection `utilisateurs`
   - **Requêtes :**
     1. `db.utilisateurs.find({ age: { $gt: 30 } })`
     2. `db.utilisateurs.find({ nom: "Dupont" })`
     3. `db.utilisateurs.find({ age: { $lte: 25 }, ville: "Paris" })`

### 2. Index composite sur les champs `nom` et `ville` dans une collection `clients`
   - **Requêtes :**
     1. `db.clients.find({ ville: "Lyon" })`
     2. `db.clients.find({ nom: "Durand", ville: "Marseille" })`
     3. `db.clients.find({ nom: "Durand" })`

### 3. Index de texte sur le champ `description` dans une collection `produits`
   - **Requêtes :**
     1. `db.produits.find({ $text: { $search: "bio" } })`
     2. `db.produits.find({ prix: { $lt: 20 } })`
     3. `db.produits.find({ $text: { $search: "durable" } })`

### 4. Index géospatial sur le champ `location` dans une collection `magasins`
   - **Requêtes :**
     1. `db.magasins.find({ location: { $near: [50.85045, 4.34878] } })`
     2. `db.magasins.find({ type: "supermarché" })`
     3. `db.magasins.find({ location: { $geoWithin: { $geometry: { type: "Polygon", coordinates: [...] } } } })`

### 5. Index sur le champ `dateDeNaissance` dans une collection `personnes`
   - **Requêtes :**
     1. `db.personnes.find({ dateDeNaissance: { $gt: new Date('1990-01-01') } })`
     2. `db.personnes.find({ prénom: "Alice" })`
     3. `db.personnes.aggregate([{ $group: { _id: "$dateDeNaissance", nombre: { $sum: 1 } } }])`

## Conclusion
Chaque index est spécialement conçu pour optimiser certains types de requêtes. Comprendre ces correspondances est crucial pour utiliser efficacement les bases de données MongoDB. 🧠💡