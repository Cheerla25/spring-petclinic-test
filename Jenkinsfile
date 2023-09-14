pipeline {
    agent any
    stages{
        stage('cloning'){
            steps{
             branch: 'main', git_url: 'https://github.com/Cheerla25/spring-petclinic-test.git'
            }
        }

        stage('build'){
            steps{
                sh 'mvn package'
            }
        }
    }
}