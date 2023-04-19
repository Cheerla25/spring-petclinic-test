pipeline {
    agent any
    stages {
        stage('cloning the code'){
            steps{
                git branch: 'main' url: 'https://github.com/Cheerla25/spring-petclinic-test.git'
            }
        }

        stage('build'){
            steps{
                sh 'mvn package'
            }
        }

        stage('archive the artifacts'){
            steps{
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }

        stage('publish junit results'){
            steps{
                junit '**/surefire-reports/*.xml'
            }
        }

    }
}
