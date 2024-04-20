pipeline{

    agent any

    stages{

        stage('get GitUrl'){
            steps{
                echo ${GIT_URL}
            }
        }

        stage('docker Build'){
            steps{
                sudo docker build -t sicei-${GIT_BRANCH}:1.0.0-${BUILD_NUMBER} .
            }
        }
    }

}