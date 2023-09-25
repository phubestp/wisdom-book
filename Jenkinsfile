pipeline {
    agent {
        docker {
            image 'maven:3-amazoncorretto-17'
            args '-v ' + pwd() + ':/workspace -p 33333:8090'
        }
    }

    stages {
        stage('Source') {
            steps {
                git branch: 'main',
                url: 'https://github.com/phubestp/wisdom-book'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                echo 'testing...'
            }
        }

        stage('Deploy') {
            steps {
                bat 'java -jar ./target/book-1.0.jar'
            }
        }
    }
}
