pipeline{

    agent any

    stages{

        stage('get GitUrl'){
            steps{
                echo '${GIT_URL}'
            }
        }

        stage('Build') {
            steps {
                sh 'npm install'
                sh 'npm run build'
                echo 'building...'
            }
        }

         stage('Test') {
            steps {
                echo 'yet to be implemented...'
                echo 'testing...'
            }
        }

        stage('Deploy'){
            steps{
                sh 'sudo docker build -t sicei-${GIT_BRANCH}:1.0.0-${BUILD_NUMBER} .'
                echo 'deploying...'
            }
        }
    }

}
