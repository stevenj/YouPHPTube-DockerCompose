# YouPHPTube-DockerCompose
Docker Compose configuration to run a YouPHPTube site.

# NO NONSENSE INSTALL GUIDE
1. Go to https://github.com/stevenj/YouPHPTube and follow the Non Nonsense Install Guide for that.
2. Go to https://github.com/stevenj/YouPHPTube-Encoder and follow the Non Nonsense Install Guide for that.
3. Clone this repository
```sh
$ git clone https://github.com/stevenj/YouPHPTube-DockerCompose.git
```
4. Change to the YouPHPTube-DockerCompose directory.
5. Modify the file docker-compose.yml to suit yourself.  Or leave it as is, with some easy defaults.
6. If you didn't modify the file, make a directory for the websites data:
```sh
$ sudo mkdir /srv/youphptube
$ sudo chmod ugo+rwx /srv/youphptube
$ sudo mkdir /srv/youphptube-encoder
$ sudo chmod ugo+rwx /srv/youphptube-encoder
```
5. Run your new YouPHPTube site:
```sh
$ docker-compose up -d
```
6. Run a browser and point it to <yourserver.ip>:8888
7. Configure it.
    * The database server name is not ```localhost```, it is ```mysql```
    * The encoder server name is ```youphptube-encoder```
    * Everything else is up to your preferences.

## Things you might want to change

The location where the servers store their files:
edit docker-compose.yml and change the ```/srv``` paths to suit your installation.  Make sure they exist and docker can read/write them (world writable is easiest).

The ports.  We default to Port 8000 in the container, and export it as port 8888 and 8889 for the main site, and the encoder respectively.  Just edit docker-compose.yml to suit yourself.  If you change the encoder, you need to change the configuration in the main site to point to it.

The Mysql passwords, because by default they are not very secure.  Just find them in the docker-compose.yml and set accordingly.  Then update your sites database configuration to match.