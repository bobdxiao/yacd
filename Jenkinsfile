pipeline {

    agent any

    options {
        timeout(time: 30, unit: 'MINUTES')
    }

    stages {
        stage("Build Image"){
            steps{
                sh "docker build -t harbor.happylemon.life/lib/yacd:${BUILD_NUMBER} . "
            }
        }

        stage("Push Image"){
            steps{
                sh "docker push harbor.happylemon.life/lib/yacd:${BUILD_NUMBER} > /dev/null"
                sh "docker tag harbor.happylemon.life/lib/yacd:${BUILD_NUMBER} harbor.happylemon.life/lib/yacd:latest > /dev/null"
                sh "docker push harbor.happylemon.life/lib/yacd:latest > /dev/null"
            }
        }

        stage("Clean Image"){
            steps{
                sh "docker rmi harbor.happylemon.life/lib/yacd:${BUILD_NUMBER} > /dev/null"
                sh "docker rmi harbor.happylemon.life/lib/yacd:latest > /dev/null"
            }
        }

    }
}
