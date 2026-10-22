CINEBOOK - JAVA SWING + CORE JAVA + SQLITE
===========================================

Requirements:
- JDK 17 or newer
- Maven (recommended) OR VS Code with Java support
- Internet is needed once to download Maven dependencies (SQLite JDBC driver). After dependencies are cached, it can usually run offline.

Project structure:
CineBook/
  pom.xml
  src/main/java/cinebook/
    Main.java, Person.java, User.java, Admin.java
    Movie.java, Show.java, Booking.java
    BookingService.java, AuthService.java, AdminService.java, Database.java
    AuthGUI.java, CineBookGUI.java, AdminDashboardGUI.java

RUN IN VS CODE:
1. Extract the ZIP.
2. Open the CineBook folder (the folder containing pom.xml) in VS Code.
3. Install JDK 17+ and Apache Maven. In terminal, check:
     java -version
     mvn -version
4. Run from the project root:
     mvn clean compile
     mvn exec:java
   Maven downloads SQLite JDBC and required Maven plugins the first time. If your connection is unreliable, run these commands when internet is available and let them finish.
5. SQLite database file `cinebook.db` is created in the project working directory automatically.

ADMIN LOGIN:
  Email: admin@cinebook.com
  Password: Admin@123

ADMIN DASHBOARD (tabs):
- Overview: total bookings, total revenue, tickets sold, registered customers,
  cancelled bookings, movie/showtime counts, and revenue by movie.
- Movies: add, update and delete movies (select a row to load it into the form).
  A movie with active bookings cannot be deleted until those bookings are cancelled.
- Showtimes & Prices: add, update and delete showtimes and ticket prices
  (time format like 10:00 AM or 6:30 PM). Price changes apply to new bookings;
  existing bookings keep the price they were booked at.
- Bookings: view all customer bookings, search by ID/name/email/movie, filter by
  status, and cancel a booking (its seats become available again and it no
  longer counts toward revenue).
- Users: view all registered accounts with their booking count and total spent.

LOGOUT:
- Both the customer booking screen and the admin dashboard have a Logout button
  that returns to the login screen.

DATABASE:
- `users`: customer and admin accounts
- `movies`: movie details
- `shows`: showtimes and prices
- `bookings`: booked seats, total price, date/time and status (CONFIRMED / CANCELLED)
- Sample movies and shows are inserted only when the database is brand new, so movies deleted by the admin stay deleted.
- An existing cinebook.db from the older version is upgraded automatically (a status column is added to bookings).
- User accounts and bookings persist when the program closes.

IMPORTANT:
- This is an educational project. The demo stores passwords as plain text in SQLite for simplicity; this is NOT safe for real-world use. Real systems should use password hashing.
- Do not delete `cinebook.db` if you want to keep saved accounts/bookings.
- If `mvn` is not recognized, install Maven or use the VS Code Maven for Java extension and configure Maven.
