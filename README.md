# CINE_FLOW
CineFlow v2 is a JavaFX-based multiplex management system built with Java 21 and MySQL. It features personalized movie recommendations, smart seat allocation, automated waitlists, secure QR-code ticketing, dynamic pricing, and an admin dashboard for managing bookings, shows, and revenue analytics.
# 🎬 CineFlow v2 – Multiplex Movie Ticket Reservation System

CineFlow v2 is a desktop application for managing multiplex movie ticket reservations, built using **Java 21, JavaFX 21, Maven, and MySQL 8.x** with JDBC.

It combines a modern glassmorphic user interface with intelligent booking features, automated processes, secure digital ticketing, and administrative tools.

## ✨ Key Features

### 1. Personalized Movie Recommendations
- Recommends movies based on genre, language, ratings, and user preferences.
- Uses exponential recency decay and composite scoring.
- Applies diversity ranking to avoid repetitive recommendations.
- Provides explainable recommendations such as "Because you loved Interstellar."

### 2. Smart Seat Allocation
- Automatically suggests the best available seats.
- Considers screen distance, viewing angle, seat category, and user preferences.
- Supports group seating through contiguous seat selection.
- Avoids leaving isolated empty seats.

### 3. Automated FIFO Waitlist System
- Maintains a First-In-First-Out (FIFO) waiting queue.
- Automatically reallocates seats when bookings are cancelled.
- Uses temporary 10-minute seat holds.
- Sends in-app notifications when seats become available.

### 4. Secure QR Code Ticketing
- Generates digital tickets using QR codes.
- Uses HMAC-SHA256 signatures to prevent ticket tampering.
- Provides an entry gate validation system.
- Prevents duplicate admissions through atomic ticket validation.

### 5. Dynamic Pricing System
- Adjusts ticket prices based on seat occupancy, showtime, and demand.
- Supports configurable pricing rules and discounts.
- Uses locked price quotes during checkout.
- Includes an interactive pricing simulator for administrators.

### 6. Admin Dashboard
- Manage movies, screens, and showtimes.
- Monitor bookings and waitlists.
- View revenue and occupancy reports.
- Manage pricing rules and validate digital tickets.

---

## 🛠️ Technology Stack

| Component | Technology |
|---|---|
| Programming Language | Java 21 |
| Frontend | JavaFX 21 |
| Database | MySQL 8.x |
| Database Connectivity | JDBC |
| Build Tool | Apache Maven |
| QR Code Generation | ZXing 3.5.3 |
| Testing Framework | JUnit 5 |
| Styling | JavaFX CSS |

## 🏗️ Architecture

The application follows a layered architecture:

- **Model Layer:** Represents application entities such as users, movies, bookings, seats, and tickets.
- **DAO Layer:** Handles database operations using JDBC and prepared statements.
- **Service Layer:** Implements business logic, including booking, recommendations, pricing, and seat allocation.
- **UI Layer:** Provides the JavaFX desktop interface.

The application uses MySQL with the InnoDB storage engine for transactional database operations.

---

## 🚀 Installation and Setup

### Prerequisites

Make sure the following are installed:

- Java Development Kit (JDK 21)
- Apache Maven 3.8+
- MySQL Server 8.x

### 1. Clone the Repository

```bash
git clone <your-repository-url>
cd CineFlow-v2
```

### 2. Set Up the Database

Start your MySQL server and execute:

```bash
mysql -u root -p < database/schema.sql
mysql -u root -p < database/seed_data.sql
```

This creates the `cineflow_db` database and loads the sample data.

### 3. Configure Database Credentials

Copy `db.properties.example` to `db.properties` and update your MySQL credentials:

```properties
db.url=jdbc:mysql://localhost:3306/cineflow_db?useSSL=false&allowPublicKeyRetrieval=true&serverTimezone=Asia/Kolkata&characterEncoding=UTF-8
db.user=root
db.password=YOUR_MYSQL_PASSWORD
```

For Razorpay integration, configure the required API credentials in your private `db.properties` file.

**Important:** Never commit your actual database passwords or API secrets to GitHub.

### 4. Run Tests

```bash
mvn clean compile test
```

### 5. Launch the Application

```bash
mvn javafx:run
```

---

## 🎯 Project Objective

The main objective of CineFlow v2 is to develop an intelligent and user-friendly multiplex management system that goes beyond traditional movie ticket booking.

By integrating personalized recommendations, smart seat allocation, automated waitlist management, secure QR ticket validation, and dynamic pricing, the application demonstrates the practical implementation of object-oriented programming, database management, algorithms, concurrency, and application security.

---

## 📂 Project Structure

```text
CineFlow-v2/
│
├── database/
│   ├── migrations/
│   ├── schema.sql
│   └── seed_data.sql
│
├── docs/
│   └── DEMO_SCRIPT.md
│
├── posters/
│
├── src/
│   ├── main/
│   │   ├── java/com/cineflow/
│   │   │   ├── dao/
│   │   │   ├── model/
│   │   │   ├── service/
│   │   │   └── Main.java
│   │   └── resources/
│   │
│   └── test/
│
├── db.properties.example
├── pom.xml
└── README.md
```

## 🔐 Security Highlights

- Password hashing for user authentication.
- Prepared statements for database queries.
- HMAC-SHA256 signed QR ticket tokens.
- Constant-time signature comparison.
- Atomic ticket validation to prevent duplicate entry.
- Transaction-based booking operations.

## 📌 Future Enhancements

- Integration with additional payment gateways.
- Enhanced recommendation algorithms.
- Mobile application support.
- Advanced business analytics and reporting.

---

**CineFlow v2 – Making Movie Booking Smarter, Simpler, and More Secure.**
