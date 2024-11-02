@Library("Shared") _
pipeline {
    agent { label "vinod" }
    stages {
        stage("Hello") {
            steps {
                script {
                    hello()
                }
            }
        }
        stage("Code") {
            steps {
                script {
                    clone("https://github.com/Abhishek-28-eng/django-notes-app.git", "main")
                }
            }
        }
        stage("Build") {
            steps {
                script {
                    docker_build("notes-app", "latest", "abhishek280")
                }
            }
        }
        stage("Push to DockerHub") {
            steps {
                echo "This is pushing the image to DockerHub"
                script {
                    docker_push("notes-app", "latest", "abhishek280")
                }
            }
        }
        stage("Deploy") {
            steps {
                echo "This is deploying the code"
                sh "docker build -t notes-app:latest ."
            }
        }
    }
}
