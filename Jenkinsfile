pipeline{
    agent any
    
    tools{
        jdk 'java-11'
        maven 'maven'
    }
    
    stages{
        stage('Git-checkout'){
            steps{
                git branch: 'master' , url: 'https://github.com/manjukolkar/web-application.git'
            }
        }
        stage('Code Compile'){
            steps{
                sh 'mvn compile'
            }
        }
        stage('Code Package'){
            steps{
                sh 'mvn clean install'
            }
        }
        stage('Build and tag'){
            steps{
                sh 'docker build -t shannu888/shanmukha .'
            }
        }
        stage('Containerisation'){
            steps{
                sh '''
                docker run -it -d --name c7 -p 9007:8080 shannu888/shanmukha 
                '''
            }
        }
           
    }
}
