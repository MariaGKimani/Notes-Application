# Notes Application

## Project Overview

### Description

The Notes Application allows users to create, edit, and delete notes while organizing them into categories for easy management. The application features user authentication, enabling individual user accounts for personalized note management. The backend is powered by Django, providing a robust API, while the frontend utilizes React to create a dynamic and interactive user interface.

## Features

- [ ]  **User Authentication**: Users can register by providing a username and password. The password will be hashed for security.
- [ ]  **Login**: Users can log in using their credentials. Django’s built-in authentication system will manage session handling.
- [ ]  **Logout**: Users can log out to end their session.
- [ ]  **CRUD Functionality for Notes**:
    - [ ]  Create: Users can add new notes.
    - [ ]  Read: Users can view their notes.
    - [ ]  Update: Users can edit existing notes.
    - [ ]  Delete: Users can remove notes.
- [ ]  **Categories for Notes**: Users can categorize notes to keep them organized.

## Architecture

- **Frontend**: Developed using React, which communicates with the Django backend via RESTful APIs.
- **Backend**: Built using Django REST Framework to handle user authentication and CRUD operations for notes.
- **Database**: Utilizes an SQLite database to store user and note data.

## Data Storage

The application has three primary models: **User**, **Category**, and **Note**.

1. **User Model**:
    - **Fields**:
        - `username`: CharField (unique identifier for each user)
        - `password`: Hashed password for secure authentication
        - `email`: EmailField (optional, can be used for notifications)

2. **Category Model**:
    - **Fields**:
        - `name`: CharField (to store category name)

3. **Note Model**:
    - **Fields**:
        - `title`: CharField (the title of the note)
        - `content`: TextField (the main content of the note)
        - `category`: ForeignKey (linking to the Category model for organization)
        - `user`: ForeignKey (linking to the User model to associate notes with users)
        - `created_at`: DateTimeField (timestamp for when the note was created)
        - `updated_at`: DateTimeField (timestamp for when the note was last updated)

## Database Relationships

- **User to Note**: One-to-Many relationship (a user can have multiple notes).
- **Category to Note**: One-to-Many relationship (a category can have multiple notes).

## Technology Stack

- **Backend Framework**: Django (Python) with Django REST Framework
- **Frontend Framework**: React (JavaScript)
- **Database**: SQLite for development; PostgreSQL for production
- **Version Control**: Git for source code management

## Implementation Steps

### Step 1: Set Up Django Project

1. **Initialize a new Django project**:
    - Open your terminal and navigate to the directory where you want to create the project.
    - Run the following command to create a new Django project named `notes_app`:
      ```bash
      django-admin startproject notes_app
      ```
    - Navigate into the project directory:
      ```bash
      cd notes_app
      ```

2. **Create the notes app**:
    - Run the following command to create a new app named `notes`:
      ```bash
      python manage.py startapp notes
      ```

3. **Configure settings**:
    - Open `notes_app/settings.py` and add `notes` to the `INSTALLED_APPS` list:
      ```python
      INSTALLED_APPS = [
          ...,
          'notes',
      ]
      ```

4. **Set up the database**:
    - The default database is SQLite, which is configured by default in Django. Ensure the database settings in `settings.py` are as follows:
      ```python
      DATABASES = {
          'default': {
              'ENGINE': 'django.db.backends.sqlite3',
              'NAME': BASE_DIR / "db.sqlite3",
          }
      }
      ```

5. **Run initial migrations**:
    - Run the following command to create the necessary database tables:
      ```bash
      python manage.py migrate
      ```

6. **Create a superuser** (optional, for accessing the Django admin):
    - Run the following command and follow the prompts to create a superuser:
      ```bash
      python manage.py createsuperuser
      ```

7. **Run the development server**:
    - Start the server to ensure everything is set up correctly:
      ```bash
      python manage.py runserver
      ```
    - Open your web browser and navigate to `http://127.0.0.1:8000/` to see the default Django welcome page.

Now that we have set up the Django project and created the notes app, we can move on to **Step 2**: Create User Authentication. Let me know if you’d like to continue with that or if you have any questions about Step 1!
