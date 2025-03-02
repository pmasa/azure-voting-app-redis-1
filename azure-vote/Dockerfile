#FROM tiangolo/uwsgi-nginx-flask:python3.6
#RUN pip install redis
#ADD /azure-vote /app

# -------- new ---------

FROM cseelye/rpi-nginx-uwsgi-flask

RUN pip install redis
ADD /azure-vote /app
