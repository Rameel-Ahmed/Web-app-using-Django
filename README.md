# Web-app-using-Django
# 📝 Django Job Application Form

This is a simple Django web application that allows users to submit a job application form. It collects user data such as first name, last name, email, date, and occupation, then stores it in a database.

---

## 📁 Project Structure

```
project/
│
├── app/
│   ├── forms.py
│   ├── models.py
│   ├── views.py
│   ├── templates/
│   │   ├── base.html
│   │   ├── index.html
│   │   └── about.html
│   └── ...
├── manage.py
└── ...
```

---

## ⚙️ Features

- Form to collect user job application data
- Stores data in a database (default: SQLite)
- Bootstrap-styled frontend
- Flash success message on form submission
- Admin panel support via superuser

---

## 🚀 Getting Started

### 1. Clone the Repo

```bash
git clone <your-repo-url>
cd <project-directory>
```

### 2. Set Up Virtual Environment (Optional but Recommended)

```bash
python -m venv env
source env/bin/activate  # On Windows use: env\Scripts\activate
```

### 3. Install Requirements

```bash
pip install django
```

### 4. Apply Migrations

```bash
python manage.py migrate
```

### 5. Create Superuser (Optional)

```bash
python manage.py createsuperuser
```

### 6. Run the Server

```bash
python manage.py runserver
```

Visit `http://127.0.0.1:8000/` in your browser.

---

## 📄 Files Overview

### `forms.py`

Defines the Django form using `forms.Form` to capture user inputs.

```python
class ApplicationForm(forms.Form):
    first_name = forms.CharField(max_length=80)
    last_name = forms.CharField(max_length=80)
    email = forms.EmailField()
    date = forms.DateField()
    occupation = forms.CharField(max_length=80)
```

---

### `models.py`

Defines a Django model to store form data in the database.

```python
class Form(models.Model):
    first_name = models.CharField(max_length=80)
    last_name = models.CharField(max_length=80)
    email = models.EmailField()
    date = models.DateField()
    occupation = models.CharField(max_length=80)
```

---

### `views.py`

Handles rendering the form, validating POST requests, saving data, and rendering templates.

```python
def index(request):
    if request.method == "POST":
        ...
        if form.is_valid():
            Form.objects.create(...)
            messages.success(request, "Form Submitted Successfully.")
            return redirect("index")
    else:
        form = ApplicationForm()
    return render(request, "index.html", {"form": form})
```

---

## 🖼 Templates

### `base.html`

Contains the overall layout and navigation bar using Bootstrap.

### `index.html`

Contains the job application form and uses Django template tags for form submission and message display.

---

## 🧪 How It Works

- User opens the form via `/`
- Fills in the data and submits
- Django validates and saves it to the database
- Success message is shown
- Data can be viewed from the Django admin panel

---

## 🛠 Notes

- By default, data is stored in `db.sqlite3`. You can configure another DB like MySQL in `settings.py`.
- Make sure to register your model in `admin.py` to view it in the admin panel.

---

## ✅ Future Improvements

- Add validation messages
- Add email confirmation or notification
- Store submissions with timestamps
- Paginate or list submitted entries in admin

---

## 📃 License

This project is for educational/demo purposes. Modify and use as needed.
