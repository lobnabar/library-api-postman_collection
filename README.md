# Library API Testing - Reservation Module (Postman Collection)

## 📌 Project Overview
This repository contains an automated API testing collection built using **Postman** for the **Reservation Module** of a **Library Management API**. The tests validate end-to-end workflows, role-based authentication (Admin & Client), dynamic variable chaining, and strict adherence to business logic rules.

---

## ⚙️ Core Business Logic Tested
* **Stock-Dependent Reservation:** A user (Client) is **only** allowed to reserve a book when its available stock is **zero (`0`)**.
* **In-Stock Restriction:** If copies of a book are currently available (`stock > 0`), the system enforces buying or borrowing instead, and **blocks** any reservation attempts.

---

## 🧪 Test Scenarios Covered

### 1. Positive Scenarios (End-to-End Flow)
* **Authentication & Role Management:**
  * **Admin Login:** Authenticating as an Admin to obtain an access token for inventory management.
  * **Client Login:** Authenticating as a Client to obtain an access token for browsing and reserving books.
* **Test Data Setup & Verification:**
  * **Create Book (Admin):** Adding a new book resource and configuring its stock to `0` to meet the reservation precondition.
  * **Get Books / Check Stock (Client):** Retrieving book details to verify that the target book has `0` available copies.
* **Book Reservation:**
  * **Reserve Out-of-Stock Book:** Successfully placing a reservation on the book with `0` stock and validating the expected response status and payload.

### 2. Negative & Edge-Case Scenarios
* **Business Rule Violation (In-Stock Book):** Attempting to reserve a book that currently has available copies (`stock > 0`), verifying that the API rejects the request as per business rules.
* **Non-Existent Resource:** Attempting to reserve a book using an invalid or non-existent `bookId` (expecting `404 Not Found` / appropriate error response).
* **Invalid Input / Authorization:** Testing invalid request payloads, missing fields, or unauthorized access attempts.

---

## 🛠️ Tools & Techniques Used
* **Postman:** API request design, assertions (status codes, response body validation), and test execution.
* **Dynamic Variable Chaining:** Extracting authentication tokens (`Admin` & `Client`) and dynamic resource IDs (`bookId`, `reservationId`) via Postman test scripts to ensure seamless, independent test runs.

---

## 🚀 How to Run This Collection
1. Download or clone the `.json` collection file from this repository.
2. Open **Postman** and click **Import** in the top left corner.
3. Select the imported `.json` file.
4. *(Optional)* Configure the `base_url` variable if running against a local or staging server.
5. Open the **Collection Runner** and execute the requests in sequence to observe the full Positive and Negative test flows.
