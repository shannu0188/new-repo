pipeline{
    agent any
    
    tools{
        jdk 'java-11'
        maven 'maven'
    }
    
    stages{
        stage('Git-checkout'){
            steps{
                git branch: 'master' , url: 'https://github.com/shannu0188/new-repo.git'
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
                docker run -it -d --name s1 -p 9004:8080 shannu888/shanmukha 
                '''
            }
        }
           
    }
}
