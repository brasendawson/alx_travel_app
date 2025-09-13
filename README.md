# ALX Travel App

A Django REST API application for travel listings with Swagger documentation.

## Setup and Installation

### Prerequisites
- Python 3.8+
- MySQL (optional, SQLite is used by default for development)

### Installation

1. **Clone the repository** (if applicable):
   ```bash
   git clone <repository-url>
   cd alx_travel_app
   ```

2. **Create and activate a virtual environment**:
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # On Windows: .venv\Scripts\activate
   ```

3. **Install dependencies**:
   ```bash
   pip install -r requirements.txt
   ```
   
   Or install manually:
   ```bash
   pip install django djangorestframework django-cors-headers celery drf-yasg django-environ PyMySQL
   ```

4. **Environment Configuration**:
   - Copy `.env.example` to `.env`
   - Update the values in `.env` as needed
   - For MySQL: Set `USE_MYSQL=True` and configure MySQL credentials
   - For SQLite (default): Set `USE_MYSQL=False`

5. **Run migrations**:
   ```bash
   cd alx_travel_app
   python manage.py migrate
   ```

6. **Create a superuser** (optional):
   ```bash
   python manage.py createsuperuser
   ```

7. **Start the development server**:
   ```bash
   python manage.py runserver
   ```

## Configuration

### Environment Variables (`.env` file)

```env
# Django Settings
SECRET_KEY=your-secret-key-here
DEBUG=True
ALLOWED_HOSTS=localhost,127.0.0.1

# Database Configuration
USE_MYSQL=False  # Set to True to use MySQL

# MySQL Configuration (only used if USE_MYSQL=True)
DB_NAME=alx_travel_app
DB_USER=root
DB_PASSWORD=your-mysql-password
DB_HOST=localhost
DB_PORT=3306

# CORS Settings
CORS_ALLOWED_ORIGINS=http://localhost:3000,http://127.0.0.1:3000
```

### Key Features Configured

1. **Django REST Framework**: For building REST APIs
2. **CORS Headers**: For cross-origin requests
3. **Swagger Documentation**: Available at `/swagger/`
4. **Environment Variables**: Using `django-environ` for secure configuration
5. **MySQL Support**: With PyMySQL adapter (configurable via environment)
6. **SQLite Fallback**: For easy development setup

## API Documentation

Once the server is running, you can access:

- **Swagger UI**: http://127.0.0.1:8000/swagger/
- **ReDoc**: http://127.0.0.1:8000/redoc/
- **JSON Schema**: http://127.0.0.1:8000/swagger.json

## Project Structure

```
alx_travel_app/
├── manage.py
├── alx_travel_app/
│   ├── __init__.py
│   ├── settings.py      # Main configuration
│   ├── urls.py          # URL routing with Swagger
│   ├── wsgi.py
│   └── asgi.py
├── listings/            # Main app for travel listings
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── views.py
│   ├── urls.py          # App-specific URLs
│   └── migrations/
├── .env                 # Environment variables (not in git)
├── .env.example         # Environment template
└── README.md
```

## Development

### Adding New API Endpoints

1. Create views in `listings/views.py`
2. Add URL patterns in `listings/urls.py`
3. The Swagger documentation will automatically update

### Database Switching

To switch from SQLite to MySQL:
1. Set `USE_MYSQL=True` in your `.env` file
2. Configure MySQL credentials in `.env`
3. Ensure MySQL server is running
4. Run migrations: `python manage.py migrate`

## Packages Installed

- **django**: Web framework
- **djangorestframework**: REST API framework
- **django-cors-headers**: CORS handling
- **celery**: Async task processing
- **drf-yasg**: Swagger/OpenAPI documentation
- **django-environ**: Environment variable management
- **PyMySQL**: MySQL database adapter