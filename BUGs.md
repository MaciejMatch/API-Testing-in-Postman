# Reported Bugs

## Bug 1 - Inconsistent API Documentation for Create Booking Request

### Environment:
- **API:** Restful-Booker  
- **Endpoint:** `POST /booking`  
- **Environment:** Public sandbox  

### Description:
The API documentation for the Create Booking endpoint is inconsistent regarding the structure of the `checkin` and `checkout` fields:  
- In the **Request body section**, `checkin` and `checkout` are documented as top-level fields.  
- However, the API only accepts these fields when they are nested inside the `bookingdates` object, as shown in the example JSON and response structure.  

This inconsistency may lead to consumers building requests according to the documentation, which are then rejected by the API.  

### Actual Result:
- API returns **500 Internal Server Error** for requests that follow the documentation.
![Bug 1 - Actual Result (500 Error)](https://github.com/MaciejMatch/API-Testing-in-Postman/blob/main/screenshots/BUG1.png)

### Expected Result:
- Documentation should clearly specify that `checkin` and `checkout` fields must be nested under the `bookingdates` object.  
- Alternatively, the API should accept `checkin` and `checkout` as documented in the top-level request body.

---

## Bug 2 - API Returns 500 Instead of 400 for Invalid Create Booking Request

### Environment:
- **API:** Restful-Booker  
- **Endpoint:** `POST /booking`  
- **Environment:** Public sandbox  

### Summary:
The API returns **500 Internal Server Error** instead of **400 Bad Request** when the request body validation fails.

### Description:
When a Create Booking request is sent with an **invalid body structure** (e.g., missing the required `bookingdates` object), the API responds with **500 Internal Server Error**.  
This behavior indicates improper error handling. Invalid client input should not trigger a server error.

### Steps to Reproduce:
1. Send a `POST /booking` request.
2. Provide a request body where `checkin` and `checkout` fields are at the root level (not nested in `bookingdates`).  
   Example payload:  
   ```json
   {
       "firstname": "John",
       "lastname": "Smith",
       "checkin": "2026-02-01",
       "checkout": "2026-02-03"
   }
   ```
3. Submit the request.

### Actual Result:
- API incorrectly returns **500 Internal Server Error** for the invalid request.
![Bug 2 - Actual Result (500 Error)](https://github.com/MaciejMatch/API-Testing-in-Postman/blob/main/screenshots/BUG2.png)

### Expected Result:
- API should return **400 Bad Request**.  
- Response should include a validation error indicating that the `bookingdates` object is required.

---

## Notes
Both bugs highlight issues with API documentation and error handling. Addressing them would improve the developer experience as well as prevent invalid requests leading to server errors.
