# Custom users using Django REST framework

Django customized User model set up so that an email address can be used as the primary identifier, RESTfully exposing his endpoints for client apps to use (ReactJS, iOS, Android and other).
This project follows the the tutorial given by Toni Sredanović in hos blog post which you can read [here](https://medium.com/krakensystems-blog/custom-users-using-django-rest-framework-5f755d643504).

## Init project

```bash
virtualenv --python=<path/to/python3.6> venv
python3 -m venv ./venv
source venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt
python manage.py migrate
```

## Run project

```bash
source venv/bin/activate
python manage.py runserver
```

## User

- Register: POST http://localhost:8000/rest-auth/registration/
  ```json
  {
    "email": "test@test.com",
    "password1": "ujmik,ol.",
    "password2": "ujmik,ol."
  }
  ```
  - sends email containing verification URL

- Verify email:
  - user clicks on the verification URL
  - email gets verified
  - user is redirected to http://localhost:8000/?verification=1

- Log in: POST http://localhost:8000/rest-auth/login/
  ```json
  {
    "email": "test@test.com",
    "password": "ujmik,ol."
  }
  ```

- Current user: GET http://localhost:8000/rest-auth/user/

- Log out: POST http://localhost:8000/rest-auth/logout/

- Password change: POST http://localhost:8000/rest-auth/password/change/
  ```json
  {
    "new_password1": ".lo,kimju",
    "new_password2": ".lo,kimju"
  }
  ```

- Password reset: not yet RESTful
