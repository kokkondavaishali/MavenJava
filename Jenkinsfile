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
}
