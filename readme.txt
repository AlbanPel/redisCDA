############Docker Redis###################

//docker

    docker pull redis

//start a redis instance

    docker run --name some-redis -d redis

//start with persistent storage

    docker run --name some-redis redis-server --save 60 1 --loglevel warning

//connect via redis cli

    docker run -it --network some-network --rm redis-cli -h some-redis

//connect cli in a container

    docker exec -it nameContainer bash
    redis-cli

//set and get
    set mykey somevalue
    get mykey
