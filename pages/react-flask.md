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

- Ran into a seemingly easy (but annoying) CORS error but it was as simple as switching the proxy URL from http://localhost:3000 to http://127.0.0.1:5000

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
