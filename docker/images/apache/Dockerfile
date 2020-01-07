# Base Image
FROM ubuntu:16.04

# Owner
MAINTAINER Amit Vashist <amitvashist.tech@gmail.com>

# Update the Package Repo. 
RUN apt-get update

# Install Apache Packages 
RUN apt-get install apache2 -y 

# Create New Index Page
COPY amit.html /var/www/html/index.html

# Excute the Apache Service
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
