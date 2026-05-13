FROM node:20
EXPOSE 8080
ENV DB_HOST=mysql
# Install mysql-client as root
USER root
#RUN apt-get update && apt-get install -y mysql-client && rm -rf /var/lib/apt/lists/*
RUN apt-get update && apt-get install -y mariadb-client && rm -rf /var/lib/apt/lists/*

RUN useradd expense
RUN mkdir /opt/server
RUN chown expense:expense -R /opt/server 
WORKDIR /opt/server
COPY package*.json ./

RUN npm install
COPY . .
USER expense

CMD [ "node","index.js" ]