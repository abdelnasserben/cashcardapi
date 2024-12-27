
## API **Cash Card**  

Bienvenue dans le projet **Cash Card**, une solution pour simplifier la gestion des allocations familiales. Cette application utilise **Spring Boot** pour offrir une API RESTful sécurisée et performante, avec une conception robuste et des fonctionnalités bien pensées. 

---


### **Présentation**  
Le **Cash Card** permet aux parents de gérer facilement les fonds destinés à leurs enfants, en remplaçant l'argent liquide par des "cash cards" virtuelles. Ces cartes fonctionnent de manière similaire à des cartes cadeaux et permettent de :  
- Envoyer, recevoir et suivre les fonds alloués.  
- Contrôler les transactions à tout moment.  

---

#### **Architecture et conception**  
L'application a été développée en suivant une approche incrémentale et orientée projet :  

1. **API RESTful** :  
   - Un design axé sur la simplicité et l'efficacité pour permettre une interaction fluide avec les "cash cards".  
   - Endpoints bien définis pour effectuer les opérations CRUD (Create, Read, Update, Delete).  

2. **Base de données relationnelle** :  
   - Les "cash cards" sont stockées dans une base de données relationnelle, avec un mapping des données en objets Java grâce à Spring Data.  

3. **Sécurité** :  
   - Intégration de **Spring Security** pour garantir une protection optimale contre les accès non autorisés.  
   - Gestion des rôles et authentification pour chaque endpoint.  

4. **Test-First** :  
   - L'application a été développée en utilisant une approche **Test-Driven Development (TDD)** et **La boucle "Red, Green, Refactor"**. Cela signifie que les tests sont écrits avant même d'implémenter une fonctionnalité. Cette méthode garantit une application fiable, robuste et évolutive. 

5. **Steel Thread** :  
   - Une approche progressive où chaque intégration clé (API, base de données, sécurité) est mise en place pour fournir un produit fonctionnel dès les premières étapes.  

---


### **Endpoints principaux**  
Voici les endpoints disponibles pour interagir avec l'application :  

| Méthode | Endpoint               | Description                           | Authentification requise |  
|---------|------------------------|---------------------------------------|---------------------------|  
| GET     | `/cashcards`           | Liste toutes les cartes.              | ✅ Oui                    |  
| POST    | `/cashcards`           | Crée une nouvelle carte.              | ✅ Oui                    |  
| GET     | `/cashcards/{id}`      | Affiche les détails d'une carte.      | ✅ Oui                    |  
| PUT     | `/cashcards/{id}`      | Met à jour une carte existante.       | ✅ Oui                    |  
| DELETE  | `/cashcards/{id}`      | Supprime une carte.                   | ✅ Oui                    |  

---


### **Contrats de l'API**
Voici en détails comment réagir avec l'API:

#### **1. Récupérer une Cash Card par ID**

##### **Request**  
- **URI** : `/cashcards/{requestedId}`  
- **HTTP Verb** : `GET`  
- **Body** : Aucun 

##### **Response**  
- **HTTP Status** :  
  - `200 OK` : La Cash Card a été trouvée et appartient à `sarah1`.  
  - `404 NOT FOUND` : La Cash Card n'existe pas ou n'appartient pas à `sarah1`.  

- **Body Type** : JSON  
- **Example Body** :  
  ```json
  {
    "id": 99,
    "amount": 123.45,
    "owner": "sarah1"
  }
  ```

#### **2. Créer une Cash Card**

##### **Request**  
- **URI** : `/cashcards`  
- **HTTP Verb** : `POST`  
- **Body** :  
  ```json
  {
    "amount": 100.00
  }
  ```
##### **Response**  
- **HTTP Status** :  
  - `201 CREATED` : La Cash Card a été créée avec succès.
- **Headers** :  
  - `Location` : L'URI de la nouvelle Cash Card, permettant au client d'accéder à la Cash Card créée.
- **Body** : Aucun.

#### **Récupérer toutes les Cash Cards**

##### **Request**  
- **URI** : `/cashcards`  
- **HTTP Verb** : `GET`
- **Parameters** :
  - `page` : Numéro de la page (par défaut : 0).
  - `size` : Taille de la page (par défaut : 20).
  - `sort` : Propriété pour trier (par défaut : amount,asc).  
- **Body** : Aucun

##### **Response**  
- **HTTP Status** :  
  - `200 OK` : La liste des Cash Cards a été récupérée avec succès.

- **Body Type** : JSON  
- **Example Body** :  
  ```json
  [
    {
      "id": 99,
      "amount": 123.45,
      "owner": "sarah1"
    },
    {
      "id": 100,
      "amount": 1.00,
      "owner": "sarah1"
    }
  ]
  ```

#### **Mettre à jour une Cash Card par ID**

##### **Request**  
- **URI** : `/cashcards/{requestedId}`  
- **HTTP Verb** : `PUT`  
- **Body** :  
  ```json
  {
    "amount": 150.00
  }
  ```
##### **Response**  
- **HTTP Status** :  
  - `204 NO CONTENT` : La Cash Card a été mise à jour avec succès.
  - `404 NOT FOUND` : La Cash Card n'existe pas ou n'appartient pas à l'utilisateur connecté.
- **Body** : Aucun.

#### **Supprimer une Cash Card par ID**

##### **Request**  
- **URI** : `/cashcards/{id}`  
- **HTTP Verb** : `DELETE`  
- **Body** : None

##### **Response**  
- **HTTP Status** :  
  - `204 NO CONTENT` : La Cash Card a été supprimée avec succès.  
  - `404 NOT FOUND` : La Cash Card n'existe pas ou n'appartient pas à l'utilisateur connecté.  

- **Body** : None  

---


### **Comment commencer ?**  
1. Clonez ce dépôt :  
   ```bash
   git clone https://github.com/abdelnasserben/cashcardapi.git
   ```
