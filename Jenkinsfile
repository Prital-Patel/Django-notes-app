pipeline {
    agent any

    stages {
        stage("Code") {
            steps {
                echo "Cloning the image"
                git url:"https://github.com/Prital-Patel/Django-notes-app.git", branch: "main"
            }
        }
        
     stage("Build") {
         steps {
                echo 'Building the image'
                sh "docker build -t notes-app ."
            }
     }
     
      stage("Push to Docker Hub") {
          steps {
                echo "Push to docker hub"
                withCredentials([usernamePassword(credentialsId:"dockerHub",passwordVariable:"dockerHubPass",usernameVariable:"dockerHubUser")]){
                sh "docker tag notes-app ${env.dockerHubUser}/notes-app:latest"
                sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPass}"
                sh "docker push ${env.dockerHubUser}/notes-app:latest"
                }
            }
      }
      
       stage("Deploy") {
           steps {
                echo "Deploy the image"
                sh "docker-compose down && docker-compose up -d"
            }
       }
        
    }
}
