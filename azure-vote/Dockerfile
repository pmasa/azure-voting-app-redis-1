#FROM tiangolo/uwsgi-nginx-flask:python3.6
#RUN pip install redis
#ADD /azure-vote /app

# -------- new ---------

FROM cseelye/rpi-nginx-uwsgi-flask

#RUN pip install redis
#FROM hypriot/rpi-redis

#FROM    tiangolo/uwsgi-nginx-flask:python3.6

RUN  pip install redis-server
 
ADD /azure-vote /app

