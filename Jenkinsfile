pipeline {
    agent any

    stages {
        stage('Git checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/engrbayo/Jenkins-marvins-practise.git']]])
            }
        }
        stage('Build with Maven') {
            steps {
                echo 'cd MyWebApp && mvn clean install'
            }
        }
        stage('Third stage') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'sonar-file', path: '', url: 'http://3.89.187.211:8080/')], contextPath: 'myapp', war: '**/*.war'
            }
        }
    }
}
