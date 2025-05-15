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


