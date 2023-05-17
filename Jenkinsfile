pipeline {
    agent any
    environment {
        PATH = "/bin/mvn:$PATH"
    }
    
    stages{
        stage("Get the code from GITHUB"){
            steps{
                git branch : 'main' , url : 'https://github.com/samu132/softwaremakers.git'
            }
        }
        
        stage("Build the Code"){
            steps{
                sh "mvn clean package"
            }
        }
        
        stage("Deploy the Code"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'B162186', path: '', url: 'http://15.206.74.189:8080')], contextPath: 'App', war: '**/*.war'
            }
        }
    }
}
