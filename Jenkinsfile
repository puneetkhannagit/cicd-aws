pipeline {
    agent any

    stages {

        stage('Checkout from GitHub') {
            steps {
                // Checkout main branch
                git branch: 'main', url: 'https://github.com/puneetkhannagit/cicd-aws.git'
            }
        }

        stage('Build with Maven') {
            steps {
                dir("${env.WORKSPACE}") {
                    // Build project, skip tests
                    bat 'mvn clean package -DskipTests=true'

                    // Print where the JAR was built
                    bat 'echo Built JAR(s) in: %cd%\\target'
                    bat 'dir "%cd%\\target\\*.jar"'
                }
            }
        }
    }

    post {
        success {
            echo "Build successful."
        }
        failure {
            echo "Build failed."
        }
    }
}
