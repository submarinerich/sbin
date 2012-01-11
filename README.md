# sbin

A minimal scala pastebin backed by redis


## usage

### redis

Start your redis server

    > path/to/redis-version/redis-server

### sbin

Run with defaults

    rake run
  


---

**Note** This is legacy stuff I haven't enabled in the current build scripts - _candersonmiller_


Will start server at http://localhost:8079 with default login/password "admin"/"admin"

Run with provided username and password

    > sbt
    run jim:jam
    
Will start server at http://localhost:8080 with login/password "jim"/"jam"


Run with provided username and password and port

    > sbt
    run jim:jam 3000
    
Will start server at http://localhost:3000 with login/password "jim"/"jam"

