pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Build') {
            steps {
                echo 'Building'
                bat 'build.bat'
                
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying'
              
            }
        }
        stage('Test') {
            steps {
                echo 'Testing '
                            }
        }
        stage('Release') {
            steps {
                echo 'Releasing'
                            
                
            }
        }
    }
}
