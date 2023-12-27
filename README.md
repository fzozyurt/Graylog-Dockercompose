# Graylog Docker Compose files

## Prerequisites
- [Docker](https://docs.docker.com/engine/install/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Configure Graylog

All the [Graylog configurations](https://docs.graylog.org/docs/server-conf) can be set via environment variables. Just prefix the parameter name with `GRAYLOG_` and put it in upper case.

There is an environment file (`example.env`) where you can store these environment variables. Rename this to `.env` so Docker Compose will pick it up.

      cp example.env .env


**Important:** Be sure to to set the `GRAYLOG_PASSWORD_SECRET` and `GRAYLOG_ROOT_PASSWORD_SHA2` environment variables in the .env file! Graylog won't start without these.

## Starting Graylog

After you've configured `GRAYLOG_PASSWORD_SECRET` and `GRAYLOG_ROOT_PASSWORD_SHA2`, run these commands to start the instance:

    docker compose up

To start it daemonized, run:

    docker compose up -d

Default client port is `9000`. So now you can navigate to `http://localhost:9000`. 

Login:

      admin
      
Password: 

      admin
      

If you're running the DataNode and it's the initial startup, use 

      password from the logs of your first graylog node

as the password for the basic auth dialog to access the preflight/configuration UI. Use 

      <your password from GRAYLOG_ROOT_PASSWORD_SHA2>

after you configured graylog. If you have manually configured graylog to connect to OpenSearch directly, use

      <your password from GRAYLOG_ROOT_PASSWORD_SHA2>

because the preflight/configuration UI will not be shown.

## Create SHA2 Password


      pwgen -N 1 -s 96



## License

Graylog itself is licensed under the Server Side Public License (SSPL), see [license information](https://www.mongodb.com/licensing/server-side-public-license).

This Docker image is licensed under the Apache 2.0 license, see [LICENSE](LICENSE).
