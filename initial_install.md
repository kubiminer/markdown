## install you os
goto: https://bwh1.net/ then `Client Area > my services >kiwiVM`


## system setting
```c
ssh root@192.243.113.243 -p[your_port_number]
adduser [username]
usermod -aG sudo [username]
exit

ssh [username]@192.243.113.243 -p[your_port_number]

sudo apt update
dudo apt -y upgrade

sudo apt install nano
sudo apt install ufw

sudo apt-get install python-pip python-m2crypto
export LC_ALL=C
sudo pip install shadowsocks
```

`sudo nano /etc/shadowsocks.json` Create configuration file at /etc/shadowsocks.json, with the following content,
```json
{
   "server":"[server ip address]",
   "server_port":8388,
   "local_port":0,
   "password":"[password]",
   "timeout":600,
   "method":"aes-256-cfb"
}
```
`sudo ssserver -c /etc/shadowsocks.json -d start`


## Auto Start on System Boot
If you want shadowsocks server to automatically start on system boot, then edit /etc/rc.local file `sudo nano /etc/rc.local`
Add the following line to the file above exit 0 line
`/usr/bin/python /usr/local/bin/ssserver -c /etc/shadowsocks.json -d start`

## ufw setting
```
sudo ufw allow ssh
sudo ufw allow http
sudo ufw allow https
sudo ufw allow 8388

sudo ufw enable
sudo ufw status
```
