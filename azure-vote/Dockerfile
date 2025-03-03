#FROM tiangolo/uwsgi-nginx-flask:python3.6
#RUN pip install redis
#ADD /azure-vote /app

# -------- new ---------
# Using official python runtime base image
#FROM python:2.7
FROM hypriot/rpi-python:2.7

# Set the application directory
WORKDIR /app

# Install our requirements.txt
ADD requirements.txt /app/requirements.txt

RUN pip install -r requirements.txt

# Copy our code from the current folder to /app inside the container
#ADD . /app
ADD /azure-vote /app

# Make port 5000 available for links and/or publish
EXPOSE 80 

# Define our command to be run when launching the container
#CMD ["python", "app.py"]
CMD ["python", "/app/azure-vote/main.py"]

