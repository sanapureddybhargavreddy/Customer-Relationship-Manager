# Spring Boot MVC CRM CRUD Application

## Overview
This is a Spring Boot web application that implements a Customer Relationship Management (CRM) system. It provides full CRUD (Create, Read, Update, Delete) capabilities for managing Customer records.

The application follows the classic Model-View-Controller (MVC) architecture using Spring MVC, Spring Data JPA for database interactions, and JavaServer Pages (JSP) for the frontend views.

## Features
- **View Customers:** View a list of all current customers in the system.
- **Add Customer:** Add new customers with their first name, last name, and email.
- **Update Customer:** Edit existing customer details.
- **Delete Customer:** Remove a customer from the database.

## Architecture & Technologies Used
- **Language:** Java (JDK 8)
- **Framework:** Spring Boot 2.7.11
- **Web Layer:** Spring Web MVC
- **Database Access:** Spring Data JPA / Hibernate
- **Database:** MySQL
- **View Layer:** JSP (JavaServer Pages), JSTL, Tomcat Embed Jasper
- **Boilerplate Reduction:** Lombok

## Project Structure
- `in.ineuron.model`: Contains the `Customer` JPA Entity mapping to the `customer` database table.
- `in.ineuron.controller`: Contains the `CustomerController` that handles web requests (`/customer/list`, `/customer/showForm`, etc.) and routes them to JSP views.
- `in.ineuron.service`: Contains business logic and acts as an intermediary between the Controller and DAO layers. 
- `in.ineuron.dao`: Contains the repository (Interface `ICustomerDAO`) for database operations.
- `src/main/webapp/WEB-INF/pages`: Contains JSP views (`customer-form.jsp`, `list-customers.jsp`, `index.jsp`).

## Requirements

### Prerequisites
- **Java:** JDK 8 or higher
- **Maven:** For building the project and resolving dependencies
- **Database:** MySQL Server installed and running locally
- **IDE:** Eclipse, IntelliJ IDEA, or VS Code (optional but recommended)

### Database Configuration
Before running the application, you need to configure your MySQL database connection.
Create a database named `players` or update the database name in the configuration. 

In `src/main/resources/application.properties`, configure the following properties according to your local MySQL setup:

```properties
# DataSource configuration
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
spring.datasource.url=jdbc:mysql:///players
spring.datasource.username=root
spring.datasource.password=your_mysql_password

# JPA / Hibernate configuration
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
spring.jpa.database-platform=org.hibernate.dialect.MySQL8Dialect
```
*(Note: Change `9676171521` or `your_mysql_password` to your actual MySQL root password).*

## How to Run

1. Clone or download the repository to your local machine.
2. Ensure your MySQL server is running.
3. Open a terminal or command prompt in the project's root directory.
4. Clean and build the project using Maven:
   ```bash
   mvn clean install
   ```
5. Run the Spring Boot application:
   ```bash
   mvn spring-boot:run
   ```
6. Alternatively, you can run the application directly from your IDE by executing the `BootMvcProj8MvcCrmCrudappApplication.java` main class.
7. Once the application starts on `server.port=8080`, open your web browser and navigate to:
   ```
   http://localhost:8080/CRM/customer/list
   ```

## API Endpoints (Controller Mappings)
- `GET /CRM/customer/list`: Displays all customers.
- `GET /CRM/customer/showForm`: Shows the form to add a new customer.
- `POST /CRM/customer/saveCustomer`: Saves customer data to the database.
- `GET /CRM/customer/showFormForUpdate?customerId={id}`: Shows the form pre-filled with the customer data for updating.
- `GET /CRM/customer/showFormForDelete?customerId={id}`: Deletes the selected customer.
