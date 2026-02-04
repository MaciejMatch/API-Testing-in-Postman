# Test Scripts

---

## **Create Token**
```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
const response = pm.response.json();
pm.environment.set("token", response.token);
pm.test("Response time is less than 900ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(900);
});
```

---

## **Retrieve All Bookings**
```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
pm.test("Response time is less than 1200ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(1200);
});
const ids = pm.response.json();
pm.test("Booking lists is not empty", () => {
    pm.expect(ids.length).to.be.above(0);
});
const randomId = ids[Math.floor(Math.random() * ids.length)].bookingid;
pm.environment.set("id", randomId);
```

---

## **Check Booking by ID**
```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
pm.test("Status code is not 404", function () {
    pm.response.to.not.have.status(404);
});
pm.test("Response time is less than 800ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(800);
});
```

---

## **Reservation - Create Booking**
```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
pm.test("Response time is less than 1200ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(1200);
});
pm.test("Pass response", function () {
    pm.expect(pm.response.code).to.be.oneOf([200]);
});
const response = pm.response.json();
pm.environment.set("bookingId", response.bookingid);
```

---

## **Check Create Reservation**
```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
pm.test("Response time is less than 800ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(800);
});
```

---

## **Updates a Current Booking**
```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
pm.test("Response time is less than 800ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(800);
});
```

---

## **Part Update**
```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
pm.test("Response time is less than 900ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(900);
});
```

---

## **Check Update Booking**
```javascript
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});
pm.test("Response time is less than 800ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(800);
});
```

---

## **Delete**
```javascript
pm.test("Status code is 201", function () {
    pm.response.to.have.status(201);
});
pm.test("Check delete booking", function () {
    pm.response.to.have.body("Created");
});
```

---

## **Check Delete Booking**
```javascript
pm.test("Status code is 404", function () {
    pm.response.to.have.status(404);
});
```

---

### Usage Instructions
- Copy each block of code into the corresponding Postman test script for the appropriate request.
- Make sure to set up proper environment variables (`token`, `id`, `bookingId`) based on the test scenario.
- Customize response time thresholds as needed to match your API requirements.
