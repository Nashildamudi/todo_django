# Django Todo Application

A simple and intuitive todo application built with Django that allows users to manage their daily tasks efficiently.

## Features

- **Add Tasks**: Create new todo items
- **Mark as Done/Undone**: Toggle task completion status
- **Edit Tasks**: Modify existing task descriptions
- **Delete Tasks**: Remove tasks permanently
- **Task Organization**: 
  - Active tasks displayed on the left
  - Completed tasks displayed on the right
  - Tasks sorted by last updated time
- **Responsive Design**: Bootstrap-powered UI that works on all devices
- **Date Display**: Shows current date in a readable format

## Technology Stack

- **Backend**: Django 5.2.4
- **Database**: SQLite (default)
- **Frontend**: HTML, CSS, Bootstrap 5.3.0
- **Icons**: Font Awesome 4.7.0
- **Python Version**: Compatible with Python 3.x

## Project Structure

```
todo_django/
├── db.sqlite3              # SQLite database
├── manage.py               # Django management script
├── todo_main/              # Main project configuration
│   ├── __init__.py
│   ├── asgi.py            # ASGI configuration
│   ├── settings.py        # Django settings
│   ├── urls.py            # Main URL configuration
│   ├── views.py           # Home page view
│   └── wsgi.py            # WSGI configuration
├── todos/                  # Todo app
│   ├── __init__.py
│   ├── admin.py           # Admin interface configuration
│   ├── apps.py            # App configuration
│   ├── models.py          # Task model definition
│   ├── tests.py           # Test cases
│   ├── urls.py            # App-specific URLs
│   ├── views.py           # Todo-related views
│   └── migrations/        # Database migrations
├── templates/              # HTML templates
│   ├── home.html          # Main todo interface
│   └── edit_task.html     # Task editing interface
└── env/                   # Virtual environment (if present)
```

## Installation & Setup

### Prerequisites
- Python 3.7 or higher
- pip (Python package installer)
- Git

### Step 1: Clone the Repository
```bash
git clone https://github.com/Nashildamudi/todo_django.git
cd todo_django
```

### Step 2: Create Virtual Environment (Recommended)
```bash
# Create virtual environment
python -m venv env

# Activate virtual environment
# On Windows:
env\Scripts\activate
# On macOS/Linux:
source env/bin/activate
```

### Step 3: Install Dependencies
```bash
pip install django
```

### Step 4: Run Database Migrations
```bash
python manage.py makemigrations
python manage.py migrate
```

### Step 5: Create Superuser (Optional)
```bash
python manage.py createsuperuser
```

### Step 6: Run the Development Server
```bash
python manage.py runserver
```

The application will be available at `http://127.0.0.1:8000/`

## Usage

### Adding a Task
1. Navigate to the home page
2. Type your task in the input field at the bottom
3. Click the "Add" button or press Enter

### Managing Tasks
- **Mark as Done**: Click the green "Mark as Done" button on any active task
- **Edit Task**: Click the pencil icon to modify a task description
- **Delete Task**: Click the trash icon to permanently remove a task
- **Mark as Undone**: Click "Mark as unDone" on completed tasks to reactivate them

### Interface Overview
- **Left Panel**: Active/pending tasks
- **Right Panel**: Completed tasks
- **Bottom**: Add new task form

## Models

### Task Model
```python
class Task(models.Model):
    task = models.CharField(max_length=250)          # Task description
    is_completed = models.BooleanField(default=False) # Completion status
    created_at = models.DateTimeField(auto_now_add=True)  # Creation timestamp
    updated_at = models.DateTimeField(auto_now=True)      # Last update timestamp
```

## URL Patterns

- `/` - Home page (task list)
- `/admin/` - Django admin interface
- `/todos/addTask/` - Add new task (POST)
- `/todos/mark_as_done/<id>/` - Mark task as completed
- `/todos/mark_as_undone/<id>/` - Mark task as pending
- `/todos/edit_task/<id>/` - Edit task
- `/todos/delete_task/<id>/` - Delete task

## API Endpoints

All todo operations are handled through form submissions and redirects:

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | Display home page with tasks |
| POST | `/todos/addTask/` | Create new task |
| GET | `/todos/mark_as_done/<pk>/` | Mark task as completed |
| GET | `/todos/mark_as_undone/<pk>/` | Mark task as pending |
| GET/POST | `/todos/edit_task/<pk>/` | Edit existing task |
| GET | `/todos/delete_task/<pk>/` | Delete task |

## Customization

### Styling
The application uses Bootstrap 5 for styling. You can customize the appearance by:
- Modifying the CSS in the HTML templates
- Adding custom CSS files
- Updating Bootstrap classes

### Database
To use a different database:
1. Update the `DATABASES` setting in `todo_main/settings.py`
2. Install the appropriate database adapter
3. Run migrations

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -am 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Create a Pull Request

## Known Issues

- Minor typo in `views.py` line 24: `get_tesk` should be `get_task` (functionality works correctly)
- Edit template has a minor HTML formatting issue on line 16

## Future Enhancements

- [ ] User authentication and authorization
- [ ] Task categories/tags
- [ ] Due dates and reminders
- [ ] Task priority levels
- [ ] Search and filter functionality
- [ ] REST API for mobile app integration
- [ ] Task sharing between users

## License

This project is open source and available under the [MIT License](LICENSE).

## Contact

**Nashil Damudi**
- GitHub: [Nashildamudi](https://github.com/Nashildamudi)
- Repository: [todo_django](https://github.com/Nashildamudi/todo_django.git)

## Acknowledgments

- Django community for the excellent framework
- Bootstrap for the responsive UI components
- Font Awesome for the icons

---

*Happy Task Management! 📝✅*