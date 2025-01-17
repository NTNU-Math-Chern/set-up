## :globe_with_meridians: Remote settings

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

> (rare case) I used SSH before on the same host computer, I re-installed it, and got some error while setting SSH again. The reason is there is some old information in the SSH configuration, you need to clean it.