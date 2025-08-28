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

### ***Key Entities***

- **Users**
    - *Fields*
        - `user-id`: Unique identifier for each user (Primary Key).
        - `email`: User's email address for authentication and communication.
        - `name`: Full name of the user for profile display.
        - `password_hash`: Securely hashed password for user authentication.
        - `created_at`: Timestamp of when the user account was created.
    - *Description* - Stores details of properties available for booking.

- **Properties**
    - *Fields*
        - `property_id`: Unique identifier for each property (Primary Key).
        - `host_id`: References the user who owns the property (Foreign Key to Users).
        - `title`: Descriptive title of the property listing.
        - `location`: Address or coordinates of the property.
        - `price_per_night`: Cost of renting the property per night.
    - *Description* - Stores details of properties available for booking.
- **Bookings**
    - *Fields*
        - `booking_id`: Unique identifier for each booking (Primary Key).
        - `property_id`: References the booked property (Foreign Key to Properties).
        - `user_id`: References the user making the booking (Foreign Key to Users).
        - `check_in_date`: Start date of the booking.
        - `check_out_date`: End date of the booking.
    - *Description* - Manages reservation details for properties.
- **Payments**
    - *Fields*
        - `payment_id`: Unique identifier for each payment (Primary Key).
        - `booking_id`: References the associated booking (Foreign Key to Bookings).
        - `amount`: Total payment amount for the booking.
        - `payment_status`: Status of the payment (e.g., pending, completed, failed).
        - `created_at`: Timestamp of when the payment was processed.
    - *Description* - Tracks payment transactions related to bookings.
- **Reviews**
    - *Fields*
        - `review_id`: Unique identifier for each review (Primary Key).
        - `property_id`: References the reviewed property (Foreign Key to Properties).
        - `user_id`: References the user who wrote the review (Foreign Key to Users).
        - `rating`: Numerical rating (e.g., 1-5) for the property.
        - `comment`: Textual feedback about the property.
    - *Description* - Stores user reviews and ratings for properties.

### **Entity Relationships**

- **Users to Properties**: A user (host) can own multiple properties, but each property is associated with only one host (One-to-Many).
- **Users to Bookings**: A user (guest) can make multiple bookings, but each booking is made by only one user (One-to-Many).
- **Properties to Bookings**: A property can have multiple bookings, but each booking is associated with only one property (One-to-Many).
- **Bookings to Payments**: Each booking can have one associated payment, and each payment is linked to a single booking (One-to-One).
- **Properties to Reviews**: A property can have multiple reviews, but each review is associated with only one property (One-to-Many).
- **Users to Reviews**: A user can write multiple reviews, but each review is written by only one user (One-to-Many).



## **Feature Breakdown**

- **User Management**: Enables secure registration, authentication, and profile management for users. This feature ensures that guests and hosts can create accounts, log in securely, and update their personal information, forming the foundation for user interactions in the platform.
- **Property Management**: Allows hosts to create, update, and delete property listings with details like location and price. This feature empowers hosts to manage their offerings, making properties available for guests to browse and book.
- **Booking System**: Facilitates the reservation of properties by users, including managing check-in and check-out dates. It ensures a smooth process for guests to secure accommodations and for hosts to track their bookings.
- **Payment Processing**: Handles secure payment transactions for bookings, recording payment details and status. This feature ensures seamless and trustworthy financial interactions between guests and the platform.
- **Review System**: Enables users to post ratings and comments for properties they’ve stayed at. This fosters trust and transparency by allowing guests to share feedback and helping others make informed booking decisions.
- **Data Optimisation**: Implements indexing and caching strategies to enhance database performance. This ensures fast data retrieval and a responsive user experience, even with large datasets.



## **API Security**

### **Key Security Measures**

- **Authentication**: Implements JSON Web Tokens (JWT) for secure user authentication, requiring users to provide valid credentials to access protected API endpoints. This ensures only registered users can interact with the system.
- **Authorisation**: Utilises role-based access control (RBAC) to restrict access to resources based on user roles (e.g., guest, host, admin). This prevents unauthorised users from modifying properties, bookings, or sensitive data.
- **Rate Limiting**: Enforces API request limits per user to prevent abuse and denial-of-service (DoS) attacks. This is implemented using Redis to track and throttle requests, ensuring system availability.
- **Data Encryption**: Employs HTTPS for all API communications and encrypts sensitive data (e.g., passwords, payment details) at rest using industry-standard algorithms. This protects data integrity and confidentiality during transmission and storage.
- **Input Validation and Sanitisation**: Validates and sanitises all user inputs to prevent SQL injection, cross-site scripting (XSS), and other injection attacks. This ensures the integrity of data processed by the backend.

### **Importance of Security**

- **Protecting User Data**: Secure authentication and encryption safeguard sensitive user information, such as emails and passwords, preventing unauthorised access and data breaches that could erode user trust.
- **Securing Payments**: Robust encryption and validation for payment processing protect financial transactions, ensuring user funds and payment details remain confidential and secure from fraud.
- **Preventing Unauthorised Access**: Authorisation controls ensure that only authorised users can manage properties, bookings, or reviews, maintaining the integrity of user and host interactions.
- **Ensuring System Availability**: Rate limiting and input validation protect the API from abuse and malicious attacks, ensuring consistent performance and availability for all users.
- **Maintaining Trust and Transparency**: Secure handling of reviews and data ensures that feedback remains authentic and trustworthy, fostering confidence in the platform’s review system.



## **CI/CD Pipeline**

### **Overview**

Continuous Integration and Continuous Deployment (CI/CD) pipelines automate the process of testing, building, and deploying code changes to ensure a reliable and efficient development workflow. They are crucial for the Airbnb Clone Project as they enable rapid iteration, reduce manual errors, and ensure that new features and bug fixes are consistently tested and deployed to production with minimal downtime.

### **Importance**

CI/CD pipelines enhance code quality by running automated tests on every code commit, catching issues early in the development cycle. They also streamline deployments by automating the process of building and deploying Docker containers, ensuring consistency across development, testing, and production environments.

### **Tools Used**

- **GitHub Actions**: Automates testing and deployment workflows, running unit tests, integration tests, and linting on every code push or pull request.
- **Docker**: Packages the application and its dependencies into containers, ensuring consistent environments across development, testing, and production.
- **PostgreSQL**: Used in the CI/CD pipeline for integration testing to validate database interactions in a controlled environment.
- **Redis**: Supports testing of caching mechanisms during the CI process to ensure performance optimisations work as expected.
