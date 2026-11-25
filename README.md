# Laravel POS -- TFA8 Activity

A Laravel-based Point of Sale (POS) project extended for the TFA7
activity: **Forms, Validation, and File Upload**.

The activity adds customer and user management forms, server-side
validation, profile editing, and avatar uploads.

## Features

-   User registration and login using Laravel Breeze.
-   Customer management:
    -   View customer records.
    -   Create customers with a full name and valid email address.
    -   Edit existing customer records.
-   User management:
    -   View user accounts.
    -   Create user records with a username, full name, and email
        address.
    -   Edit existing user records.
    -   Validate that usernames and email addresses are unique.
-   Avatar upload:
    -   Accept image uploads up to 2 MB.
    -   Store uploaded files on Laravel's public storage disk.
    -   Save the avatar file path in the database.
-   Validation feedback for submitted forms.

> **Activity requirement to verify:** The assignment also requires
> creating a display-ready processed avatar/thumbnail using an
> instructor-approved image package. Confirm that image processing has
> been implemented before treating this requirement as complete. The
> current basic upload implementation stores the uploaded image file.

## Requirements

Install the following before running the project:

-   PHP 8.2 or a compatible version required by the installed Laravel
    version
-   Composer
-   MySQL or MariaDB
-   Node.js and npm
-   A web browser

For a local Windows setup, XAMPP can provide PHP and MySQL.

## Installation

### 1. Clone or download the project

Clone the repository:

``` bash
git clone YOUR_GITHUB_REPOSITORY_URL
```

Go into the project directory:

``` bash
cd YOUR_PROJECT_FOLDER
```

If you downloaded the project as a ZIP file, extract it and open the
extracted folder in your terminal.

### 2. Install PHP dependencies

``` bash
composer install
```

### 3. Create the environment file

Copy `.env.example` and name the copy `.env`.

On Windows PowerShell:

``` powershell
Copy-Item .env.example .env
```

Open `.env` and configure your database connection. Example:

``` env
APP_NAME="Laravel POS"
APP_ENV=local
APP_KEY=
APP_DEBUG=true
APP_URL=http://127.0.0.1:8000

DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=
DB_USERNAME=root
DB_PASSWORD=
```

Create the database in phpMyAdmin or your MySQL tool. Replace
`YOUR_DATABASE_NAME` with the database name you created. Update the
username and password if your MySQL setup uses different credentials.

### 4. Generate the application key

``` bash
php artisan key:generate
```

### 5. Run database migrations

``` bash
php artisan migrate
```

This runs the project's pending migrations. **Do not use `migrate:fresh`
on a database containing records you need to keep**, because it drops
existing tables.

### 6. Create the public storage link

Avatar files are stored on Laravel's `public` disk. Run:

``` bash
php artisan storage:link
```

This makes files stored under `storage/app/public` accessible through
`public/storage`.

### 7. Install frontend dependencies and build assets

``` bash
npm install
npm run build
```

### 8. Start the Laravel development server

``` bash
php artisan serve
```

Open the URL shown in the terminal, usually:

``` text
http://127.0.0.1:8000
```

Register or log in, then open the customer or user management pages.

## Main Routes

The customer and user management routes are protected by authentication.

  Page or action    Route
  ----------------- ------------------------------
  Customer list     `/customers`
  Create customer   `/customers/create`
  Edit customer     `/customers/{customer}/edit`
  User accounts     `/users`
  Create user       `/users/create`
  Edit user         `/users/{user}/edit`
  Login             `/login`
  Register          `/register`

## Validation Rules

### Customers

-   `full_name` is required.
-   `email` is required and must be a valid email address.

### Users

-   `username` is required and must be unique.
-   `full_name` is required.
-   `email` is required, must be valid, and must be unique.
-   `avatar` is optional, must be an image, and must not exceed 2 MB.

When editing a record, the unique validation rule ignores the current
record so that the user can keep their existing username or email
address.

## Avatar Storage

Uploaded avatar files are stored in:

``` text
storage/app/public/avatars
```

The database stores the relative file path in the `avatar` column,
rather than storing the image itself.

Make sure the `public/storage` symbolic link exists. If it does not,
run:

``` bash
php artisan storage:link
```

## Database and Submission

The project uses Laravel migrations to create and update its database
tables.

For submission, include either:

-   A database export (for example, an SQL file), or
-   The migrations and any seeders needed to recreate the database
    structure and sample data.

Do not include private credentials from your `.env` file in the public
GitHub repository. Keep `.env` local and commit `.env.example` instead.



## Developer
**QUEJADA, RAINA KISHAN S.**
