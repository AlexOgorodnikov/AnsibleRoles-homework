FROM ubuntu:20.04

#setting time zone
ENV TZ=Europe/Moscow
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

#set volume
VOLUME [ "/tmp/:/home/app/" ]

#update and app install
RUN apt-get -y update && apt-get install -y \
git \
maven

#setting directory and packaging
WORKDIR /home/app
RUN git clone https://github.com/boxfuse/boxfuse-sample-java-war-hello.git /home/app
RUN mvn package

#moving war file
WORKDIR /home/app/target
COPY /home/app/target/hello-1.0.war /tmp/hello-1.0.war