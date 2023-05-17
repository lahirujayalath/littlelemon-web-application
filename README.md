# Back-End Developer Capstone Little Lemon Web Application

## Description of the project
This is the final assignment for Back-End Developer Capstone course


## Specification of Requirement
 - Does the web application use Django to serve static HTML content?
 - Has the learner committed the project to a Git repository?
 - Does the application connect the backend to a MySQL database?
 - Are the menu and table booking APIs implemented?
 - Is the application set up with user registration and authentication?
- Does the application contain unit tests?
- Can the API be tested with the Insomnia REST client?

## Getting Started

### code repo
```bash
git clone git@github.com:YangyangLi0528/littlelemon-web-application.git
```
### dependencies
 - [Python 3]
 - [Django]
 - [Django REST framework]
 - [Djoser]
 - [sqlite3] optional Database
 - [MySQL] default Database

### virtual environment

It is recommend to work within a virtual environment.
If using Conda,  
```bash
 conda activate base 
 ```

### database setup
 - we use **MySQL** by default and need your local mysql to support
 Change settings (USER and PASSWORD) in littlelemon/settings.py, you should use your credentials.

 - sqlite3 is a very simple and easy local database, to use it please open settings.py and search ```DATABASES```, uncomment the 
 ``` bash
 DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.sqlite3",
        "NAME": BASE_DIR / "db.sqlite3",
    }
}
```
and comment MySQL related config
```bash
DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.mysql",
        "NAME": "LittleLemon",
        "HOST" : "127.0.0.1",
        "PORT" : "3306",
        "USER" : "littlelemon",
        "PASSWORD" : "littlelemon@demo",
        "OPTIONS": {  
            "init_command": "SET sql_mode='STRICT_TRANS_TABLES'"  
        }
    }
}
```
## Running the project
please switch to the littlelemon directory and run
```bash
python3 manage.py runserver
```
## Unit Test
```bash
python3 manage.py test
```

### credentials
To run unit test or request API endpoint, you may need tokens
- name: admin
- password: admin
- token: 7927d1d278c7fc3ad05277ce3c26af1da403b5e3	

## API
In order to request the API, we need JWT tokens that can be generated by logging in with the provided credentials (username and password) and you will get auth_token

POST http://127.0.0.1:8000/auth/token/login/


| URL                   | METHOD                                      | USER LEVEL     | DESCRIPTION                                                                     |
| -------------------------- | ----------------------------------------- | ---------- | --------------------------------------------------------------------------- |
| /auth/token/login/         | POST                                     | anyone        | login with a correct username and password and will generate token that can be used to request other urls                                                           |
| /auth/token/logout/        | POST | anyone       | Logout the user (remove user token)                          |
| /auth/users/                | POST                          | anyone       | Creates a new user with name, email and password                            |
| /auth/users/me/            | GET          | anyone        | Displays the current user                                                   |
| /auth/users/me/            |PUT, PATCH     | anyone| Update the current user                                                     |
| /auth/users/me/            | DELETE | anyone     | Delete the current user                                                     |
| /restaurant/users          | GET                                     | Admin        | Returns all users                                                           |
| /restaurant/users          | POST                                    | Admin       | Creates a new user                                                          |
| /restaurant/menu-items            | GET |  customer| return all menu-items |
| /restaurant/menu-items/{menuItem} | GET | customer                     | Returns the specific menu-item      |
| /restaurant/menu-items/{menuItem} | PUT, PATCH                   |  admin| Updates the menu-item item |
| /restaurant/menu-items/{menuItem} | DELETE     | admin                   | Deletes the menu-item item |
| /restaurant/bookings             | GET | customers        | Returns all bookings user   |
| /restaurant/bookings              | POST   |customers    | Creates a new booking       |


index page can be seen on 
```base
http://127.0.0.1:8000/restaurant/home/
```
and API ROOT page can be seen on 
```base
http://127.0.0.1:8000/restaurant/
```
