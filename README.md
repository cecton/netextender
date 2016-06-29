Dockerized NetExtender (command line)
=====================================

Usage
-----

```
# You need to run it in foreground in order to enter your credentials
docker run --privileged -it --rm --name myvpn \
    -v ~/.ssh/id_rsa.pub:/authorized_keys cecton/netextender


# Open a socks proxy on your machine using ssh
ip=$(docker inspect -f '{{ .NetworkSettings.IPAddress }}' myvpn)
ssh -fND 9050 root@$ip

# This will go into background and you will be able to connect through the VPN
# by changing the proxy settings to socks://localhost:9050

# You can also run Git through the VPN using proxychains
# (no configuration is required, proxychains uses localhost:9050 by default)
proxychains git clone ...

```
