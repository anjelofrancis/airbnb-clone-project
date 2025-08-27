# airbnb-clone-project

## **Overview**

The Airbnb Clone Project is a full-stack web application designed to replicate the core functionalities of the Airbnb platform. It provides a robust and scalable backend system to manage user interactions, property listings, bookings, payments, and reviews, ensuring a seamless experience for both guests and hosts. This project serves as a practical exercise in backend development, database design, API creation, and modern software development practices.


## **Project Goals**

- ***User Management***: Implement secure user registration, authentication, and profile management.
- ***Property Management***: Enable hosts to create, update, and manage property listings.
- ***Booking System***: Facilitate property reservations and manage booking details.
- ***Payment Processing***: Handle secure payment transactions for bookings.
- ***Review System***: Allow users to post and view reviews for properties.
- ***Data Optimisation***: Ensure efficient data retrieval and storage through database optimisations.


## **Team Roles**

- ***Backend Developer***: Designs and implements API endpoints, develops business logic, and integrates with the database to support user, property, booking, payment, and review functionalities. Ensures the backend is secure, scalable, and maintainable.
- ***Database Administrator***: Designs and optimises the PostgreSQL database schema, implements indexing strategies, and manages data integrity. Focuses on performance tuning and scalability to efficiently handle large datasets.
- ***DevOps Engineer***: Configures and manages deployment pipelines using Docker and CI/CD tools like GitHub Actions. Monitors backend services, ensures scalability, and maintains a consistent development and production environment.
- ***QA Engineer***: Develops and executes test plans to validate backend functionalities, including API endpoints and database operations. Ensures the system meets quality standards through rigorous testing and bug identification.


## **Technology Stack**

- ***Django***: A high-level Python web framework used for building the RESTful API, providing a robust structure for handling requests, routing, and business logic.
- ***Django REST Framework***: A toolkit for creating and managing RESTful APIs, enabling CRUD operations for user, property, booking, and review data.
- ***PostgreSQL***: A powerful relational database used for storing and managing application data, such as user profiles, property listings, and booking records.
- ***GraphQL***: A query language that allows flexible and efficient data retrieval, enabling clients to request exactly the data they need from the backend.
- ***Celery***: A distributed task queue for handling asynchronous tasks, such as sending notifications or processing payments, to improve performance and user experience.
- ***Redis***: A fast in-memory data store used for caching frequently accessed data and managing user sessions to reduce database load.
- ***Docker***: A containerization tool that ensures consistent development, testing, and deployment environments across different systems.
- ***GitHub Actions***: Automated pipelines (e.g., using GitHub Actions) for continuous integration and deployment, enabling efficient testing and rollout of code changes.


## **Database Design**

The database is designed to support the core functionalities of the Airbnb Clone Project using PostgreSQL. Below are the key entities, their important fields, and their relationships.

### ***Key Entities**

- **Users**
    - *Fields*
        - `user-id`: Unique identifier for each user (Primary Key).
        - `email`: User's email address for authentication and communication.
        - `name`: Full name of the user for profile display.
        - `password_hash`: Securely hashed password for user authentication.
        - `created_at`: Timestamp of when the user account was created.
    - *Description* 
