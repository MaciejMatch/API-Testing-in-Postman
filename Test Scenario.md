# Booking Lifecycle Test Scenario

## Description
Tests the complete lifecycle of a booking: **create → retrieve → update → partial update → delete**, using a valid authentication token.

---

## Preconditions
1. The **RESTful‑Booker API** is running (e.g., `GET /ping` → Response: **201**).
2. User has valid credentials:
   - **Username:** `admin`
   - **Password:** `password123`
3. API client (e.g., Postman) is configured to **store the token** for subsequent requests.

---

## Test Steps

### **Step 1 – Generate Auth Token**
- **Action:**  
    Send a `POST` request to the endpoint `POST /auth` with valid credentials.  
- **Expected Result:**  
    - Response Status: **200 OK**  
    - JSON Response should contain a valid token.

---

### **Step 2 – Retrieve All Bookings**
- **Action:**  
    Send a `GET` request to the endpoint `GET /booking`.  
- **Expected Result:**  
    - Response Status: **200 OK**  
    - JSON Response should contain a list of all existing bookings.

---

### **Step 3 – Create New Booking**
- **Action:**  
    Send a `POST` request to the endpoint `POST /booking` using the generated token.  
- **Expected Result:**  
    - Response Status: **200/201 Created**  
    - JSON Response should contain `bookingid` and the booking data.

---

### **Step 4 – Retrieve Booking by ID**
- **Action:**  
    Send a `GET` request to the endpoint `GET /booking/{bookingid}` using the `bookingid` saved from Step 3.  
- **Expected Result:**  
    - Response Status: **200 OK**  
    - JSON Response should match the booking data sent in Step 3.

---

### **Step 5 – Update Booking**
- **Action:**  
    Send a `PUT` request to the endpoint `PUT /booking/{bookingid}` using the token.  
- **Expected Result:**  
    - Response Status: **200 OK**  
    - JSON Response should reflect all updated booking data.

---

### **Step 6 – Partial Update Booking**
- **Action:**   
    Send a `PATCH` request to the endpoint `PATCH /booking/{bookingid}` using the token.  
- **Expected Result:**  
    - Response Status: **200 OK**  
    - Only the specified fields should be updated, while the remaining fields stay unchanged.

---

### **Step 7 – Delete Booking**
- **Action:**  
    Send a `DELETE` request to the endpoint `DELETE /booking/{bookingid}` using the token.  
- **Expected Result:**  
    - Response Status: **201** (Success).  

---

### **Step 8 – Verify Booking Deletion**
- **Action:**  
    Send a `GET` request to the endpoint `GET /booking/{bookingid}` for the deleted `bookingid`.  
- **Expected Result:**  
    - Response Status: **404 Not Found**.  

---

## **Negative Steps**

### **1. Delete Booking Without Token**
- **Action:**  
    Attempt to delete a booking without providing a valid authentication token (`DELETE /booking/{bookingid}`).  
- **Expected Result:**  
    - Response Status: **401 Unauthorized / 403 Forbidden**.

---

### **2. Create Booking with Missing Fields**
- **Action:**  
    Attempt to send a `POST /booking` request with an empty or incomplete payload.  
- **Expected Result:**  
    - Response Status: **400 Bad Request**.  
    - Response body should include a validation message explaining the missing required fields.

---

### **3. Retrieve Non-existent Booking**
- **Action:**  
    Send a `GET /booking/{invalidId}` request where `{invalidId}` is a non-existent ID (e.g., `999999999`).  
- **Expected Result:**  
    - Response Status: **404 Not Found**.  
    - The response should indicate that the booking does not exist.

---

## Notes
- Use proper assertions to validate response codes and the structure of the response body.
- Ensure that all API interactions return consistent and expected results to avoid flaky tests.
