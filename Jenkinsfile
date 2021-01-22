pipeline {
    agent any
    stages {
        stage('Clone Generator From Github'){
            steps{
                git branch: 'main',
                    url: 'https://github.com/JarlKDue/quarkus-gradle-template/'
            }
        }
        
        stage('Generate Project'){
            steps{
                sh './gradlew cleanArch generate -i -Dtarget=generated -Dgroup=com.xxx.yyy -Dname=dummy-service -Dversion=1.0-SNAPSHOT'
            }
        }
    }
}
