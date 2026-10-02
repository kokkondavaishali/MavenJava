pipeline {
    agent any

    tools {
        jdk 'JDK21'
        maven 'MAVEN_HOME'
    }

    stages {
        stage('Git Repo & Clean') {
            steps {
                deleteDir()
                bat "git clone https://github.com/kokkondavaishali/MavenJava.git"
                bat "mvn clean -f MavenJava"
            }
        }

        stage('Install') {
            steps {
                bat "mvn install -f MavenJava"
            }
        }

        stage('Test') {
            steps {
                bat "mvn test -f MavenJava"
            }
        }

        stage('Package') {
            steps {
                bat "mvn package -f MavenJava"
            }
        }
    }

    post {
        success {
            emailext(
                subject: "Jenkins Build Successful: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The Jenkins build was successful.\n\nJob: ${env.JOB_NAME}\nBuild: #${env.BUILD_NUMBER}",
                to: "kokkondavaishali@gmail.com"
            )
        }

        failure {
            emailext(
                subject: "Jenkins Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The Jenkins build has failed.\n\nJob: ${env.JOB_NAME}\nBuild: #${env.BUILD_NUMBER}",
                to: "kokkondavaishali@gmail.com"
            )
        }
    }
}
