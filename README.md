# airbnb-clone-project
- [Team Roles](#TeamRoles)
- [Technology Stack](#TechnologyStack)
- [Database Design](#DatabseDesign)
  
👥 ## TeamRoles

The success of this Airbnb Clone Backend Project relies on a cross-functional team, each role bringing specific expertise to ensure the system is secure, scalable, and production-ready.

🔹 Backend Developer

Implements API endpoints (REST & GraphQL) for users, properties, bookings, payments, and reviews.

Designs and maintains database schemas and models in Django & PostgreSQL.

Develops core business logic, ensuring data integrity and consistency.

Works closely with the QA Engineer to resolve bugs and optimize performance.

🔹 Database Administrator (DBA)

Oversees database architecture, indexing, and query optimization.

Ensures data reliability, consistency, and security in PostgreSQL.

Manages backups, migrations, and database scaling strategies.

Collaborates with Backend Developers to fine-tune queries and caching mechanisms.

🔹 DevOps Engineer

Sets up CI/CD pipelines for automated testing and deployment.

Manages Docker containers and orchestrates deployment environments.

Monitors backend performance, uptime, and system health.

Implements security best practices and ensures scalability of backend services.

🔹 QA Engineer

Designs and executes test cases (unit, integration, and API tests).

Ensures the backend meets functional requirements and handles edge cases.

Automates regression testing for stable releases.

Works closely with the team to track and resolve defects before deployment.



## TechnologyStack

This project is built using the following technologies:

- **Django**: A high-level Python web framework used for building the RESTful API.  
- **Django REST Framework (DRF)**: Provides powerful tools for creating and managing RESTful APIs.  
- **PostgreSQL**: A robust relational database system used for reliable data storage and management.  
- **GraphQL**: Enables flexible and efficient querying of data, allowing clients to request only the data they need.  
- **Celery**: Handles asynchronous tasks such as sending notifications and processing background jobs.  
- **Redis**: Used for caching, message brokering, and session management to improve performance.  
- **Docker**: Ensures consistent development and deployment environments through containerization.  
- **CI/CD Pipelines**: Automates testing, building, and deployment of code changes for faster and more reliable releases.

## DatabseDesign
The database for the Airbnb Clone Project is designed to support core functionality such as user management, property listings, booking operations, reviews, and payments. Below is a breakdown of the key entities, their important fields, and relationships.

### Entities & Fields

#### 1. Users
- `id` (Primary Key) – unique identifier for each user
- `name` – full name of the user
- `email` – unique email address
- `password_hash` – securely stored password
- `role` – indicates if the user is a host, guest, or admin

#### 2. Properties
- `id` (Primary Key) – unique identifier for each property
- `user_id` (Foreign Key) – references the owner (host) from Users
- `title` – name/short description of the property
- `location` – address or city of the property
- `price_per_night` – cost of booking per night

#### 3. Bookings
- `id` (Primary Key) – unique identifier for each booking
- `user_id` (Foreign Key) – references the guest who made the booking
- `property_id` (Foreign Key) – references the booked property
- `start_date` – check-in date
- `end_date` – check-out date
- `status` – booking status (pending, confirmed, cancelled)

#### 4. Reviews
- `id` (Primary Key) – unique identifier for each review
- `user_id` (Foreign Key) – references the guest who left the review
- `property_id` (Foreign Key) – references the property being reviewed
- `rating` – numerical rating (e.g., 1–5)
- `comment` – text feedback from the user

#### 5. Payments
- `id` (Primary Key) – unique identifier for each payment
- `booking_id` (Foreign Key) – references the booking being paid for
- `amount` – total payment amount
- `payment_method` – e.g., credit card, PayPal
- `status` – payment status (pending, successful, failed)

---

### Relationships

- **Users → Properties**: One user (host) can list multiple properties.
- **Users → Bookings**: One user (guest) can create multiple bookings.
- **Properties → Bookings**: A property can have many bookings.
- **Bookings → Payments**: Each booking has one corresponding payment.
- **Properties → Reviews**: A property can have many reviews.
- **Users → Reviews**: A user can leave multiple reviews.

This relational structure ensures scalability, data integrity, and alignment with real-world Airbnb-like workflows.
