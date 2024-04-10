pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/Prakashkuvvam/spring-pet-clinic.git'
            }
        }
        
        stage('Compile') {
            steps {
                sh "mvn clean compile"
            }
        }
        
        stage('Test') {
            steps {
                sh "mvn test"
            }
        }
        
        stage('Sonar Analysis') {
            steps {
                sh ''' mvn sonar:sonar \
                        -Dsonar.projectKey=vprofile \
                        -Dsonar.host.url=http://54.234.251.47:9000 \
                        -Dsonar.login=c8eef3e8caf47716a8c98d5564c51b06a12c8c2b '''
            }
        }
        
        stage('Build') {
            steps {
                sh "mvn clean install"
            }
        }   
    }
}

