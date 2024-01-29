# Travaux Pratiques: Développement d'une Application de Cache avec Redis en Go

## Partie: Application de Cache Redis en Go
**Durée estimée :** 3 heures

### Objectifs
- Développer une application en Go qui utilise Redis pour le caching
- Comprendre l'intégration de Redis dans un environnement de développement Go

### Prérequis
- Connaissances de base en Go (Golang)
- Redis installé et fonctionnel sur votre machine
- Un environnement de développement Go configuré (IDE ou éditeur de texte, avec Go installé)

### Étapes

#### Étape 1: Création de l'Application Web en Go
1. **Créez une Application Web Basique en Go :**
   - Développez une application Go qui fait une requête HTTP à une API externe. Par exemple, utilisez l'API OpenWeatherMap pour obtenir des données météorologiques.
   - Implémentez une fonction qui envoie une requête à l'API et reçoit la réponse.

   ```go
   package main

   import (
       "io/ioutil"
       "log"
       "net/http"
   )

   func fetchWeatherData(city string) string {
       resp, err := http.Get("https://api.openweathermap.org/data/2.5/weather?q=" + city + "&appid=your_api_key")
       if err != nil {
           log.Fatal(err)
       }
       defer resp.Body.Close()
       body, err := ioutil.ReadAll(resp.Body)
       if err != nil {
           log.Fatal(err)
       }
       return string(body)
   }

   func main() {
       // Exemple d'appel de fonction
       weatherData := fetchWeatherData("Paris")
       log.Println(weatherData)
   }
   ```

#### Étape 2: Intégration de Redis
1. **Intégrez Redis dans votre Application Go :**
   - Installez le package Redis pour Go, par exemple, en utilisant `go get github.com/redis/go-redis/v9`
   - Établissez une connexion entre votre application Go et le serveur Redis.

   ```go
   package main

   import (
       "github.com/redis/go-redis/v9"
   )

   func newRedisClient() *redis.Client {
       client := redis.NewClient(&redis.Options{
           Addr:     "localhost:6379", // Adresse du serveur Redis
           Password: "",              // Pas de mot de passe
           DB:       0,               // Base de données par défaut
       })
       return client
   }
   ```

#### Étape 3: Mise en Place du Caching
1. **Cachez les Réponses de l'API :**
   - Avant de faire une requête à l'API, vérifiez si les données pour la ville spécifique sont déjà dans le cache Redis. Utilisez les fonctions `Get` et `Set` du client Redis.

   ```go
   func getCachedWeatherData(client *redis.Client, city string) string {
       cachedData, err := client.Get(context.TODO(), city).Result()
       if err == redis.Nil {
           // Données non trouvées dans Redis, besoin de faire une requête à l'API
           data := fetchWeatherData(city)
           // Mettez en cache les données avec un TTL
           client.Set(context.TODO(), city, data, 300 * time.Second)
           return data
       } else if err != nil {
           log.Fatal(err)
       }
       return cachedData // Retournez les données du cache
   }
   ```

#### Étape 4: Exercices d'Autonomie
1. **Optimisation et Test de l'Application :**
Tester différentes valeurs de TTL pour le cache et observer l'impact sur les performances.

2. **Développement de Fonctionnalités Supplémentaires :**
   - Ajoutez des fonctionnalités supplémentaires à l'application, comme la prise en charge de différentes villes ou différents types de données météorologiques.

---

Ce TP offre une expérience pratique de développement d'une application Go en utilisant Redis pour le caching. Il combine l'apprentissage guidé avec des opportunités d'exploration autonome, permettant aux étudiants de consolider leurs connaissances et de développer leurs compétences de manière créative. Bon codage ! 🌟👨‍💻👩‍💻