version : '2.1'
services:
  mysqldb:
    image: yuxiqian/eyulingo-mongodb:latest

    environment:
      MYSQL_ROOT_PASSWORD: 
      MYSQL_DATABASE: bookie
      MYSQL_USER: docker
      MYSQL_PASSWORD: 123456docker
    ports:
      - "3306:3306"
    container_name: mysqldb
    healthcheck:
      test: ["CMD", "mysqladmin" ,"ping", "-h", "localhost"]
      timeout: 20s
      retries: 10

  server:
    image: yuxiqian/bookie-server:latest
    ports:
      - "8080:8080"
    links:
      - mysqldb
    depends_on:
      mysqldb:
        condition: service_healthy
    container_name: server
    restart: always