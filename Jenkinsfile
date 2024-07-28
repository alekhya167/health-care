pipeline{
    agent any
    stages{
        stage('checkout the code from github'){
            steps{
                 git url: 'https://github.com/alekhya167/health-care/'
                 echo 'github url checkout'
            }
        }
        stage('codecompile with alekhya'){
            steps{
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }
        stage('codetesting with alekhya'){
            steps{
                sh 'mvn test'
            }
        }
        stage('qa with alekhya'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('package with alekhya'){
            steps{
                sh 'mvn package'
            }
        }
        stage('run dockerfile'){
          steps{
               sh 'docker build -t myimg .'
           }
         }
        stage('port expose'){
            steps{
                sh 'docker run -dt -p 8081:8081 --name c000 myimg'
            }
        }   
    }
}
