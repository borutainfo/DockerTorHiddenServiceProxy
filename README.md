# Docker Tor Hidden Service Proxy

Create simple darknet proxy to clearnet website using Docker container.

See example on [boruta.info](https://boruta.info/). Proxy request is sending additional header `x-tor`, which allows you to recognize the tor domain.  

## Setup

1. Clone repository:
    ```bash
    git clone git@github.com:borutainfo/DockerTorHiddenServiceProxy.git
    ```

2. Edit `tor/proxy.conf` and change `{YOUR_DOMAIN}` to clearnet domain you want to create proxy.

3. Edit `docker-compose.yml` and change `{YOUR_DOMAIN_PRIVATE_KEY}` to hidden service domain private key.
    
    If you do not have domain already generated you can comment out line in Dockerfile:
    ```dockerfile
    RUN echo "${PRIVATE_KEY}" > /var/lib/tor/proxy/private_key
    ```
    Domain will be generated automatically. You can read the hostname after docker-compose up, by command:
    ```bash
    docker exec dockertorhiddenserviceproxy_tor-server_1 cat /var/lib/tor/proxy/hostname
    ``` 

4. Run docker-compose:
    ```bash
    docker-compose up -d
    ```
