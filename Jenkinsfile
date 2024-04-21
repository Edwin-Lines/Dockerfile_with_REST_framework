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
                sh 'CONTAINER_ID=$(sudo docker ps -a -q --filter="name=sicei-${GIT_BRANCH}")'
                sh 'if [ -n "$CONTAINER_ID" ]; then'
                sh 'sudo docker stop "$CONTAINER_ID"'
                sh 'sudo docker rm "$CONTAINER_ID"'
                sh 'else'
                sh 'echo "El contenedor no existe."'
                sh 'fi'
                sh 'sudo run -d --name sicei-${GIT_BRANCH} -p 3000:3000 sicei-${GIT_BRANCH}:1.0.0-${BUILD_NUMBER}'
            }
        }
    }

}
