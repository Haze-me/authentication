Django REST Framework Authentication Learning Project

This project is designed to teach the complete authentication workflow in Django REST Framework step by step.

The project evolves in 3 stages of login while keeping the same codebase, so the learner understands how authentication logic grows in real projects

## What This Project Teaches

By the end of this project, the learner will understand:

How to create a custom user model

How passwords are hashed in Django

How authenticate() works internally

How JWT access and refresh tokens are generated

Why Django authenticates with username by default

How to login with email

How to login with username or email (professional method)

## Tech Stack

Django

Django REST Framework

SimpleJWT (JWT Authentication)

## Installation

django-admin startproject authproject
cd authproject
python manage.py startapp accounts
pip install djangorestframework djangorestframework-simplejwt

## Add to settings.py:
INSTALLED_APPS = [
    'rest_framework',
    'accounts',
]

## JWT Settings:
from datetime import timedelta

REST_FRAMEWORK = {
    'DEFAULT_AUTHENTICATION_CLASSES': (
        'rest_framework_simplejwt.authentication.JWTAuthentication',
    ),
}

SIMPLE_JWT = {
    'ACCESS_TOKEN_LIFETIME': timedelta(minutes=30),
    'REFRESH_TOKEN_LIFETIME': timedelta(days=1),
}

## Set custom user:
AUTH_USER_MODEL = 'authen.User'

## Run migrations:
python manage.py makemigrations
python manage.py migrate

## User Registration

### Endpoint
POST /api/register/

### Body
{
  "first_name": "John Doe",
  "last_name": "Lagos",
  "username": "john",
  "state": "Enugu",
  "password1": "pass123",
  "password2": "pass123"
}

## STAGE 1 — Login with Username & Password

POST /api/login/

{
  "username": "john",
  "password": "pass123"
}

## STAGE 2 — Login with Email & Password

{
  "email": "john@email.com",
  "password": "pass123"
}

## STAGE 3 — Login with Username OR Email:

{
  "login": "john or john@gmail.com",
  "password": "pass123"
}

## Run Server:
python manage.py runserver

## Base URL:
http://127.0.0.1:8000/api/