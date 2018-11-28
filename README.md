**Technical Test Result**
# Docker + Lumen with Nginx and MySQL

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

**Tax Object Create**
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

  ```	{
		  "name": "Music Cafe",
		  "taxcode": 4,
		  "amount": 490
		}
  ```



