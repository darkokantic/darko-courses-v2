FROM python:3.8-slim-buster

WORKDIR /opt/server

ENV DEBIAN_FRONTEND=noninteractive
RUN apt update && apt install -y postgresql libpq-dev gcc
RUN pip3 install flask
RUN pip3 install psycopg2
RUN pip3 install waitress
RUN pip3 install -U flask-cors

COPY code /opt/server

ENV PYTHONUNBUFFERED=1

ARG ARG_PG_HOST
ENV PG_HOST=$ARG_PG_HOST

ARG ARG_PG_PORT
ENV PG_PORT=$ARG_PG_PORT

ARG ARG_PG_DATABASE
ENV PG_DATABASE=$ARG_PG_DATABASE

ARG ARG_PG_USERNAME
ENV PG_USERNAME=$ARG_PG_USERNAME

ARG ARG_PG_PASSWORD
ENV PG_PASSWORD=$ARG_PG_PASSWORD

ARG ARG_DESTINATION_USERNAME
ENV DESTINATION_USERNAME=$ARG_DESTINATION_USERNAME

ARG ARG_DESTINATION_PASSWORD
ENV DESTINATION_PASSWORD=$ARG_DESTINATION_PASSWORD

EXPOSE 8080

CMD ["python3", "main.py"]