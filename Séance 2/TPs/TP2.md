# Travaux Pratiques: Gestion des Sessions Utilisateur avec Redis en Go

## Partie: Gestion des Sessions Utilisateur en Go avec Redis
**Durée estimée :** 3 heures

### Objectifs
- Comprendre et implémenter la gestion des sessions utilisateur en utilisant Redis
- Explorer l'intégration de Redis pour le stockage de session dans une application web Go

### Prérequis
- Connaissances en développement Go (Golang)
- Redis installé et en fonction sur votre machine
- Un environnement de développement Go configuré

### Étapes

#### Étape 1: Création d'une Application Web en Go avec Authentification
1. **Développez une Application Web Basique en Go :**
   - Créez une application web simple avec une page d'accueil et une page de connexion.
   - Implémentez un système d'authentification basique où l'utilisateur peut se connecter avec un nom d'utilisateur et un mot de passe.

   ```go
   package main

   import (
       "fmt"
       "net/http"
   )

   func main() {
       http.HandleFunc("/", homePage)
       http.HandleFunc("/login", login)
       http.ListenAndServe(":8080", nil)
   }

   func homePage(w http.ResponseWriter, r *http.Request) {
       fmt.Fprintf(w, "Bienvenue sur la page d'accueil !")
   }

   func login(w http.ResponseWriter, r *http.Request) {
       if r.Method == "POST" {
           r.ParseForm()
			username := r.Form.Get("username")
			_ = r.Form.Get("password")
       } else {
		fmt.Fprintf(w, `<form method="POST">
			Username: <input type="text" name="username"/>
			Password: <input type="password" name="password"/>
			<input type="submit" value="Login"/>
		</form>`)
   }
   ```

#### Étape 2: Intégration de Redis pour la Gestion des Sessions
1. **Configurez Redis dans Votre Application :**
   - Établissez une connexion entre votre application Go et le serveur Redis.
   - Utilisez le package Redis pour Go pour intégrer Redis.

2. **Gestion des Sessions :**
   - Lorsqu'un utilisateur se connecte, créez une session unique et stockez-la dans Redis.
   - Utilisez un identifiant de session (par exemple, un UUID) comme clé et stockez les informations de l'utilisateur (comme le nom d'utilisateur) dans Redis.

   ```go
   package main

   import (
       "github.com/go-redis/redis"
       "github.com/google/uuid"
   )

   func newRedisClient() *redis.Client {
       // Configuration similaire à l'étape 2 de l'application de cache
   }

   func createSession(client *redis.Client, username string) string {
       sessionToken := uuid.New().String()
       _, err := client.Set(sessionToken, username, 120*time.Second).Result()
       if err != nil {
           // Gérez l'erreur
       }
       return sessionToken
   }
   ```

#### Étape 3: Exercices d'Autonomie
1. **Implémentez la Vérification de Session :**
   - Ajoutez une fonctionnalité qui vérifie la session de l'utilisateur à chaque requête. Si la session est valide (présente dans Redis), l'utilisateur est considéré comme connecté.
   - Si la session n'existe pas ou a expiré, redirigez l'utilisateur vers la page de connexion.

2. **Gestion des Sessions Expirées :**
   - Implémentez un mécanisme pour gérer les sessions expirées. Par exemple, affichez un message d'erreur ou redirigez l'utilisateur vers la page de connexion.

3. **Développement de Fonctionnalités Supplémentaires :**
   - Explorez la possibilité d'ajouter des fonctionnalités supplémentaires, comme la déconnexion, la prolongation des sessions, ou la modification des informations de l'utilisateur.
