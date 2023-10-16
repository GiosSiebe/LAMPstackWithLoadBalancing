# LAMPstackWithLoadBalancing
I made a LAMP stack with Docker that runs Apache2 that shows an PHP website, where the index.php file is on the host system. I used an Ubuntu 22.04 virtual machine to run this configuration on. The file takes data out of another container that runs MySQL. I also userd load balancing with nginx.

The first container is based on an Ubuntu 22.04 and is a custom image. It installs and runs Apache2 and PHP on it. It gets its webpages from the host machine instead of on the guest machine itself. This container is connected to a second container.

The second container is a MySQL container that just uses the latest image from Docker HUB. We just change the permissions on the SQL files so that PHP can connect to the database. We make the data persistent, so it stays when we delete the containers.

For loadbalancing we use NGINX. We make a second containr for our webserver and balance the load over these 2 containers.
