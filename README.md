# 📓 Journal App

A full-stack **personal journaling REST API** built with Spring Boot, MongoDB, and Spring Security. Users can securely create, manage, and retrieve their journal entries — with JWT-based authentication, Redis caching, async event processing via Kafka, and email notifications.

---

## 🚀 Features

- User registration and login with **JWT authentication**
- Create, read, update, and delete personal journal entries
- Entries are private — users can only access their own data
- **Redis** caching for faster reads
- **Kafka** for async event-driven features (e.g. welcome emails)
- **Email notifications** via JavaMailSender
- Full test coverage with **JUnit** and integration tests
- Code quality analysis with **SonarQube**

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Language | Java 17 |
| Framework | Spring Boot 3.x |
| Database | MongoDB |
| ORM | Spring Data JPA / MongoRepository |
| Security | Spring Security + JWT |
| Caching | Redis |
| Messaging | Apache Kafka |
| Email | JavaMailSender (SMTP) |
| Testing | JUnit 5 · Mockito · Integration Tests |
| Code Quality | SonarQube |
| Build Tool | Maven |
| IDE | IntelliJ IDEA |

---

## 📁 Project Structure

```
journalApp/
├── src/
│   ├── main/
│   │   ├── java/com/example/journalapp/
│   │   │   ├── controller/       # REST controllers
│   │   │   ├── service/          # Business logic
│   │   │   ├── repository/       # MongoDB repositories
│   │   │   ├── model/            # Entity / document classes
│   │   │   ├── security/         # JWT filter, Spring Security config
│   │   │   ├── kafka/            # Kafka producer & consumer
│   │   │   └── config/           # Redis, Mail, App config
│   │   └── resources/
│   │       └── application.properties
│   └── test/
│       └── java/com/example/journalapp/
│           ├── controller/       # API integration tests
│           └── service/          # Unit tests
├── pom.xml
└── README.md
```

---

## ⚙️ Getting Started

### Prerequisites

- Java 17+
- Maven 3.8+
- MongoDB (local or Atlas)
- Redis (local or cloud)
- Apache Kafka (optional, for async features)
- IntelliJ IDEA (recommended)

### Installation

```bash
# Clone the repository
git clone https://github.com/your-username/journalApp.git
cd journalApp

# Configure environment
# Edit src/main/resources/application.properties with your DB and mail credentials

# Build the project
mvn clean install

# Run the application
mvn spring-boot:run
```

The API will start at `http://localhost:8080`.

---

## 🔐 Authentication

This app uses **JWT (JSON Web Tokens)** for stateless authentication.

1. Register a new user via `POST /api/auth/register`
2. Login via `POST /api/auth/login` — returns a JWT token
3. Include the token in the `Authorization` header for protected routes:

```
Authorization: Bearer <your_token>
```

---

## 📡 API Endpoints

### Auth

| Method | Endpoint | Description |
|---|---|---|
| POST | `/api/auth/register` | Register a new user |
| POST | `/api/auth/login` | Login and receive JWT |

### Journal Entries

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/journal` | Get all entries for logged-in user |
| GET | `/api/journal/{id}` | Get a specific entry |
| POST | `/api/journal` | Create a new entry |
| PUT | `/api/journal/{id}` | Update an entry |
| DELETE | `/api/journal/{id}` | Delete an entry |

> All journal endpoints require a valid JWT token.

---

## 🧪 Running Tests

```bash
# Run all tests
mvn test

# Run with coverage report
mvn test jacoco:report
```

---

## 📊 Code Quality (SonarQube)

```bash
mvn sonar:sonar \
  -Dsonar.host.url=http://localhost:9000 \
  -Dsonar.login=your_sonar_token
```

---

## 📬 Email Notifications

The app sends email notifications (e.g. on registration) using JavaMailSender. Configure SMTP credentials in `application.properties`:

```properties
spring.mail.host=smtp.gmail.com
spring.mail.port=587
spring.mail.username=your_email@gmail.com
spring.mail.password=your_app_password
```

---

## 📦 application.properties (sample)

```properties
# MongoDB
spring.data.mongodb.uri=mongodb://localhost:27017/journaldb

# JWT
jwt.secret=your_secret_key
jwt.expiration=86400000

# Redis
spring.redis.host=localhost
spring.redis.port=6379

# Kafka
spring.kafka.bootstrap-servers=localhost:9092

# Mail
spring.mail.host=smtp.gmail.com
spring.mail.port=587
spring.mail.username=your_email@gmail.com
spring.mail.password=your_app_password
spring.mail.properties.mail.smtp.auth=true
spring.mail.properties.mail.smtp.starttls.enable=true
```

---

## 🤝 Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

---

## 📄 License

This project is licensed under the MIT License.
