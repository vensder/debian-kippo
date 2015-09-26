# Kippo SSH Honeypot based on Debian image (196 Mb).

Move your real ssh port from default 22 to another (for ex. 22000)

##### Run this docker image by command:
```sh
sudo docker run -p 22:2222 -d \
  --name kippo vensder/debian-kippo-ssh-honeypot
```

##### You can view kippo logs from host by commands:
```sh
sudo docker logs kippo
sudo docker logs -f --tail 10 kippo 
```

##### Also you may use volume mounting for host user with uid:gid 1000:1000
```sh
sudo mkdir -p /home/kippo/log/tty
sudo chown -R 1000:1000 /home/kippo
sudo docker run -p 22:2222 -v /home/kippo/log:/home/kippo/log -d \
   --name kippo vensder/debian-kippo-ssh-honeypot
```

##### If you use SELinux on host system, you must change file SELinux security context:
```sh
sudo chcon -Rt svirt_sandbox_file_t /home/kippo
```

Logs will be write to /home/kippo/log/tty/ directory on your host system.
