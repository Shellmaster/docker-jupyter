# docker-jupyter

This is a very basic jupyter notebook docker that should go behind a proxy server

- Available kernels:

 -  python3    /usr/local/lib/python3.4/dist-packages/ipykernel/resources
 -  bash       /usr/local/share/jupyter/kernels/bash


Examples:

`docker run -ti --rm -p 127.0.0.1:8080:8080 -e url='user1' -h jupyter --name user1 shellmaster/docker-jupyter`

If you are running it behind a proxy then you need to specify an origin domain eg.:

`docker run -ti --rm -p 127.0.0.1:8080:8080 -e url='user1' -e origin='https://github.com' -h jupyter --name user1 shellmaster/docker-jupyter`

If you want to keep it in the background then eg.:

`docker run -d -p 127.0.0.1:8080:8080 -e url='user1' -e origin='https://github.com' -h jupyter --name user1 shellmaster/docker-jupyter`

Info:

Please remember to replace the 'user1' with a unique name to make sure that users from other images won't be able to access your session

then you will need to go to http(s)://YOUR_DOMAIN_OR_IP/user1/

Please note that all kernels are using web sockets so if you are proxying from Apache (httpd) then you need a mod_proxy_wstunnel.so and good 'RewriteRule's or ProxyPass conditions.

There are some cases where jupyter is stopping for a very long time or you might want to stop an instance when it's not being used by a user (after some inactivity) then you can use jup-stop script eg.:

`docker exec ID_OF_THE_INSTANCE jup-stop`

- TODO:

 - Add more info about mounting a "/notebook" volume for users
 - Add examples of rewrite rules
 - Add a link to a good GUI interface

If you are interested in more details please send me an email (look at the Dockerfile)

Good luck!
