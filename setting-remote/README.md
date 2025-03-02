## :globe_with_meridians: Remote settings

### SSH

```shell
sudo apt install -y openssh-server
sudo service ssh start
```

Suppose you have a `<STATIC_IP>` for the host computer. You should be able to connect with

```shell
ssh <USER>@<STATIC_IP>
```


If you are using a router, go to **DHCP settings** or **Address Reservation** and assign a `<ROUTER_STATIC_IP>` to your host computer. Then, go to the **Port Forwarding** or **NAT** to add a port on `<ROUTER_STATIC_IP>` with
- external port: `<PORT>` (router to host)
- internel port: 22 (default SSH port)

```shell
ssh <USER>@<STATIC_IP> -p <PORT>
```

> (rare case) I used SSH before on the same host computer, I re-installed it, and got some error while setting SSH again. The reason is that there is some old information in the SSH configuration, you need to clean it.

### VSCode server

```shell
curl -fsSL https://code-server.dev/install.sh | sh
```

Generate a configuration file by running `code-server`. Quit it. Modify the configuration file:
```shell
vim ~/.config/code-server/config.yaml
```
You should see this
```
bind-addr: 127.0.0.1:8080  
auth: password       
password: <RANDOM_PASSWORD> 
cert: false 
```
Change it to
```
bind-addr: 0.0.0.0:<PORT>  
auth: password       
password: <CUSTOM_PASSWORD> 
cert: false 
```

If you are using a router, go to **DHCP settings** or **Address Reservation** and assign a `<ROUTER_STATIC_IP>` to your host computer. Then, go to the **Port Forwarding** or **NAT** to add a port on `<ROUTER_STATIC_IP>` with
- external port: `<PORT>` (router to host)
- internel port: `<PORT>` (code-server port)

### systemd service
The following is to auto-run `code-server` at boot on Ubuntu by setting it up as a systemd service.
```shell
sudo touch /etc/systemd/system/code-server.service
sudo vim /etc/systemd/system/code-server.service
```
Write this in your service file
```
[Unit]
Description=Code-Server
After=network.target

[Service]
Type=simple
User=chern
ExecStart=/usr/bin/code-server
Restart=always

[Install]
WantedBy=multi-user.target
```

Then run 
```shell
sudo systemctl enable code-server
sudo reboot
```

You should be able to access `code-server` after booting.