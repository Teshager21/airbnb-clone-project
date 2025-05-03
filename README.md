# 🏡 Airbnb Clone
The backend for the Airbnb Clone project is designed to provide a robust and scalable foundation for managing user interactions, property listings, bookings, and payments. This backend will support various functionalities required to mimic the core features of Airbnb, ensuring a smooth experience for users and hosts.

## 👥 Team Roles
| Name              | Role                          | Responsibilities                                  |
|-------------------|-------------------------------|--------------------------------------------------|
| Teshager Admasu       | 🧠 Project Lead / Full Stack Dev | Architecture, backend API, database, deployment |
| Teammate      | ⚙️ Backend Developer           | RESTful APIs, authentication, data modeling      |
| Teammate      | 🎨 UI/UX Designer              | Design mockups, responsive layout, styling       |
| Teammate      | 🌐 Frontend Developer          | React components, routing, integration           |
| Teammate      | 🧪 QA Engineer                 | Test coverage, bug tracking, performance testing |
| Teammate      |🚀 DevOps Engineer              | CI/CD pipelines, infrastructure, cloud deployment |

---

## 🛠️ Technology Stack Overview

**Frontend:**
- React / Next.js
- Tailwind CSS
- Axios

**Backend:**
- Django: A high-level Python web framework used for building the RESTful API.
- Django REST Framework: Provides tools for creating and managing RESTful APIs.
- PostgreSQL: A powerful relational database used for data storage.
- GraphQL: Allows for flexible and efficient querying of data.
- Celery: For handling asynchronous tasks such as sending notifications or processing payments.
- Redis: Used for caching and session management.
- Docker: Containerization tool for consistent development and deployment environments.
- CI/CD Pipelines: Automated pipelines for testing and deploying code changes.

**Other:**
- Cloudinary (image uploads)
- Google Maps API / Leaflet
- Stripe (payment integration)

---

## 🗃️ Database Design

**1. Users:**

| Field         | Description                        |
|---------------|------------------------------------|
| `id`          | Unique identifier (Primary Key)    |
| `name`        | Full name                          |
| `email`       | Unique user email                  |
| `password`    | Hashed password                    |
| `role`        | Guest, Host, or Admin              |


***🔁 Relationships:***

- A user can create multiple properties
- A user can make multiple bookings
- A user can leave multiple reviews
- A user can make multiple payments

**2. Properties:**

| Field         | Description                        |
|---------------|------------------------------------|
| `id`          | Unique identifier (Primary Key)    |
| `title`       | Property title                     |
| `description` | Details about the property         |
| `location`    | Address or coordinates             |
| `price`       | Per-night price                    |
| `user_id`     | Foreign Key → Users (host owner)   |

***🔁 Relationships:***

- A property belongs to one user (host)
- 
- A property can have many bookings
- 
- A property can have many reviews

**3. Bookings**

| Field         | Description                        |
|---------------|------------------------------------|
| `id`          | Unique identifier (Primary Key)    |
| `user_id`     | Foreign Key → Users (guest)        |
| `property_id` | Foreign Key → Properties           |
| `start_date`  | Check-in date                      |
| `end_date`    | Check-out date                     |
| `total_price` | Total calculated cost              |

***🔁 Relationships:***

- Each booking is made by one user

- Each booking is for one property

**4. Reviews**

| Field         | Description                        |
|---------------|------------------------------------|
| `id`          | Unique identifier (Primary Key)    |
| `user_id`     | Foreign Key → Users                |
| `property_id` | Foreign Key → Properties           |
| `rating`      | Score out of 5                     |
| `comment`     | Optional text review               |

***🔁 Relationships:***

- A user can leave one review per booking

- A property can have many reviews

**5. Payments**
| Field         | Description                        |
|---------------|------------------------------------|
| `id`          | Unique identifier (Primary Key)    |
| `user_id`     | Foreign Key → Users (payer)        |
| `booking_id`  | Foreign Key → Bookings             |
| `amount`      | Payment amount                     |
| `status`      | Paid / Pending / Failed            |
| `method`      | Stripe / Credit Card / PayPal      |

***🔁 Relationships:***

- Each payment is linked to one booking

- Each payment is made by one user

---

## 🚀 Feature Breakdown

- 🔐 User Authentication (Sign up, Login, Logout)
- 🏘️ Browse available properties
- 🗺️ Location-based search with map integration
- 🗓️ Book and manage reservations
- 🏠 Host dashboard to manage listings
- 💬 Messaging between hosts and guests
- 🌙 Responsive design for all devices

---

## 🔐 API Security
Ensuring the security of this application's API is crucial for protecting sensitive user data, managing access control, and maintaining trust in the platform.

**✅ Key Security Measures**
1. Authentication
    - Uses JWT (JSON Web Tokens) to authenticate users.

    - Tokens are issued upon login and must be included in all protected requests.

    - Ensures that only verified users can access their data or perform actions.

2. Authorization
    - Role-based access control (RBAC) implemented:

    - Guests can book properties.

    - Hosts can manage listings.

    - Admins can moderate platform content.

    - Prevents users from accessing or modifying unauthorized resources.

3. Rate Limiting
    - Limits the number of requests a user/IP can make in a given timeframe.

    - Protects the API from brute-force attacks and abuse.

4. Input Validation & Sanitization
    - All incoming data is validated (e.g., using Joi, Zod).

    - Prevents SQL injection, XSS, and malformed request payloads.

5. HTTPS Enforcement
    - Ensures that all data in transit is encrypted.

    - Protects sensitive information (like passwords, payment data) from being intercepted.

6. Secure Payment Integration
    - Uses trusted third-party payment processors like Stripe.

    - Sensitive payment details are never stored on our servers.

## 🚀 CI/CD Pipeline

Continuous Integration (CI) and Continuous Deployment/Delivery (CD) are essential practices in modern software development. CI/CD pipelines automate the process of building, testing, and deploying code, enabling faster and more reliable software releases.

---

### 🧠 Why It’s Important

Implementing a CI/CD pipeline ensures that:

✅ Code changes are automatically tested and validated  
✅ Bugs are detected early in the development cycle  
✅ Deployments are consistent, repeatable, and faster  
✅ The development workflow becomes more efficient and less error-prone  

---

### 🛠️ Tools We Use

This project can leverage the following tools for setting up and managing the CI/CD pipeline:

- ⚙️ **GitHub Actions** – Automates workflows like testing and deployment on every push or pull request  
- 🐳 **Docker** – Containerizes the app to ensure consistent environments across development, testing, and production  
- 📦 **Docker Hub** / **GitHub Container Registry** – Stores and distributes Docker images  
- ☁️ *(Optional)* **Terraform**, **Ansible**, **AWS**, **GCP**, **Azure Pipelines** – For infrastructure provisioning and cloud deployment  

---

