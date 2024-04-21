pipeline{
    agent any

    stages{
        stage('get GitUrl'){
            steps{
                echo "${GIT_URL}"
            }
        }

        stage('Build') {
            steps {
                sh 'npm install'
                echo 'building...'
                sh "RAMA=$(echo ${GIT_BRANCH} | cut -b 8-14 | tr '[:upper:]' '[:lower:]' | tr '/' '_')"
                sh 'sudo docker build -t sicei-${GIT_BRANCH}:1.0.0-${BUILD_NUMBER} .'
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
                echo 'deploying...'
                sh 'sudo docker run -d --name sicei-${GIT_BRANCH} -p 3000:3000 sicei-${GIT_BRANCH}:1.0.0-${BUILD_NUMBER}'
            }
        }
    }

}
