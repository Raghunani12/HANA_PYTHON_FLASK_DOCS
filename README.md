# HANA_PYTHON_FLASK_DOCS

# Flask Beginner Guide

This document is a step-by-step guide for creating a simple Flask application. It introduces you to the basics of Flask and helps you build a well-structured project.

---

## 1. Prerequisites

Ensure you have the following installed on your system:
- Python (3.6 or later)
- pip (Python package manager)
- A text editor or IDE (e.g., VS Code, PyCharm)

---

## 2. Setting Up Your Environment

### Step 1: Create a Virtual Environment

Open your terminal or command prompt and run the following commands:

```bash
python -m venv myenv
```

Activate the virtual environment:

- **Windows**:
  ```bash
  myenv\Scripts\activate
  ```
- **macOS/Linux**:
  ```bash
  source myenv/bin/activate
  ```

### Step 2: Install Flask

With the virtual environment activated, install Flask:

```bash
pip install flask
```

---

## 3. Creating Your First Flask App

### Step 1: Project Structure

Create a folder for your project, e.g., `simple_flask_app`, and navigate to it. Inside the folder, create a file named `app.py`.

### Step 2: Write Your Flask Application

Add the following code to `app.py`:

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def home():
    return "Welcome to your first Flask app!"

if __name__ == '__main__':
    app.run(debug=True)
```

### Step 3: Run the App

Run the following commands in your terminal:

```bash
cd simple_flask_app
python app.py
```

You should see output like this:

```
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
```

### Step 4: Open Your Browser

Visit [http://127.0.0.1:5000/](http://127.0.0.1:5000/) to see:

```
Welcome to your first Flask app!
```

---

## 4. Adding Routes and Templates

### Step 1: Understanding Routes

Add another route in `app.py`:

```python
@app.route('/about')
def about():
    return "This is the About page."
```

Restart your app and visit [http://127.0.0.1:5000/about](http://127.0.0.1:5000/about).

### Step 2: Use Templates for HTML Pages

Modify your project structure:

```
simple_flask_app/
├── app.py
├── templates/
    ├── home.html
    ├── about.html
```

Create `home.html` in the `templates` folder:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Home Page</title>
</head>
<body>
    <h1>Welcome to your Flask App!</h1>
    <p>This is the home page.</p>
    <a href="/about">Go to About Page</a>
</body>
</html>
```

Create `about.html` in the `templates` folder:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>About Page</title>
</head>
<body>
    <h1>About This App</h1>
    <p>This app is built using Flask, a lightweight Python web framework.</p>
    <a href="/">Go to Home Page</a>
</body>
</html>
```

Update `app.py`:

```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def home():
    return render_template('home.html')

@app.route('/about')
def about():
    return render_template('about.html')

if __name__ == '__main__':
    app.run(debug=True)
```

### Step 3: Passing Dynamic Data to Templates

Update `app.py` to pass data to `home.html`:

```python
@app.route('/')
def home():
    user = "Raghu"
    return render_template('home.html', username=user)
```

Update `home.html`:

```html
<h1>Welcome, {{ username }}!</h1>
<p>This is the home page.</p>
```

Reload the page to see the dynamic content.

---

## 5. Next Steps

1. **Form Handling**: Learn how to handle user input with forms.
2. **Database Integration**: Connect your app to a database like SQLite.
3. **Styling**: Add CSS or frameworks like Bootstrap for better visuals.
4. **Deployment**: Host your app online using services like Heroku or AWS.

---

Happy coding! Feel free to reach out for further guidance.
