# tor

Based on hsaito's docker-torbox, but I ended up needing to make significant
modifications. Usage style inspired by the official elasticsearch Dockerfile.

## Example Usage:

Run tor as a user and get a socks proxy:

    dockr run --name tor-socks -p 9050:9050 -v $HOME/volumes/tor-socks:/var/lib/tor crccheck/tor

Run a custom configuration file:

First, have your own torrc file in ~/volumes/tor-relay/torrc, then:

    dockr run --name tor-relay --net=host \
      -v $HOME/volumes/tor-relay:/var/lib/tor crccheck/tor \
      tor -f /var/lib/tor/torrc

Generate a tor hashed password:

    dockr run --rm crccheck/tor tor --quiet --hash-password hunter2

References:

* https://github.com/hsaito/docker-torbox
* https://registry.hub.docker.com/u/dockerfile/elasticsearch/dockerfile/
* https://www.torproject.org/docs/tor-manual.html.en
