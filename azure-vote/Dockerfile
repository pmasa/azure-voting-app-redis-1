#FROM tiangolo/uwsgi-nginx-flask:python3.6
#RUN pip install redis
#ADD /azure-vote /app

# -------- new ---------
# Using official python runtime base image
#FROM python:2.7
FROM hypriot/rpi-python:2.7

# Pull base image
#FROM resin/rpi-raspbian:wheezy
MAINTAINER Dieter Reuter <dieter@hypriot.com>

# Install dependencies
#RUN apt-get update && apt-get install -y \
#    python \
#    python-dev \
#    python-pip \
#    python-virtualenv \
#    --no-install-recommends && \
#    rm -rf /var/lib/apt/lists/*

# Set the application directory
WORKDIR /app

# Install our requirements.txt
#ADD requirements.txt /app/requirements.txt
RUN sudo apt-get install python-pip
RUN pip install redis
RUN sudo pip install flask
RUN sudo pip install flask-socketio



#RUN pip install -r requirements.txt

# Copy our code from the current folder to /app inside the container
#ADD . /app
ADD /azure-vote /app

# Make port 5000 available for links and/or publish
EXPOSE 80 

# Define our command to be run when launching the container
#CMD ["python", "app.py"]
CMD ["python", "/app/azure-vote/main.py"]

