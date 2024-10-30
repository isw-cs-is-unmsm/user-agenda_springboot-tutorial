
# User Agenda Project

This project is a simple **User Agenda** built using **Spring Boot** to demonstrate CRUD (Create, Read, Update, Delete) operations. 
The application allows you to manage users by performing basic CRUD actions through RESTful API endpoints. 
Each user entry consists of a `name`, `lastname`, `hobbie`, `photo`, and a `description`.

## Project Structure

The project follows the **Model-View-Controller (MVC)** design pattern. Here’s a breakdown of the main components:

### 1. Model (User.java)
The `User` class is a Java Persistence API (JPA) entity that represents the database table schema. The `User` class has the following fields:
- `id`: Primary key, auto-generated integer value.
- `name`: String, stores the user's first name.
- `lastname`: String, stores the user's last name.
- `hobbie`: String, stores the user's hobby.
- `photo`: Binary data type (BLOB) to store an image file for the user (optional).
- `description`: Text, a detailed description of the user.

### 2. Repository (UserRepository.java)
The `UserRepository` interface extends Spring Data JPA’s `JpaRepository`, providing standard CRUD operations without requiring custom queries. 
This interface allows the application to communicate with the database layer to perform operations such as saving, updating, deleting, and finding users.

### 3. Service (UserService.java)
The `UserService` class provides the business logic layer. It includes methods for each CRUD operation and leverages the `UserRepository` 
to interact with the database. This design makes the application more modular, as the service layer separates business logic from data access.

### 4. Controller (UserController.java)
The `UserController` class is a REST controller that handles HTTP requests mapped to specific endpoints. It uses `UserService` 
to perform operations on `User` objects and return responses. The main endpoints include:

- `GET /api/users`: Retrieves all users.
- `GET /api/users/{id}`: Retrieves a user by ID.
- `POST /api/users`: Creates a new user.
- `PUT /api/users/{id}`: Updates an existing user by ID.
- `DELETE /api/users/{id}`: Deletes a user by ID.


## How to Run the Project

1. **Prerequisites**: 
   - Java 8 or higher
   - MySQL database (installed by docker-composer)
   - Maven

2. **Database Setup**:
   - Watch the docker composer explanation in the file `docker-and-docker-composer.md`

3. **Run the Application**:
   - Navigate to the project directory.
   - Run the following command to start the application:
     ```bash
     mvn spring-boot:run
     ```

4. **Testing the APIs**:
   - You can use `curl` or Postman.

## Example CURL Commands for Testing

- **Create a User**:
   ```bash
   curl -X POST http://localhost:8081/api/users       -H "Content-Type: application/json"       -d '{"name": "John", "lastname": "Doe", "hobbie": "Reading", "description": "A reader of mystery novels", "photo": null}'
   ```

- **Get All Users**:
   ```bash
   curl -X GET http://localhost:8081/api/users
   ```

- **Get a User by ID**:
   ```bash
   curl -X GET http://localhost:8081/api/users/1
   ```

- **Update a User**:
   ```bash
   curl -X PUT http://localhost:8081/api/users/1       -H "Content-Type: application/json"       -d '{"name": "Jane", "lastname": "Doe", "hobbie": "Traveling", "description": "A world traveler", "photo": null}'
   ```

- **Delete a User**:
   ```bash
   curl -X DELETE http://localhost:8081/api/users/1
   ```

## Technologies Used
- **Spring Boot**: For building and running the REST API
- **Spring Data JPA**: For database operations
- **MySQL**: Database to store user information
- **Maven**: For dependency management and build
- **Docker and Docker-composer**: For deploy the database

## Future Improvements
- Implement file upload for the `photo` field to support actual image uploads.
- Add frontend templates to enhance user experience.
- Include more validations on user inputs.
- Add the instruction of the maven project inside the Docker-composer file.

This project serves as a foundation for creating and managing user agendas and demonstrates core CRUD functionalities with Spring Boot.
