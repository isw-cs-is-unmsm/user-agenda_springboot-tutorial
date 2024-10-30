
# User API Documentation

This document provides examples of how to interact with the User API, which includes creating, retrieving, updating, and deleting users.

---

## 1. Create a User (POST)

To create a new user, use the POST method with a JSON payload:

```bash
curl -X POST http://localhost:8081/api/users \
   -H "Content-Type: application/json" \
   -d '{
         "name": "John",
         "lastname": "Doe",
         "hobbie": "Reading",
         "description": "An avid reader of mystery novels",
         "photo": null
       }'
```

---

## 2. Get All Users (GET)

To retrieve all users:

```bash
curl -X GET http://localhost:8081/api/users
```

---

## 3. Get a User by ID (GET)

To retrieve a user by their ID, replace `{id}` with the specific user ID:

```bash
curl -X GET http://localhost:8081/api/users/{id}
```

---

## 4. Update a User (PUT)

To update a user by ID, replace `{id}` with the specific user ID and provide the updated user details in JSON format:

```bash
curl -X PUT http://localhost:8081/api/users/{id} \
   -H "Content-Type: application/json" \
   -d '{
         "name": "Jane",
         "lastname": "Doe",
         "hobbie": "Traveling",
         "description": "A world traveler",
         "photo": null
       }'
```

---

## 5. Delete a User (DELETE)

To delete a user by ID, replace `{id}` with the specific user ID:

```bash
curl -X DELETE http://localhost:8081/api/users/{id}
```
