**New: [wireguard-install](https://github.com/Nyr/wireguard-install) is also available.**

## openvpn-install
OpenVPN [road warrior](http://en.wikipedia.org/wiki/Road_warrior_%28computing%29) installer for Ubuntu, Debian, CentOS and Fedora.

This script will let you set up your own VPN server in no more than a minute, even if you haven't used OpenVPN before. It has been designed to be as unobtrusive and universal as possible.

### Installation
Run the script and follow the assistant:

`wget https://git.io/vpn -O openvpn-install.sh && bash openvpn-install.sh`

Once it ends, you can run it again to add more users, remove some of them or even completely uninstall OpenVPN.

### I want to run my own VPN but don't have a server for that
You can get a VPS from just $1/month at [VirMach](https://billing.virmach.com/aff.php?aff=4109&url=billing.virmach.com/cart.php?gid=18).

### Donations

If you want to show your appreciation, you can donate via [PayPal](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=VBAYDL34Z7J6L) or [cryptocurrency](https://pastebin.com/raw/M2JJpQpC). Thanks!

ps aux | grep openvpn
kill -9 12862

local 10.0.0.13
port 1194
proto tcp
dev tun
ca ca.crt
cert server.crt
key server.key
dh dh.pem
auth SHA512
tls-crypt tc.key
topology subnet
server 10.8.0.0 255.255.255.0
;push "redirect-gateway def1 bypass-dhcp" 注释掉全局代理
ifconfig-pool-persist ipp.txt
;push "dhcp-option DNS 183.60.83.19" 注释掉全DNS
;push "dhcp-option DNS 183.60.82.98"
client-to-client
keepalive 10 120
cipher AES-256-CBC
user nobody
group nobody
persist-key
persist-tun
verb 3
crl-verify crl.pem


openvpn --daemon --config /etc/openvpn/server/server.conf
