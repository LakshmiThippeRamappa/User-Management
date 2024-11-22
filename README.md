# User Management Application

A web-based CRUD application for managing user data (create, read, update, delete). The application is built using Java Servlets, JSP, JSTL, and MySQL for the backend, and Bootstrap for the frontend.

## Features

- List all users with pagination.
- Add a new user with details (name, email, country).
- Edit user details.
- Delete users.
- Basic error handling.

## Requirements

### Software Dependencies

1. **Java Development Kit (JDK)** - Version 8 or later.
2. **Apache Tomcat** - Version 8.0 or later.
3. **MySQL Database** - Version 8 or later.
4. **MySQL Connector for Java** - Version 8.0.13 (jar included in the project).

### Required JARs

The following JARs are necessary to run the project:

- `jsp-api-2.2.jar`
- `jstl-1.2.jar`
- `mysql-connector-java-8.0.13.jar`
- `servlet-api-2.5.jar`

Add these libraries to your project classpath.

## Setup Instructions

### 1. Database Setup

1. Open your MySQL client and create a new database:

    ```sql
    CREATE DATABASE userdb;
    ```

2. Use the following schema for the `users` table:

    ```sql
    CREATE TABLE users (
        id INT AUTO_INCREMENT PRIMARY KEY,
        name VARCHAR(100) NOT NULL,
        email VARCHAR(100) NOT NULL,
        country VARCHAR(100) NOT NULL
    );
    ```

3. Update the credentials in the `UserDAO.java` file:

    ```java
    private String jdbcURL = "jdbc:mysql://localhost:3306/userdb?useSSL=false";
    private String jdbcUsername = "your_mysql_username";
    private String jdbcPassword = "your_mysql_password";
    ```

### 2. Deploying the Application

1. **Clone the repository** or copy the project files to your local machine.
2. **Open the project in your IDE** (Eclipse).
3. **Add dependencies**: Ensure all required JARs are included in the build path.
4. **Configure Apache Tomcat**:
   - Add the project to Tomcat Server in your IDE.
   - Deploy the application.
5. Start the Tomcat Server.

## Project Structure

UserManagementApp/
│
├── src/main/java/com/usermanagement/
│   ├── dao/                  # Data Access Object (DAO) classes
│   │   └── UserDAO.java
│   ├── model/                # POJO classes
│   │   └── User.java
│   └── web/                  # Servlet classes
│       └── UserServlet.java
│
├── WebContent/
│   ├── user-form.jsp         # JSP file for add/edit forms
│   ├── user-list.jsp         # JSP file for listing users
│   ├── Error.jsp             # JSP file for error handling
│   └── WEB-INF/
│       └── web.xml           # Servlet mappings
│
├── lib/                      # Required JARs
├── README.md                 # Project documentation



## Technologies Used

### Backend
- **Java Servlet** - To handle HTTP requests and responses.
- **JSP & JSTL** - For rendering dynamic views.
- **MySQL** - Relational database for storing user data.

### Frontend
- **Bootstrap 4** - CSS framework for responsive UI design.

### Server
- **Apache Tomcat** - Web server to run the application.

## API Endpoints

| Action         | HTTP Method | URL             | Description           |
|----------------|-------------|-----------------|-----------------------|
| List Users     | GET         | `/list`         | View all users.       |
| Show Add Form  | GET         | `/new`          | Show "Add User" form. |
| Insert User    | POST        | `/insert`       | Add a new user.       |
| Show Edit Form | GET         | `/edit?id=<id>` | Show "Edit User" form.|
| Update User    | POST        | `/update`       | Update user details.  |
| Delete User    | GET         | `/delete?id=<id>` | Delete a user.        |

## Troubleshooting

- **ClassNotFoundException (MySQL Driver)**  
  Ensure the `mysql-connector-java-8.0.13.jar` is in your project’s classpath.
  
- **Database Connection Error**  
  Verify the JDBC URL, username, and password in `UserDAO.java`.

- **404 Error**  
  Ensure the servlet mappings in `web.xml` are correct and that Tomcat is configured properly.

## Future Improvements

- Add user authentication and role-based access.
- Implement pagination for the user list.
- Validate user inputs on the client-side.
- Add logging and monitoring.
