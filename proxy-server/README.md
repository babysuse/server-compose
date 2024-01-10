# Introduction

This is the centralized proxy server and database for all the servers. The main purpose of this is to add path matching functionality to the servers along with/instead of the port forwarding mechanism depending on using **`ports:`** or not. After setting admin databass credentials in *.env*, in order to launch it, run

```bash 
docker network create server-compose-network
docker-compose up -d
```

## Join an server

In order to utilize the proxy server,

* Join the network **`server-compose-network`**.
* If the database is involved, initialize the database by 
    ```bash
    ./init-db NEW_DB_USER NEW_DB_PASS [DATABASE]
    ```
    Then database will be accessible by **`postgres-server`**.

* After launching the application, add a new **`location`** section for the application and reload the proxy server by
    ```bash 
    docker exec proxy-server nginx -s reload
    ```
    There are two ways to set up **`proxy_pass`**.

    * Expose the application and then use **`localhost:POST`**.
    * Use the endpoint of the application which by default is the service name in the *docker-compose.yaml*.

## Backup the database

TBC
