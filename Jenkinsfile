pipeline {
    agent any

    options {
        skipDefaultCheckout(true)
    }

    tools {
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }

    stages {
        stage('Checkout main') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[
                        url: 'https://github.com/eyaa12345678/devops-project.git',
                        credentialsId: 'github-https-creds'
                    ]]
                ])
            }
        }

        stage('Maven Compile') {
            steps {
                dir('backend') {
                    sh 'mvn -version'
                    sh 'mvn compile'
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline SUCCESS'
        }

        failure {
            echo 'Pipeline FAILED'
        }
    }
}
