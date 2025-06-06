# IRIS-WEB

## Intro
THe DFIR-IRIS project is an open source Incindent Response system that is easy to work with.

It supports automation in the form of webhooks and can nicely interact with other systems. I prefer to use Tracecat for automation but sending hooks from IRIS can help a lot instead of polling to get information.

#### DOCS: https://docs.dfir-iris.org/latest/

### Configuration

To get started just copy the `.env.model` file to `.env`:
```
 cp .env.model .env
```
You might want to set/change the values of `IRIS_ADM_PASSWORD` to something you'd like to use. If you dont change the password will be in the logs of the cointainer _ON THE FIRST RUN_.

### Compose file

I've changed a bit in the compose file, such as commenting out the nginx service. But in general this is just to make sure that the project can run with traefik instead of the local nginx.

``` 
  app:
    ...
    labels:
      - "traefik.enable=true"
      - "traefik.docker.network=srv"
      - "traefik.http.routers.iris.rule=Host(`iris.${BASE_DOMAIN:-localhost}`)"
      - "traefik.http.services.iris.loadbalancer.server.port=8000"

    networks:
      - iris_backend
      - srv
``` 

