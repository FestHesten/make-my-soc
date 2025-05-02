# Whoami

This is a whoami container created for traefik, it will show you the information regarding your connection to the endpoint. If you are looking for specific header or other things this will give you help to debug.

## Labels
This is the most basic labels for traefik. Enable it and give it a hostname!
``` 
    labels:
      - "traefik.enable=true"
      - "traefik.http.routers.whoami.rule=Host(`whoami.localhost`)"
``` 