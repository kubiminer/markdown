# basic setups for ubuntu vps
https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-16-04

## ssh to vps
```linux
ssh root@192.243.113.243 -p 26972
```
## create a new user
```linux
# adduser karibu
# usermod -aG sudo karibu
```

### shadowsocks ssh
```
#!/bin/sh

#install pip and shadowsocks
sudo apt-get install -y python-pip
sudo pip install shadowsocks

#create shadowsocks scripts
echo "sudo ssserver -p 8388 -k [PASSWORD] -m aes-256-cfb --user nobody -d start" > ssstart.sh
echo "sudo ssserver -d stop" > ssstop.sh

#Permission
sudo chmod +x ssstart.sh ssstop.sh

#Open 8388 port
sudo ufw allow 8388

#start shadowsocks
./ssstart.sh
```
