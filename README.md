# Django Blog Application

## Project Overview

This academic Django project demonstrates the foundations of a small database-backed blog application. It uses a Django model, ORM queries, function-based views, URL routing, server-rendered templates, static CSS, and Django’s standard administration interface.

The public application provides a post list and individual post-detail pages. Post management relies on the built-in Django admin rather than custom public management forms.

## Implemented Functionality

- Database-backed `Post` model
- Post listing ordered by publication date
- Individual post-detail pages
- Django ORM queries
- Function-based Django views
- Application and project URL routing
- Server-rendered Django templates
- Static CSS styling
- Django admin registration
- Standard Django admin management
- Method for publishing posts with the current date and time

The application does not implement custom public create, update, or delete views. It also does not provide a custom authentication workflow.

## Technology Stack

- Python
- Django
- Django ORM
- SQLite
- HTML
- CSS
- Django templates

## Post Data Model

The current application defines one model named `Post`.

| Field | Type | Purpose |
|---|---|---|
| `id` | Automatically generated primary key | Identifies each post |
| `title` | Character field, maximum 200 characters | Stores the post title |
| `text` | Text field | Stores the post content |
| `published_date` | Optional date/time field | Stores when the post was published |

The model also defines a `publish()` method that assigns the current date and time to `published_date` and saves the post.

## Routes and Application Flow

| Route | Purpose |
|---|---|
| `/` | Retrieves all posts, orders them by descending publication date, and renders the post list |
| `/post/<int:pk>/` | Retrieves and displays one post using its primary key |
| `/admin/` | Provides Django’s standard administration interface |

The application flow is:

1. A request to `/` calls the `post_list` view.
2. The view retrieves `Post` records through the Django ORM.
3. The records are passed to `blog/post_list.html`.
4. The template displays each post’s publication date, title, and text.
5. Selecting a post title opens its detail page.
6. Edit and Delete links lead to the corresponding Django admin pages.

## Project Structure

```text
.
├── blog/
│   ├── migrations/
│   ├── static/
│   │   └── css/
│   │       └── blog.css
│   ├── templates/
│   │   └── blog/
│   │       ├── base.html
│   │       ├── post_detail.html
│   │       └── post_list.html
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── tests.py
│   ├── urls.py
│   └── views.py
├── mysite/
│   ├── asgi.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── myvenv/
├── .gitignore
├── db.sqlite3
├── get-pip.py
└── manage.py
```

- `manage.py` provides Django’s command-line entry point.
- `mysite/` contains the project configuration, root URL routing, and ASGI/WSGI interfaces.
- `blog/` contains the active model, views, routes, admin registration, migrations, templates, and static CSS.
- `myvenv/` is a tracked Windows virtual environment. It is generated development tooling and should not be treated as a portable dependency-management solution.
- `get-pip.py` is a standalone pip bootstrap script and is not part of the Django application.
- `db.sqlite3` is the configured and currently tracked SQLite database.

The tracked environment and bootstrap script are documented here as current repository artifacts. They are not recommended as a replacement for a dependency manifest and a locally created virtual environment.

## Getting Started

### Prerequisites

- Python 3
- Django
- A web browser

The repository does not currently include a dependency manifest. The tracked `myvenv/` directory is Windows-specific and contains machine-specific configuration, so it should not be assumed to work on another computer.

A fresh development environment would normally require Django to be installed manually.

### Typical Local Setup

Clone the repository:

```bash
git clone https://github.com/asmaayasser1/my-first-blog.git
cd my-first-blog
```

Create a local virtual environment:

```bash
python -m venv .venv
```

Activate it on Windows:

```powershell
.venv\Scripts\activate
```

Activate it on macOS or Linux:

```bash
source .venv/bin/activate
```

Install Django:

```bash
python -m pip install Django
```

Apply the included migrations:

```bash
python manage.py migrate
```

Start the Django development server:

```bash
python manage.py runserver
```

Open the local application:

```text
http://127.0.0.1:8000/
```

This clean-clone workflow has not been independently verified for the current repository.

## Storage

The application is configured to use SQLite through Django’s database settings. Post records are accessed through the Django ORM.

`db.sqlite3` is tracked in the repository, but its contents were not inspected during the professionalization review. No claim is made about whether it contains personal, production, or sensitive data.

## Admin and Authentication Scope

The `Post` model is registered with Django’s built-in admin interface.

Post management relies on Django’s standard admin authentication and permission system. The project does not implement a custom authentication system or custom public post-management workflow.

The post-list template links to Django admin change and delete pages. Access to those operations depends on standard Django admin authentication and permissions.

## Testing Status

The repository contains Django’s default test-module scaffolding, but no meaningful automated test suite is currently verified.

## Security & Development Scope

This is an academic, development-oriented Django project and is not prepared for production deployment. Production use would require appropriate configuration, secret management, dependency management, automated testing, and deployment review.

## Current Limitations

- No dependency manifest is included.
- A Windows-specific virtual environment is tracked.
- The SQLite database is tracked, but its contents remain unverified.
- No custom public create, update, or delete views are implemented.
- No custom authentication workflow is implemented.
- Automated testing is limited to default scaffolding.
- No production deployment configuration is included.
- Clean-clone reproducibility has not been verified.
- Some presentation resources depend on external stylesheets and fonts.
- `get-pip.py` is stored in the repository even though the application does not reference it.

## Academic Context

This project follows a tutorial-style learning workflow focused on foundational Django concepts, including models, ORM queries, views, URL routing, templates, static styling, migrations, and admin integration.

## Project Status

Academic Django blog project being refined for professional portfolio presentation.
