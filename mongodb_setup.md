# Install docker
### Download and install docker for your OS (I use docker desktop)

# Lunch docker
### Its important that docker is running, otherwise commands below will not work.

# Run mongoDB using docker

1. change path in your terminal to place where docker-compose.yaml is 

2. run docker using docker-compose.yaml as default with flag -d so its detached and we can use commandline

        docker compose up -d

3. Go to url with api in nodejs with localhost set up in the .yaml file
http://localhost:8081/

4. Use this command to show all containers of your docker:

        docker ps

5. pick container_ID of your mongoDB and run this command

        docker exec -it <container_ID> bash

`For me it was:`

        docker exec -it ae2805b20c8d bash

# Adding collections:

1. copy files to docker:

        docker cp yelp-samples\business.json ae2805b20c8d:/tmp/business.json
        docker cp yelp-samples\checkin.json ae2805b20c8d:/tmp/checkin.json
        docker cp yelp-samples\review.json ae2805b20c8d:/tmp/review.json
        docker cp yelp-samples\tip.json ae2805b20c8d:/tmp/tip.json
        docker cp yelp-samples\user.json ae2805b20c8d:/tmp/user.json

2. Add collections to db on docker

    ## In general
        mongoimport --uri=mongodb://<username>:<userpass>@localhost:27017/<db-name>?authSource=admin --collection=<collection-name> --file=/tmp/<filename>.json
    ---
    ## Here

        mongoimport --uri=mongodb://rootuser:rootpass@localhost:27017/samples?authSource=admin --collection=business --file=/tmp/business.json

        mongoimport --uri=mongodb://rootuser:rootpass@localhost:27017/samples?authSource=admin --collection=checkin --file=/tmp/checkin.json

        mongoimport --uri=mongodb://rootuser:rootpass@localhost:27017/samples?authSource=admin --collection=review --file=/tmp/review.json

        mongoimport --uri=mongodb://rootuser:rootpass@localhost:27017/samples?authSource=admin --collection=tip --file=/tmp/tip.json

        mongoimport --uri=mongodb://rootuser:rootpass@localhost:27017/samples?authSource=admin --collection=user --file=/tmp/user.json

# Connect to mongo shell

        mongo mongodb://localhost:27017 -u rootuser -p rootpass