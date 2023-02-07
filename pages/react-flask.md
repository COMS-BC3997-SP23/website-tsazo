---
layout: default
---

[back](../index.html)

# Setting up the basics

### Summary

- Followed most of [this React & Flask tutorial](https://dev.to/nagatodev/how-to-connect-flask-to-reactjs-1k8i) to set up both the front and back end of the website.

![Flask bug](../assets/img/week1/flaskBug.png)

- Ran into an issue of flask not being imported properly? VS Code giving me a run for my money even though the installation was as simple as [following the official Flask installation.](https://flask.palletsprojects.com/en/2.2.x/installation/#)

  - I thought there were issues with Flask, but instead the IDE was giving non-fatal warnings that didn’t affect the local development server. Server ran on http://localhost:5000 without any problems.

- Ran into a seemingly easy (but annoying) CORS error but it was as simple as switching the proxy URL from http://localhost:3000 to http://127.0.0.1:5000, but nonetheless it took hours.

  - [Stack Overflow CORS Fix](https://stackoverflow.com/questions/45367298/could-not-proxy-request-pusher-auth-from-localhost3000-to-http-localhost500)
  - [GitHub CORS Fix](https://github.com/facebook/create-react-app/discussions/10149)

- Ultimately created my first React Flask app

### Background Research

#### What is React?

#### What is Flask?

#### What is Node.js?

#### Flask v.s. Node.js with React

| Topic                  | Flask                                                           | Node.js                                                                          |
| :--------------------- | :-------------------------------------------------------------- | :------------------------------------------------------------------------------- |
| Language               | Python                                                          | Chrome's V8 JS Engine                                                            |
| Architecture           | Non-blocking I/O requires non-blocking web servers              | Inherently provides non-blocking I/O                                             |
| Package Manager        | pip                                                             | npm                                                                              |
| Speed                  | Slower because of separate Python interpreter                   | Faster -> Just-In-Time compiler                                                  |
| Open Source            | Yes                                                             | Yes                                                                              |
| Community Support      | 2.3 K Watches, 51.4 K Stars, 13.7 K Forks on GitHub             | 2.9 K Watches, 71.9 K Stars, 17.6 K Forks                                        |
| Debugging              | Easier to Debug with Python debugger (no dependencies)          | Requires effort to debug but easier with IDE                                     |
| Maintenance            | Low                                                             | Higer (relatively)                                                               |
| Real-time applications | Inherently not suitable. Use socket.io for real-time use cases. | Inherently asynchronous                                                          |
| Libraries              | Mature and stable                                               | Less mature and stable                                                           |
| Code Quality           | It is exclusively created for the back end.                     | Sometimes compromised (frontend)                                                 |
| Integration            | Integration with existing system and applications               | Fairly new and requires the creation of custom or new libraries for integration. |

### Method

**Project directory**

Create the main project directory where the website will be stored

```
$ mkdir magic_tailors
$ cd magic_tailors
```

**React frontend setup**

Create the frontend react application by running:

```
$ npm create-react-app .
```

and then start the frontend application by running:

```
$ npm start
```

The default react application page should pop up in the browser; if not, paste the following link below in your browser:
**http://localhost:3000**

At this point, you should see the following:
![React setup](../assets/img/week1/pic1.png)

Now we’ll move onto setting up the backend portion of the React Flask app.

**Flask backend setup**
Create and navigate into a new directory in the magic_tailors directory:

```
$ mkdir backend
$ cd backend
```

### Virtual Environment

From here on out, it’s important to follow [Flask’s installation](https://flask.palletsprojects.com/en/2.2.x/installation/#) process. As noted there, virtual environments manage the dependencies for projects in both development and production. Virtual environments keep Python libraries independent from one another from project to project locally in an operating system.

**Create an environment**

Create a project folder and a venv folder within:

```
$ python3 -m venv venv
```

**Activate the environment**

Before working on the project, we need to activate it by running:

```
$ . venv/bin/activate
```

The shell prompt will change to show the name of the activated environment.

**Install Flask**

Within the activated environment, install Flask:

```
$ pip install Flask
```

Now Flask should be installed!

Staying in the backend directory, now create an app.py file.

```
$ touch app.py
```

Your folder structure will now look like 👇🏼
![Directory Outline](../assets/img/week1/directory.png)

In the app.py script, create a simple API that returns your name and “Hello, World!”:

```
from flask import Flask

api = Flask(__name__)

@api.route('/hello')
def hello_world():
    response_body = {
        "name": "Trinity",
        "hello" :"Hello, World!"
    }

    return response_body
```

The code above contains a simple API which would be called by the react front end to get the `response_body` dictionary.

You might have noticed two things:

1. GET http method is not specified here. Fortunately Flask's view functions accept GET requests by default.
2. `response_body` dictionary returned at the end of the function is not being passed as an argument like `jsonify(response_body)`. View functions in Flask automatically return a dictionary, which Flask then turns to JSON format.

Now, the backend has been successfully set up, you can test this by running your application.

```
flask run
```

Then navigate to the url **http://127.0.0.1:5000/hello**. You should see the dictionary `response_body` rendered in JSON format.
![Localhost5000 Python Server showing dictionary from code.](../assets/img/week1/pic2.png)

Add the following to your `.gitignore` file especially if you plan on pushing your code to Github.

```
/backend/venv
/backend/__pycache__
```

### Connecting Flask endpoint to React front end

Return to the main `magic_tailors` directory where the frontend is located:

```
cd ..
```

**Install `axios` library**

```
npm install axios
```

**`package.json`**

Open the `package.json` file and add a proxy below the "private": true, line. This enables the Flask server on your local machine to be accessed by any API requests made by the front end as well as enabling relative paths when making those calls. For example, instead of using **http://localhost:5000/hello** you can simply make use of **/hello**.

```
\\ At the start of the file

"name": "magic_tailors",
 "version": "0.1.0",
 "private": true,
 "proxy": "http://127.0.0.1:5000",
```
