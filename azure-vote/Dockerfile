#FROM tiangolo/uwsgi-nginx-flask:python3.6
#RUN pip install redis
#ADD /azure-vote /app

# -------- new ---------

FROM cseelye/rpi-nginx-uwsgi-flask

#RUN pip install redis
#FROM hypriot/rpi-redis

#FROM    tiangolo/uwsgi-nginx-flask:python3.6

RUN apt-get install lsb-release curl gpg
RUN curl -fsSL https://packages.redis.io/gpg | sudo gpg --dearmor -o /usr/share/keyrings/redis-archive-keyring.gpg
RUN chmod 644 /usr/share/keyrings/redis-archive-keyring.gpg
RUN echo "deb [signed-by=/usr/share/keyrings/redis-archive-keyring.gpg] https://packages.redis.io/deb $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/redis.list
RUN apt-get update
RUN apt-get install redis

#RUN  pip install redis
 
ADD /azure-vote /app

