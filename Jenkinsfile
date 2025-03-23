pipeline {
    agent {
        docker {
            image 'node:18' // Use Node.js Docker image as agent
            args '--user root' // Run as root inside the container
        }
    }
    stages {
        stage('Check Node.js Version') {
            steps {
                sh 'node -v'
                sh 'npm -v'
            }
        }
        stage('Build and Run App') {
            steps {
                script {
                    // Create a simple Node.js app
                    writeFile file: 'app.js', text: '''
                    console.log("Hello from Jenkins Docker Agent!");
                    '''
                }
                sh 'node app.js' // Run the app inside the Docker container
            }
        }
    }
}
