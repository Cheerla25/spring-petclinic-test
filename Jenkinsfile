pipeline {
    agent any
    stages{
        stage('cloning'){
            steps{
             git_url: 'https://github.com/Cheerla25/spring-petclinic-test.git', branch: 'main'
            }
        }

        stage('build'){
            steps{
                sh 'mvn package'
            }
        }
    }
}