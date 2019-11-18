# museoforteolimpio.ch web site based on Grav
The web-site is based on:
- Docker (https://www.docker.com)
- Grav modern open source flat-file CMS (https://getgrav.org/)
- Bootstrap theme for Grav CMS (https://github.com/getgrav/grav-theme-bootstrap)
- Grav LangSwitcher Plugin (https://github.com/getgrav/grav-plugin-langswitcher)

## Run the website
### Configure the environnement
create the `.env` file from the copy of `.env.dist`.
Replace path/to/user with the location of your user folder (in the cloned GIT folder).

### Run the server
```
docker-compose up
```

### URL
http://127.0.0.1:8000/

### Admin interface
http://127.0.0.1:8000/admin

## Admin account
username: admin
password: 12345678A%t

## Deploy in production
- downlaod the version 1.6.11 (core + admin plugin) of Grav (https://getgrav.org/)
- put the source in the webroot of the webserver
- copy the content of folder user in the webserver user folder
- login in the admin interface and change the admin password