# Traefik

[Traefik](https://doc.traefik.io/traefik/) is used as a [reverse proxy](https://en.wikipedia.org/wiki/Reverse_proxy) for this project.

We chose traefik for the ease of use when working with docker and you can get most things done in just a few labels that describe what you want to do. The simplest example will be the *whoami* component.

The basic usage will give you a subdomain on localhost or whatever DNS you give it.

# Security notice
The default configuration in this project is insecure, please remove `      - "--api.insecure=true"` if you are using a publicly accessable node.

## Labels
```
      #Unless enabled traefik dont care about your container. 
      - "traefik.enable=true"
      # the format is traefik.http.routers.<route_name>.rule=<rule>(<value>)
      - "traefik.http.routers.whoami.rule=Host(`whoami.localhost`)"
      #Specify the network that traefik should use (this should be srv for this project)
      - "traefik.docker.network=srv"
      #Specify a port for a service, this is then the default port for traefik.
      - "traefik.http.services.<service_name>.loadbalancer.server.port=8080"
```

## Other
Traefik is huge and can do MUCH MUCH more than I will ever do with it. I'm using it because it is easy and works well enough for this project.