# Simple Notes App
# Jenkins Declrative CI/CD Pipeline

This is a simple notes app built with React and Django. It is Deploy on AWS(EC2). 

## Requirements
**Development**
1. Python 3.9
2. Node.js
3. React
   
**Deployment**
1. Docker
2. DockerHub
3. AWS
4. Jenkins
5. Docker-compose

##  Declarative Pipeline
1. Clone the repository
```
git clone https://github.com/LondheShubham153/django-notes-app.git
```

2. Build the app
```
docker build -t notes-app .
```

3. Push to DockerHub with credentials
```
docker push ${env.dockerHubUser}/my-note-app:latest"
```

4. Deploy on EC2
```
docker-compose down && docker-compose up -d
```
