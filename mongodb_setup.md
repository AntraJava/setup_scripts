# 1. Docker Installation
* Make sure Docker is installed. Terminal run `docker info`.
* https://docs.docker.com/get-docker/

# 2. MongoDB 
* Open the terminal window.
* Start MongoDb using command:
`docker run -d -p 27017:27017 --name mongodb_sep -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=12345678 mongo:4.0.16 --auth`

* An instance of Mongodb will be started, username admin password 12345678
* Login to mongo cli using: `docker exec -it mongodb_sep mongo -u admin -p`
* Give password 12345678 then enter(terminal will not display the typing)
* Switch db:  `use sep_training` then enter
* Create user for sep collection
`db.createUser(
    {
        user: "sep_user",
        pwd: "aabbccdd",
        roles: [
           { role: "readWrite", db: "sep_training" }
        ]
    }
)`
* You should see "Successfully added user: {"user" : "sep_user","roles" : [{"role" : "readWrite","db" : "iot"}]}"
* Now we can use Spring or Robo3T to connect using
  - Url:`localhost:27017`
  - Db name : `sep_training`
  - `username: sep_user   password: aabbccdd`
