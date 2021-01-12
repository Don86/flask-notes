
## Config/Settings Files

check this out to load settings from settings files and config files:

```
app = Flask(__name__, instance_relative_config=True)
app.config.from_object("config.settings")
app.config.from_pyfile("settings.py, silent=True)
```

app structure:

```
/config
  |__ __init__.py
  |__ settings.py
/Instance
  |__ __init__.py
  |__ settings.py_prod_example
/myflaskapp
  |__ __init__.py
  |__ app.py
/venv
```

* `settings.py` can, for instance, contain just `DEBUG = True`. Note: NEVER run debug mode in prod!
* key-value pairs in `settings.py` can be set such as to be accessible as a dictionary. e.g. adding the line `HELLO = "hello world?"` in `settings.py` sets `app.config["HELLO"]="Hello world?`. Note that the keys must be in all caps.
* config/settings files are sensitive! Can contain db passwords, API keys, etc. /Instance/settings.py_prod_example is a file filled with nonsense examples to show what a `settings.py` file would look like in prod.
