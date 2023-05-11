---
sidebar_position: 1
---

# Quickstart guide

Let's discover **Ratio in less than 5 minutes**.

## Dev Quickstart

In dev mode you need to start two HTTP servers:

1. A frontend devserver with livereload and complie-time errors. 3000 port by default
2. A Scala backend server with DB connections. 8080 port by default

The frontend server cannot serve DB connections and make authenticated requests.
Thus backend allows proxying all requests coming to `/` onto 3000th port.

In practice it means that in order to do a proper full-stack development you need to run both servers.

```
sh> cd frontend
sh> npm install       # First time only
sh> npm start         # This will launch the frontend devserver
sh> cd ../            # Back to the repo root
sh> sbt
sbt> run run --config ../../config/reference.config.hocon   # Run with default config
```
