# Installing ngrok on Ubuntu
* Author:   Pedric Kng  
* Updated:  26 Jun 2020

***

## Installation

Snap is a simple way to install

1. Install snap
```bash
sudo apt update
sudo apt install snapd
```

2. Install ngrok via snap
```bash
sudo snap install ngrok
```

## Ngrok Configuration

Create the ngrok configuration as per [ngrok documentation](https://ngrok.com/docs)

[Sample ngrok configuration](ngrok.yml)

Note: the 'web_addr' configuration refers to ngrok web console.
By default, it is set to localhost for ubuntu interactive mode-only (UI).
For pure console, change it to an external url/ip address.

```bash
web_addr: 192.168.137.47:4040
```

## Config as service

1. Create a [Ngrok service file](ngrok.service) in /etc/systemd/system/

Enable ngrok service
```bash
sudo systemctl daemon-reload
sudo systemctl enable ngrok.service
```

Start ngrok service
```bash
sudo systemctl start ngrok
```

Check if ngrok service is up
```bash
sudo systemctl status ngrok
```

## Extract the tunnel url

1. Browse to http%3A%2F%2Flocalhost%3A4040 for the ngrok console.

2. Query via ngrok rest api

```bash
curl http://192.168.137.47:4040/api/tunnels
```

## References
Install ngrok using snap [[1]]  

[1]:https://snapcraft.io/install/ngrok/ubuntu "Install ngrok using snap"
