# microservices

First run the service-registery service

After that, build and run the docker image using following steps:

# Build image
docker build -t question-service .

#run image
docker run -p 5000:5000 image-name(question-service)

## API Endpoints

### Question Service
- `GET /question/allQuestions` – Retrieve all questions
- `GET /question/category/{category}` – Retrieve questions by category

### Quiz Service
- `GET /quiz/get/{id}` – Retrieve quiz by ID

## Docker-compose file command

docker-compose up --build
docker-compose down

## Change below urls in question-service as well as in quiz-service :-

spring.datasource.url=jdbc:mysql://host.docker.internal:3306/questiondb 
spring.datasource.url=jdbc:mysql://host.docker.internal:3306/quizdb 

eureka.client.service-url.defaultZone=http://host.docker.internal:8761/eureka/
 


