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
                sh 'chmod +x gradlew'
                sh './gradlew cleanArch generate -i -Dtarget=generated -Dgroup=${group} -Dname=${projectName} -Dversion=1.0-SNAPSHOT'
            }
        }
        stage('Create Github Repo'){
            steps{
                sh """curl -i -H "Authorization: token 9925bc361df753ef1db70c7add60229c2250c2c5" -d '{ "name": "${projectName}", "private": false}' https://api.github.com/user/repos"""
                // sh 'curl -i -H "Authorization: token 949a81058d7ea564c9cc2e3f10da33d9dfb8f2ec" -d \'{ "name": "${projectName}", "private": false}\' https://api.github.com/user/repos'
                }
        }
        stage('Push Code to Github Repo'){
            steps{
                dir('generated'){
                    sh 'git init'
                    sh 'git remote add origin git@github.com/KirkensgaardExamples/${projectName}.git'
                    sh 'git add .'
                    sh 'git commit -m "First Commit"'
                    sh 'git push https://KirkensgaardExamples:Right55HDuke@github.com/KirkensgaardExamples/${projectName}.git'
                }
            }
        }
    }
}
