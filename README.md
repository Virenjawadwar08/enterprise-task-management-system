# 📋 Enterprise Task Management System

A full-stack task management system web application built with **React 19** on the frontend and **Spring Boot 3** on the backend. The system supports secure user authentication via JWT, full CRUD operations on personal todos.

---

## 🏗️ Project Structure

```
enterprise-task-management/
├── frontend/               # React 19 single-page application
│   ├── src/
│   │   ├── components/
│   │   │   └── todo/
│   │   │       ├── api/            # Axios API service clients
│   │   │       ├── security/       # Auth context & guards
│   │   │       ├── LoginComponent.jsx
│   │   │       ├── ListTodosComponent.jsx
│   │   │       ├── TodoComponent.jsx
│   │   │       ├── WelcomeComponent.jsx
│   │   │       ├── HeaderComponent.jsx
│   │   │       ├── FooterComponent.jsx
│   │   │       └── LogoutComponent.jsx
│   │   └── App.js
│   └── package.json
│
├── backend/                # Spring Boot 3 REST API
│   ├── src/main/java/
│   │   └── com/in28minutes/rest/webservices/
│   │       ├── todo/               # Todo entity, service, resource
│   │       ├── jwt/                # JWT config, token service & controller
│   │       ├── helloworld/         # Health check controller
│   │       └── basic/              # Basic auth config
│   ├── src/main/resources/
│   │   └── application.properties
│   └── pom.xml
│
├── .gitignore
└── README.md
```

---

## ✨ Features

- 🔐 **JWT Authentication** — Secure login with token-based session management
- ✅ **Todo CRUD** — Create, view, update, and delete personal tasks
- 📅 **Target Dates** — Assign due dates to each task using a date picker
- 👤 **Per-user Todos** — Each user sees only their own tasks
- 🔄 **REST API** — Clean RESTful endpoints consumed by the React frontend
- 📱 **Responsive UI** — Bootstrap 5 based responsive design
- ⚡ **Form Validation** — Formik-powered forms with validation on the frontend

---

## 🛠️ Tech Stack

### Frontend
| Technology | Version | Purpose |
|---|---|---|
| React | 19 | UI framework |
| React Router DOM | 7 | Client-side routing |
| Axios | 1.x | HTTP API calls |
| Bootstrap | 5.3 | UI styling |
| Formik | 2.x | Form handling & validation |
| Moment.js | 2.x | Date formatting |

### Backend
| Technology | Version | Purpose |
|---|---|---|
| Spring Boot | 3.2.5 | Application framework |
| Spring Security | 6.x | Authentication & authorization |
| Spring OAuth2 Resource Server | 6.x | JWT token validation |
| Spring Validation | 3.x | Request body validation |
| Java | 17 | Language |
| Maven | 3.x | Build tool |

---

## 🚀 Getting Started

### Prerequisites

Make sure you have the following installed:

- [Node.js](https://nodejs.org/) (v18 or above)
- [Java 17](https://adoptium.net/)
- [Maven](https://maven.apache.org/) (or use the included `mvnw` wrapper)
- [Git](https://git-scm.com/)

---

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/enterprise-task-management.git
cd enterprise-task-management
```

---

### 2. Run the Backend (Spring Boot)

```bash
cd backend
./mvnw spring-boot:run
```

The backend will start at: **http://localhost:8080**

> On Windows, use `mvnw.cmd spring-boot:run` instead.

---

### 3. Run the Frontend (React)

Open a **new terminal window**:

```bash
cd frontend
npm install
npm start
```

The frontend will start at: **http://localhost:3000**

---

## 🔌 API Endpoints

All endpoints are secured with JWT. Pass the token in the `Authorization: Bearer <token>` header.

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/authenticate` | Login and receive JWT token |
| `GET` | `/users/{username}/todos` | Get all todos for a user |
| `GET` | `/users/{username}/todos/{id}` | Get a specific todo |
| `POST` | `/users/{username}/todos` | Create a new todo |
| `PUT` | `/users/{username}/todos/{id}` | Update an existing todo |
| `DELETE` | `/users/{username}/todos/{id}` | Delete a todo |

---

## ⚙️ Configuration

Backend configuration is in `backend/src/main/resources/application.properties`:

```properties
# Logging
logging.level.org.springframework=info


# Basic Auth (uncomment to use basic auth instead of JWT)
# spring.security.user.name=in28minutes
# spring.security.user.password=dummy
```

Frontend API base URL is configured in `frontend/src/components/todo/api/ApiClient.js`:

```javascript
export const apiClient = axios.create({
    baseURL: 'http://localhost:8080'
});
```

---

## 📁 Key Frontend Components

| Component | Description |
|---|---|
| `LoginComponent` | Handles user login and token storage |
| `ListTodosComponent` | Displays all todos for the logged-in user |
| `TodoComponent` | Form to create or edit a todo |
| `WelcomeComponent` | Landing page after login |
| `AuthContext` | React context for global auth state |
| `TodoApiService` | Axios calls for all todo CRUD operations |
| `AuthenticationApiService` | Axios call for login/authentication |

---

## 🔒 Security

- Authentication is handled via **JWT (JSON Web Tokens)**
- Spring Security is configured with an OAuth2 Resource Server for token validation
- CORS is configured to allow requests from `http://localhost:3000`
- All `/users/**` routes are protected and require a valid JWT

---

## 🧪 Running Tests

### Backend Tests
```bash
cd backend
./mvnw test
```

### Frontend Tests
```bash
cd frontend
npm test
```

---

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch: `git checkout -b feature/your-feature-name`
3. Commit your changes: `git commit -m 'Add some feature'`
4. Push to the branch: `git push origin feature/your-feature-name`
5. Open a Pull Request

---

## 📄 License

This project is licensed under the MIT License.

---

> Built with ❤️ using React and Spring Boot
