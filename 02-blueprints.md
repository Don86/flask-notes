# Blueprints and Jinja2

* Motivation: keeping routes organized, instead of one-giant-list-o-routes, and route namespaces. What if you have 100 routes?
* Easily share code between Blueprinte

```
app = Flask(__name__)

app.register_blueprint(page)
```

Current directory structure:

```
/config
/instance
/myflaskapp
   |__ /blueprints
      |__ /page
         |__ /templates
         |__ __init__.py
         |__ views.py
      |__ __init__.py
   |__ static
   |__ templates
   |__ __init__.py
   |__ app.py
/venv
```

In `/myflaskapp/blueprints/page/views.py`:

```
from flask import Blueprint, render_template
# create a blueprint named "page"
page = Blueprint("page", __name__, template_folder="templates")

# Note: attach route to the page instance
@page.route("/")
def home():
    return render_template("page/home.html")

@page.route("/terms")
def terms():
    return render_template("page/terms.html")
```

In `/myflaskapp/blueprints/page/__init__.py`:

```
# import blueprints upon import of this package
# this is just how __init__.py files work
from myflaskapp.blueprints.page.views import page
```
