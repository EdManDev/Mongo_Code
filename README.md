# Some mongo db code


localhost SRV: 

WINDOWS
``` t
  mongodb://localhost:27017/?readPreference=primary&appname=MongoDB%20Compass&directConnection=true&ssl=false
```

LINUX

``` t
  mongodb://mongo:mongo@localhost:27017?authSource=admin
```

-------------------------------------------------------------------------
.ENV (dotenv)

``` t
  DATABASE_NAME=<Database_Name>
  DATABASE_URI=mongodb+srv://<Name>:<pswd>@socialnetwork.scvl8.mongodb.net/<Database_Name>

  DATABASE_USERNAME=
  DATABASE_PASSWORD=
```

---
STRAPI LOCAL MONGO DB LOCAL

``` t
  module.exports = ({ env }) => ({
    defaultConnection: "default",
    connections: {
      default: {
        connector: "mongoose",
        settings: {
          host: env("DATABASE_HOST", "127.0.0.1"),
          srv: env.bool("DATABASE_SRV", false),
          port: env.int("DATABASE_PORT", 27017),
          database: env("DATABASE_NAME"),
          username: env("DATABASE_USERNAME"),
          password: env("DATABASE_PASSWORD"),
        },
        options: {
          authenticationDatabase: env("AUTHENTICATION_DATABASE", null),
          ssl: env.bool("DATABASE_SSL", false),
        },
      },
    },
  });
  
```

STRAPI LOCAL MONGO DB CLOUD

``` t

    module.exports = ({ env }) => ({
    defaultConnection: "default",
    connections: {
      default: {
        connector: "mongoose",
        settings: {
          uri: env("DATABASE_URI"),
          srv: env.bool("DATABASE_SRV", true),
          port: env.int("DATABASE_PORT", 27017),
          database: env("DATABASE_NAME"),
        },
        options: {
          authenticationDatabase: env("AUTHENTICATION_DATABASE", null),
          ssl: env.bool("DATABASE_SSL", true),
        },
      },
    },
  });

```
