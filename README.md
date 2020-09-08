# python-sample-app

Sample Python application on Flask with PostgreSQL database

## Deploy with docker-compose

1. Bootstrap the DB
```bash
$ docker-compose up -d db-server
$ docker-compose run --rm app /bin/bash -c "cd /app && flask db upgrade"
```

2. Bring up the cluster
```bash
$ docker-compose up -d
```

3. Browse to localhost:8080 to see the app in action.


API information
---

**Show users: `GET /api/user`**

* **URL**

  `/api/user`

* **Method**

  `GET`

* **URL Params**

  None

* **Data Params**

  None

* **Success Response**

  * **Code:** 200 <br />
    **Content:**

    ```[{"id": 1,"username": "user123", "email": "user@example.com","password_hash": "example"}]```

* **Error Response**

  None

* **Sample Call**

  `curl -i -X GET http://127.0.0.1:5000/api/user`

**Create user: `POST /api/user`**

* **URL**

  `/api/user`

* **Method**

  `POST`

*  **URL Params**

   None

* **Data Params**

  JSON with required fields: `username`, `email`, `password_hash`

* **Success Response**

  * **Code:** 200 <br />
    **Content:** `{ "id" : 12, "username" : "user123",  "email": "user@example.com", "password_hash": "example"}`

* **Error Response**

  * **Code:** 400 Bad Request <br />
    **Content:** `validate error`

* **Sample Call**

  `curl -i -X POST -d '{ "username": "user123", "email": "user@example.com", "password_hash": "example" }' -H "Content-Type: application/json" http://127.0.0.1:5000/api/user`


License
---

MIT / BSD

Author Information
---

This app was created in 2019 by [Maxim Baranov](https://github.com/mbaran0v).