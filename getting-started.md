# Getting Started with Flask

**Overview**

Flask is a micro web framework for building web applications in Python. It is designed to be simple and lightweight, but highly extensible. Flask is based on 2 Python libraries:

* [Werkzeug](http://werkzeug.pocoo.org/) - a toolkit for simplifying and abstracting the communication between web servers and web applications
* [Jinja2](http://jinja.pocoo.org/) - a template engine for rendering the final web pages of the web application

**Sections:**
* [Installing Flask](#installing-flask)
* [Hello World!](#hello-world)

---

## Installing Flask

Flask can be installed easily via `pip`, a Python package manager. If you don't have `pip` installed, run the following command in terminal:

```
sudo easy_install pip
```

Once that is taken care of, we can install Flask:

```
sudo pip install Flask
```

## Hello World!

With Flask installed, let's go ahead and make a simple web application that displays some text. Create a new file called `hello.py` in your favorite text editor/IDE.

> As Flask itself is written in Python, avoid naming any file `flask.py` to prevent name clashes.

Flask is simply a class in Python so we need to import it. For the first line, enter:

```py
from flask import Flask
```

Now we need to create an instance of Flask. This looks like:

```py
app = Flask(__name__)
```

This instance creates our WSGI application for communication between our local server and the web application we're building. The `__name__` parameter tells Flask where to look for resources and other dependencies.

> For more information on the First Parameter, see [Application Object](http://flask.pocoo.org/docs/0.10/api/#application-object).

Now we need to define what happens when someone connects to our web app. We'll handle this with the following line of code:

```py
@app.route('/')
```

> Routing is the process of mapping a URL (in this case, the root/index of our web app defined by `'/'`) to some code.

Next, let's give our app a purpose. For this simple tutorial, we just want to display a `string` of text. Python functions are prefixed with `def` and then followed by the function name, opening and closing parentheses, and a colon. In the function body, we simply return the string (`Hello World!`) we want to display.

```py
def hello_world():
    return 'Hello World!'
```

> We're not using any function parameters for this example, but they would be defined within the parentheses if we did.

Now we need to define how the web application is started. We want the app to only start from the Python interpreter (via our terminal) so add the following conditional statement:

```py
if __name__ == '__main__':
    app.run()
```

`run()` will start our web app and look for any code to execute defined by our earlier `route()` statement.

Our complete application should now look like:

```py
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello World!'

if __name__ == '__main__':
    app.run()
```

Let's try running it! In terminal, point your current directory to where you saved `hello.py` and run it using this command: `python hello.py`

If everything goes well, you should see:

```
$ python hello.py
 * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit)
```

But wait, where's our app? Let's try opening the URL (http://127.0.0.1:5000/) in a web browser.

There you have it! You've successfully built your first Python web application using Flask!

### Next Steps

You've built your first app, but it doesn't have much interaction. For something with a few more features, try this [tutorial](http://flask.pocoo.org/docs/0.12/tutorial/) on building a simple microblogging application.

You can also read about other features of [Flask](http://flask.pocoo.org/docs/0.12/) or dive straight into the [API](http://flask.pocoo.org/docs/0.12/api/). If you want to contribute directly to Flask, check out the project on [GitHub](https://github.com/pallets/flask).
