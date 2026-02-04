# Test Cases

## Test Case 1 - Generate Auth Token
**Objective:** Verify that a valid token is generated for a user.  
**Endpoint:** `POST /auth`  
**Payload:**
```json
{
    "username": "admin",
    "password": "password123"
}
```
**Expected Response:** Status 200, JSON contains token.  

Below screen with positive test result:  
![Generate Auth Token](https://github.com/MaciejMatch/API-Testing-in-Postman/blob/main/screenshots/2026-02-02_14h42_33%20(1).png)

---

## Test Case 2 - Retrieve All Bookings
**Objective:** Verify that all bookings can be retrieved.  
**Endpoint:** `GET /booking`  
**Expected Response:** Status 200, JSON contains a list of bookings.  

After sending the GET request we get all the IDs in response:  
![Retrieve All Bookings](https://github.com/MaciejMatch/API-Testing-in-Postman/blob/main/screenshots/2026-02-02_14h53_39%20(1).png)

---

## Test Case 3 - Create New Booking
**Objective:** Verify that a new booking can be created successfully.  
**Endpoint:** `POST /booking`  
**Payload:**
```json
{
    "firstname": "Maciej",
    "lastname": "Musiauu",
    "totalprice": 5000,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2026-01-28",
        "checkout": "2026-01-30"
    },
    "additionalneeds": "A lot of Dumle"
}
```
**Expected Response:** Status 200/201, JSON contains bookingid and booking details.  

After sending the POST request with Body, our reservation was created:  
![Create New Booking](https://github.com/MaciejMatch/API-Testing-in-Postman/blob/main/screenshots/2026-02-02_15h19_32%20(2).png)

---

## Test Case 4 - Retrieve Booking by ID
**Objective:** Verify that a booking can be retrieved by ID.  
**Endpoint:** `GET /booking/{bookingid}`  
**Expected Response:** Status 200, JSON matches data from TC-03.  

When using the `bookingid` created in TC3 and sending a GET request, the system responded with our reservation:  
![Retrieve Booking by ID](https://github.com/MaciejMatch/API-Testing-in-Postman/blob/main/screenshots/2026-02-02_15h24_17%20(1).png)

---

## Test Case 5 - Update Booking
**Objective:** Verify that a booking can be updated.  
**Endpoint:** `PUT /booking/{bookingid}`  
**Payload:**
```json
{
    "firstname": "Maciej",
    "lastname": "Musiauu",
    "totalprice": 8900,
    "depositpaid": true,
    "bookingdates": {
        "checkin": "2026-01-28",
        "checkout": "2026-02-30"
    },
    "additionalneeds": "A lot of cookies"
}
```
**Expected Response:** Status 200, JSON reflects updated booking data.  

Before PUT:  
![Before PUT](https://github.com/MaciejMatch/API-Testing-in-Postman/blob/main/screenshots/2026-02-02_15h24_17%20(1).png)

After PUT:  
![After PUT](https://github.com/MaciejMatch/API-Testing-in-Postman/blob/main/screenshots/2026-02-02_15h38_51%20(1).png)

---

## Test Case 6 - Partial Update Booking
**Objective:** Verify that a booking can be partially updated.  
**Endpoint:** `PATCH /booking/{bookingid}`  
**Payload:**
```json
{
    "totalprice": "6500"
}
```
**Expected Response:** Status 200, `totalprice` updated, other fields unchanged.  

Before PATCH:  
![Before PATCH](https://github.com/MaciejMatch/API-Testing-in-Postman/blob/main/screenshots/2026-02-02_15h46_44%20(1).png)

After PATCH:  
![After PATCH](https://github.com/MaciejMatch/API-Testing-in-Postman/blob/main/screenshots/2026-02-02_15h49_05%20(1).png)
---

## Test Case 7 - Delete Booking
**Objective:** Verify that a booking can be deleted successfully.  
**Endpoint:** `DELETE /booking/{bookingid}`  
**Expected Response:** Status 201.  

After sending the DELETE request, we received the correct response:  
![Delete Booking](https://github.com/MaciejMatch/API-Testing-in-Postman/blob/main/screenshots/2026-02-02_15h53_11%20(1).png)

---

## Test Case 8 - Verify Booking Deletion
**Objective:** Verify that a deleted booking cannot be retrieved.  
**Endpoint:** `GET /booking/{bookingid}`  
**Expected Response:** Status 404.  

In TC7, booking `1150` was deleted. After sending a GET request with `ID:1150` for verification, the system couldn't find the booking:  
![Verify Booking Deletion](https://github.com/MaciejMatch/API-Testing-in-Postman/blob/main/screenshots/2026-02-02_16h00_19%20(1).png)

---

## NTC 1 - Delete Booking without Token
**Objective:** Verify that deleting a booking without a token fails.  
**Endpoint:** `DELETE /booking/{bookingid}`  
**Payload:** Empty  
**Expected Response:** Status 401/403.  

When trying to delete booking `1721` without an active token, the response code was `403`:  
![Delete Booking without Token](https://github.com/MaciejMatch/API-Testing-in-Postman/blob/main/screenshots/2026-02-02_16h18_59%20(1).png)

---

## NTC 2 - Create Booking with Missing Fields
**Objective:** Verify that creating a booking with missing required fields fails.  
**Endpoint:** `POST /booking`  
**Expected Response:** Status 400.  

When sending a POST request with an empty body, the system returned code `400`:  
![Create Booking with Missing Fields](https://github.com/MaciejMatch/API-Testing-in-Postman/blob/main/screenshots/2026-02-02_16h28_15%20(1).png)

---

## NTC 3 - Retrieve Non-existent Booking
**Objective:** Verify that retrieving a non-existent booking returns an error.  
**Endpoint:** `GET /booking/{invalidId}`  
**Expected Response:** Status 404.  

When sending a GET request with `id=999999999` (non-existent booking), the response code was `404`:  
![Retrieve Non-existent Booking](https://github.com/MaciejMatch/API-Testing-in-Postman/blob/main/screenshots/2026-02-02_16h32_53%20(1).png)
