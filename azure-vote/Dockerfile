#FROM tiangolo/uwsgi-nginx-flask:python3.6
#RUN pip install redis
#ADD /azure-vote /app

# -------- new ---------

# Set the base image
FROM balenalib/raspberry-pi

# File Author / Maintainer
#MAINTAINER Pedro 


## BEGIN INSTALLATION

# Install nginx
# Separate nginx user not required, as www-data account is already being used
RUN apt-get update && apt-get install -y nginx && apt-get -y clean

RUN pip install redis
ADD /azure-vote /app

# Copy start script
#COPY start-nginx.sh /opt/


## IMAGE CONFIGURATION

# Expose HTTP & HTTPS
EXPOSE 8888

# Update (optional) & start nginx
#CMD ["bash", "/opt/start-nginx.sh"]
CMD ["nginx", "-g", "daemon off;"]
