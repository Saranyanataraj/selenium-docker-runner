pipeline {
    agent any
    stages{
        stage("Pull Latest Image"){
            steps{
                sh "docker pull saranya93/selenium-docker"
            }    
        }
        stage("Start Grid"){
            steps{
                sh "docker-compose up -d hub chrome firefox"
            }
        }
        stage("Run Tests"){
            steps{
               sh "docker-compose up search-module1 search-module2 book-flight-module1 book-flight-module2" 
            }
        }
        // stage("Stop Grid"){
        //     steps{
        //         sh "docker-compose down"
        //     }

        // }
        }
    post {
        always {
            archiveArtifacts artifacts: 'output/**'
            sh "docker-compose down"
       }
    }
}