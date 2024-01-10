# Introduction

*Continued server-compose/proxy-server,* 

After setting up database with credentials for hedgedoc-server in *.env* using *init-db*,

```bash 
docker-compose up -d
```

After reloading proxy-server, hedgedoc-server will be accessible at http://localhost/hedgedoc.

## Configuration

### Access Database

```bash
(source .env && docker exec -it postgres-server psql -U "$DB_USER" -d "$DB_PASS")
```

### Log in Hedgedoc with Github

Before launching the server, in order to log in with GitHub account, pull the configuration file to configure it.

```bash 
docker run --rm quay.io/hedgedoc/hedgedoc cat /hedgedoc/lib/config/default.js > default.js
```

Go to [Github Developer Settings](https://github.com/settings/developers), create a new OAuth App, and put the client ID and secret in the github section in the *default.js*. It doesn't matter if the server is running on the localhost.

```js 
  github: {
    clientID: CLIENT_ID,
    clientSecret: CLIENT_SECRET
  },
```
