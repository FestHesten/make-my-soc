# Tracecat
[Tracecat](https://www.tracecat.com/) is a [open source](https://github.com/TracecatHQ/Tracecat) SOAR system. 
## Intro
I've been using it for a while and little while now. Not a lot of integrations are built in but support for both writing your own Python integrations and extending the core modules is very powerfull.

I've created workflows and modules at work that I intend to re-create for the "MAKE-MY-SOC" project.

If you are building integrations and are interested in getting others to use them join their [Discord](https://discord.gg/n3GF4qxFU8) and talk to them or send them a PR on their [Github](https://github.com/TracecatHQ/Tracecat)



## Setup

To set the basics of the .env file follow the guide at https://docs.tracecat.com/self-hosting/deployment-options/docker-compose

For our usage we remove the caddy and run traefik as a reverse proxy as we can control it with labels for all our components.
Most of the settings are generated however some things we might want to update.
### Replacing Caddy

We remove caddy by setting up traefik to handle the requests to the UI and API containers separately:
```
  tracecat_api:
    labels:
      - "traefik.enable=true"
      - "traefik.docker.network=srv"
      - "traefik.http.routers.tracecat_api.rule=Host(`tracecat.${BASE_DOMAIN:-localhost}`) && PathPrefix(`/api`)"
  tracecat_ui:
      labels:
      - "traefik.enable=true"
      - "traefik.docker.network=srv"
      - "traefik.http.routers.tracecat.rule=Host(`tracecat.${BASE_DOMAIN:-localhost}`)"

```

