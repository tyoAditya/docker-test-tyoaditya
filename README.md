#Technical Test Result - Tax and Bill Calculator 

## Docker + Lumen with Nginx and MySQL

## Build & Run this docker from shell with this command
```bash
docker-compose up --build -d
```

Navigate to [http://localhost:80](http://localhost:80) and you should see something like this
Lumen (5.7.6) (Laravel Components 5.7.*)

Success! You can now start access the API for Tax Object and Billings.


### Stop Everything

```bash
docker-compose down
```

**Tax Object**
----
  Create Tax Object.

* **URL**

  /api/taxobjects/create

* **Method:**

  `POST`
  
* **Data Params**

   **Required:**
 
   `name=[string]`
   `taxcode=[int between 1-3]`
   `amount=[int]`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** `{"name":"Music Cafe","taxcode":3,"amount":490}`
 
* **Error Response:**

  * **Code:** 422 UNPROCESSABLE <br />
    **Content:** `{"name":["The name field is required."],"amount":["The amount field is required."]}`

  OR

  * **Code:** 422 UNPROCESSABLE <br />
    **Content:** `{"taxcode":["Please fill Tax Code with this options: \"1\" for food, \"2\" for tobacco, and \"3\" for entertainment."]}`

* **Sample JSON Data Params:**

  ```	
    {
		  "name": "Music Cafe",
		  "taxcode": 4,
		  "amount": 490
		}
  ```


----
  Tax Object List.

* **URL**

  /api/taxobjects

* **Method:**

  `GET`
  
* **Data Params**

   **Required:**
 
   `name=[string]`
   `taxcode=[int between 1-3]`
   `amount=[int]`

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** `[{"name":"Big mac","taxcode":1,"amount":"1000.00"},{"name":"Music Cafe","taxcode":2,"amount":"90.00"},{"name":"Music Cafe","taxcode":2,"amount":"90.00"},{"name":"Music Cafe","taxcode":3,"amount":"490.00"},{"name":"Pizza","taxcode":1,"amount":"100.00"},{"name":"Marlboro","taxcode":2,"amount":"90.00"},{"name":"Music Cafe","taxcode":3,"amount":"490.00"}]`
 

**Show Bills**
----
  Show bills from all tax object.

* **URL**

  /api/bills

* **Method:**

  `GET`
  
* **Data Params**

   **none:**

* **Success Response:**

  * **Code:** 200 <br />
    **Content:** `{"allBillDetails":[{"taxobject_id":1,"name":"Big mac","taxcode":1,"amount":"1000.00","taxamount":"100.00","totalamount":"1100.00"},{"taxobject_id":2,"name":"Music Cafe","taxcode":2,"amount":"90.00","taxamount":"11.80","totalamount":"101.80"},{"taxobject_id":3,"name":"Music Cafe","taxcode":2,"amount":"90.00","taxamount":"11.80","totalamount":"101.80"},{"taxobject_id":4,"name":"Music Cafe","taxcode":3,"amount":"490.00","taxamount":"3.90","totalamount":"493.90"},{"taxobject_id":5,"name":"Pizza","taxcode":1,"amount":"100.00","taxamount":"10.00","totalamount":"110.00"},{"taxobject_id":6,"name":"Marlboro","taxcode":2,"amount":"90.00","taxamount":"11.80","totalamount":"101.80"},{"taxobject_id":7,"name":"Music Cafe","taxcode":3,"amount":"490.00","taxamount":"3.90","totalamount":"493.90"}],"totalAmount":2350,"totalTaxAmount":153.20000000000002,"grandTotal":2503.2}`
 

**Unit Test**
----
  Run unit test across create tax object types.

  * **Command**
  `./var/www/html/app/vendor/bin/phpunit --bootstrap vendor/autoload.php tests/TaxObjectBillsTest`

  * **Success Response:**
  `PHPUnit 7.4.4 by Sebastian Bergmann and contributors.

    ...                                                                 3 / 3 (100%)

    Time: 110 ms, Memory: 10.00MB

    OK (3 tests, 9 assertions)`




