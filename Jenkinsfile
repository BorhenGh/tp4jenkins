pipeline {
    agent any 
    tools { 
        maven 'maven'
        nodejs 'NodeJS'
    }
    stages {
        stage ("Clean up"){
            steps {
                deleteDir()
            }
        }
        stage ("Clone repo"){
            steps {
                sh "git clone https://github.com/BorhenGh/tp4jenkins.git"
            }
        }
        stage ("Generate backend image with Spring") {
              steps {
                   dir("tp4jenkins/springboot/app"){
                       
                      sh "mvn clean install"
                      sh "docker build -t app ."
                  }                
              }
          }

       stage("Generate front image with Angular") {
            steps {
                dir("tp4jenkins/angular-app") {
                    sh "npm install"
                    sh "npm run build"
                    sh "docker build -t front ."
                }
            }
        }
        stage ("Run docker compose") {
            steps {
                 dir("tp4jenkins"){
                    sh " docker compose up -d"
                }                
            }
        }
    }
}
