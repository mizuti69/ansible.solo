FROM python:3.8-buster

RUN apt update && apt -y upgrade

RUN apt install -y ansible vim git sshpass

RUN mkdir -p /app
WORKDIR /app
