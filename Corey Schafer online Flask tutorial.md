# Corey Schafer's Online Flask Tutorial
[Tutorial Link](https://www.youtube.com/watch?v=MwZwr5Tvyxo&list=PL-osiE80TeTs4UjLw5MM6OjgkjFeUxCYH&index=1)

## Part 1 - Getting Started

* To run Flask, set environment variable to the file we want to our Flask app to be.

      export FLASK_APP=flaskblog.py
      flask run

* The address http://127.0.0.1/ has an alias called **localhost**. We can access localhost through http://localhost:5000/ where 5000 is the port number.

* By default, we need to restart the web server for the changes to take effect. To avoid repeatedly restarting the web server, we can run the app in debug mode. To do this, we can run `set FLASK_DEBUG=1` before `flask run`.

* To run the application through Python instead of setting environment variables, we can add this line of code:

      if __name__ == "__main__":
        app.run(debug=True)

  If we run the script directly with Python, then the value of __name__ will be "__main__". But if we import the this module to somewhere else, then __name__ will take the value of the name of the module.

  We can now run the application by running `python filename.py` in the command line.

* `@app.route('/')` is a Python decorator that Flask provides to assign URLs in our app to functions easily. We can use several routes/decorators for the same function.

* We can use `Ctrl+C` to stop the server from running.

* If we navigate to a route that does not exist, then a 404 response will be returned from the server.

## Part 2 - Templates
* In sublime text, type `html` then press tab to generate html structure.

* `import render_template`

* Call the `render_template('file.html')` function to render the template.

* Put all templates inside the **templates** folder.

* You may pass arguments in the render_template function. e.g `render_template('home.html', posts=posts)`

* Flask uses **Jinja 2** as templating engine. It allows us to write code with templates. For example, in app.py,
      posts = [
      	{
      		'title': 'Blog Post 1',
      		'content': 'First post content',
      	},
      	{
      		'title': 'Blog Post 2',
      		'content': 'Second post content',
      	}
      ]

      @app.route('/')
      @app.route('/home')
      def home():
          return render_template('home.html', posts=posts)

    In the home.html template,

      {% for post in posts %}
        <h1>{{ post.title }}</h1>
        <p>{{ post.content }}</p>
      {% endfor %}

* Template of a template
  * Write layout.html
  * In the individual homepages using the layout, include     
        {% extends "layout.html" %}
          {% block content_name %}
            {% for post in posts %}
              <h2>{{ post.title }}</h2>
        	  {% endfor %}
          {% endblock content_name %}
    * In layout.html, include `{% block content_name %}{% endblock %}`


* Bootstrap starter template
  https://getbootstrap.com/docs/4.3/getting-started/introduction/

  ## Part 3 - Forms and User Input

* To install wtforms
        pip install flask-wtf
Then,
        from flask_wtf import FlaskForm
* Forms will be written in Python and will be automatically converted into HTML code.

* Create a class per form and make it inherit from *FlaskForm*
      class RegistrationForm(FlaskForm)

* Classes within FlaskForm:
  * from wtforms import StringField
  * from wtforms import PasswordField
  * from wtforms import SubmitField
  * from wtforms import BooleanField
* Validators
  * from wtforms.validators import DataRequired
  * from wtforms.validators import Length
  * from wtforms.validators import Email
  * from wtforms.validators import EqualTo


* When using forms, we need to set a secret key to our application. It helps protect against modifying cookies, cross-site request forgery attacks.

* Getting a secret key
      import secrets
      secrets.token_hex(16)

We want to make this environment variable at some point.

* The **form.hidden_tag()** template argument generates a hidden field that includes a token that is used to protect the form against CSRF attacks. All you need to do to have the form protected is include this hidden field and have the SECRET_KEY variable defined in the Flask configuration.
