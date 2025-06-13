# Expense using Docker

- Created infra using terraform

- Logged into superputty

- sudo su -

- clone this repo

- cd expenses-docker/terraform

- sh docker.sh

- Log out and login to server

- docker network create expense

- docker build -t mysql:v1.0 .

- docker run -d -p 3306:3306 --name mysql --network expense mysql:v1.0

- docker build -t backend:v1.0 .

- docker run -d -p 8080:8080 --name backend --network expense backend:v1.0

- docker build -t frontend:v1.0 .

- docker run -d -p 80:80 --name frontend --network expense frontend:v1.0

- Open the browser, enter IP. Website is ready

# If you want to deploy using docker compose

- docker stop `docker ps -a -q`

- docker rm `docker ps -a -q`

- docker network rm expense

- docker login

- docker tag mysql:v1.0 eswarsaikumar/mysql:v1.0

- docker tag backend:v1.0 eswarsaikumar/backend:v1.0

- docker tag frontend:v1.0 eswarsaikumar/frontend:v1.0

- docker push eswarsaikumar/mysql:v1.0

- docker push eswarsaikumar/backend:v1.0

- docker push eswarsaikumar/frontend:v1.0

- docker compose up -d 

- Open IP in browser, website is ready

# To delete

- docker compose down -d  

