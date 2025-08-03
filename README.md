# Personal-Library-Service

## Task 1: Endpoints

### Basic Endpoint

- **URL:** `http://localhost:8081/health`

- **Description:** Basic endpoint to test if the web server is running (implemented in `BasicController`).

- **Request Body:** None

- **Response:**

  ```
  OK
  ```

- **Example:**

  ```bash
  curl -X GET http://localhost:8081/health
  ```

- **Expected Response:**

  ```
  OK
  ```

---

### Greeting Service Endpoints

Test different greeting services for a given user.

---

#### 1. Morning Greeting

- **URL:** `http://localhost:8081/greet/morning/{user}`

- **Description:** Returns a morning greeting message from the `MorningGreetingService`.

- **Request Body:** None

- **Response:**

  ```
  Hello {user} From Morning Greeting Service!
  ```

- **Example:**

  ```bash
  curl -X GET http://localhost:8081/greet/morning/Seif
  ```

- **Expected Response:**

  ```
  Hello Seif From Morning Greeting Service!
  ```

---

#### 2. Evening Greeting

- **URL:** `http://localhost:8081/greet/evening/{user}`

- **Description:** Returns an evening greeting message from the `EveningGreetingService`.

- **Request Body:** None

- **Response:**

  ```
  Hello {user} From Evening Greeting Service!
  ```

- **Example:**

  ```bash
  curl -X GET http://localhost:8081/greet/evening/Ahmed
  ```

- **Expected Response:**

  ```
  Hello Ahmed From Evening Greeting Service!
  ```

---

#### 3. Default Greeting

- **URL:** `http://localhost:8081/greet/default/{user}`

- **Description:** Returns a default greeting message. The default service is `MorningGreetingService` (annotated with `@Primary`).

- **Request Body:** None

- **Response:**

  ```
  Hello {user} From Morning Greeting Service!
  ```

- **Example:**

  ```bash
  curl -X GET http://localhost:8081/greet/default/Mona
  ```

- **Expected Response:**

  ```
  Hello Mona From Morning Greeting Service!
  ```
  ---
  
### Notification Service Endpoints
Test different notification services for sending messages.

---

#### 1. Email Notification (Primary Service)

- **URL:** `http://localhost:8081/notify/email`

- **Description:**  Sends a notification message using the primary EmailNotificationService `annotated with @Primary.`

- **Request Body:** None

- **Response:**

```
Email Notification Sent: Hello from Email!
```

- **Example**

```bash
curl -X GET http://localhost:8081/notify/email
```

- **Expected Response**

```text
Email Notification Sent: Hello from Email!
```

---

#### 2. SMS Notification 

- **URL:** `http://localhost:8081/notify/sms`

- **Description:**  Sends a notification message using the SmsNotificationService`annotated with @Qualifier("sms")).`

- **Request Body:** None

- **Response:**

```
SMS Notification Sent: Hello from SMS!
```

- **Example**

```bash
curl -X GET http://localhost:8081/notify/sms
```

- **Expected Response**

```text
SMS Notification Sent: Hello from SMS!
```

---

### Personal Library Service

A Spring Boot service for managing a personal library with greeting and notification services.

#### API Endpoints

##### Basic Endpoint

- **URL:** `http://localhost:8081/health`
- **Description:** Basic endpoint to test if the web server is running.
- **Request Body:** None
- **Response:** `OK`
- **Example:**
  ```bash
  curl -X GET http://localhost:8081/health
    ```
### Book Management Endpoints

#### 1. Get All Books
- **URL:** `http://localhost:8081/books`
- **Method:** GET
- **Description:** Returns all books in the library.
- **Response:** Array of Book objects
- **Example:**
  ```bash
  curl -X GET http://localhost:8081/books
    ```

#### 2. Get Book by ID
- **URL:** `http://localhost:8081/books/{id}`
- **Method:** GET
- **Description:** Returns a specific book by its ID.
- **Response:** Book object
- **Example:**
  ```bash
  curl -X GET http://localhost:8081/books/1
    ```

#### 3. Add a New Book
- **URL:** `http://localhost:8081/books`
- **Method:** POST
- **Description:** Adds a new book to the library.
- **Request Body:** Book object (JSON)
- **Example:**
  ```bash
  curl -X POST http://localhost:8081/books \
  -H "Content-Type: application/json" \
  -d '{
    "title": "The Great Gatsby",
    "author": "F. Scott Fitzgerald",
    "genre": "Classic",
    "publisher": "Scribner",
    "copiesAvailable": 5
  }'
    ```

#### 4. Update a Book
- **URL:** `http://localhost:8081/books/{id}`
- **Method:** PUT
- **Description:** Updates an existing book.
- **Request Body:** Updated Book object (JSON)
- **Example:**
  ```bash
  curl -X PUT http://localhost:8081/books/1 \
  -H "Content-Type: application/json" \
  -d '{
    "title": "The Great Gatsby (Updated)",
    "author": "F. Scott Fitzgerald",
    "genre": "Classic Literature",
    "publisher": "Scribner",
    "copiesAvailable": 3
  }'
    ```

#### 5. Delete a Book
- **URL:** `http://localhost:8081/books/{id}`
- **Method:** DELETE
- **Description:** Deletes a book from the library.
- **Example:**
  ```bash
  curl -X DELETE http://localhost:8081/books/1
    ```
