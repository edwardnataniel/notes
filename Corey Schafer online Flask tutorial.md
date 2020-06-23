# Corey Schafer's Online Flask Tutorial
[Tutorial Link](https://www.youtube.com/watch?v=MwZwr5Tvyxo&list=PL-osiE80TeTs4UjLw5MM6OjgkjFeUxCYH&index=1)

## Getting Started

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
