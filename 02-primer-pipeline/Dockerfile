FROM ubuntu:22.04

#ポートを開ける
EXPOSE 9864:9864

RUN apt update
RUN apt-get update
RUN apt -y upgrade
RUN apt install -y python3-pip
RUN apt-get install -y python3
RUN apt-get update -y

RUN apt install -y curl
RUN curl -o get-pip.py https://bootstrap.pypa.io/get-pip.py
RUN python3 get-pip.py
