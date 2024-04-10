**//Get localstack id**
docker ps

**// enter comtainer id**
docker exec -it <Container-ID> bash

docker exec -it dc4 sh  

** // run command**
aws --endpoint-url=[http://localhost:4566](http://localhost:4566/) s3api create-bucket --bucket my-bucket --no-sign-request