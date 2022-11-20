############Docker Redis###################

###utilisation session utlisateurs

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
    set myKey Salut
    get myKey

// Key
    set user:1 Alban
    get user:1
    del user:1 return 1 for success
    get user:1 return (nil) entry not exist

// counter
    set counter 100
    incr counter
    (integer) 101
    incr counter
    (integer) 102
    incrby counter 50
    (integer) 152

    decr counter
    decrby counter 50

// multiple keys in a single command
    mset a 10 b 20 c 30
    mget a b c

// Exists
    set myKey Alban
    exits myKey
    (return 1)
    del myKey
    exits myKey
    (return 0)

// TTL (Time to live)
    set key 20
    TTL key
    (return -1)
    expire 10
    get key
    (return 20)
    get key (after 10 sec)
    (nil)

    set key Alban
    expire 20
    TTL key

//list
    rpush formations "CDA de Lyon" (on the right)
    lpush formations "CDA AIX-Nice" (on the left)
    lrange formations 0 -1
    rpush formations "CDA PARIS" "CDA BORDEAUX"

    lenght:
    LLEN formations

    del:
    LPOP formations
    RPOP formations
    del  formations

// Set (no repeat key)
    SADD users "Rob"
    SADD users "Robert"
    SADD users "ROB"

    List:
    SMEMBERS users

    del robert
    SREM users "Robert"

    find user
    SISMEMBER users "Robert"
    SISMEMBER users "Rob"


    SADD users2 "Fred" "Fredo" "Frederique"

    union (agréga):
    SUNION users users2

    All commande https://redis.io/commands/

// Set ord
    ZADD score 10 "Fred"
    ZADD score 30 "Marie"
    ZADD score 55 "Alban"

    ZRANGE score 0 -1
    ZREVRANGE score 0 -1

    Zrange 0 -1  withscores

// HASH
    HSET user:123 username "John doe"
    HSET user:123 age 35
    HSET user:123 mail "jdoe@gmail.com"

    HMSET user:124 username "ALbert" age "15" mail "albert@gamil.com"

    HGETALL user:123

//geo
    https://redis.io/commands/?group=geo

//pubsub (open 2 terminals)

    first terminal:
    Subscribe formations user:350

    second terminal:
    PUBLISH formations "Nouvelle formation REDIS pour les CDA"
    PUBLISH user:350 "Hello!!"

    https://redis.io/commands/?group=pubsub

    Ex:
    first terminal:
    PSUBSCRIBE user*
    second terminal:
    PUBLISH user "Hello the world"

//redis have 16 bdd
    Keys * (return all keys in the frist bdd)

    Select 1 (select another bdd)
    keys* return 0


 Peristence

    https://redis.io/docs/management/persistence/


 Manager Redis
    https://apps.microsoft.com/store/detail/another-redis-desktop-manager/9MTD84X0JFHZ?hl=fr-fr&gl=fr














