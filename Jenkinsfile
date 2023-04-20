pipeline {
    agent any 
    stages {
        stage('cloning the url'){
            steps {
                git url: 'https://github.com/Cheerla25/spring-petclinic-test.git', branch: 'main'
            }
        }

        stage('build'){
            steps{
                sh 'mvn clean install'
            }
        }

        stage('archive artifacts'){
            steps{
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }

        stage('publish junit results') {
            steps{
                junit '**/surefire-reports/*.xml'
            }
        }

        stage('sonarqube analysis'){
            steps{
                 withSonarQubeEnv('sonarqube_server') {
                sh 'mvn clean package sonar:sonar'
              }
            }
        }

        stage('push to jfrog artifactory'){
            steps{
                 rtMavenDeployer (
                    id: 'MAVEN_DEPLOYER',
                    serverId: 'PRASHU_ID',
                    releaseRepo: 'libs-release-local',
                    snapshotRepo: 'libs-snapshot-local'
                )
            }
        }

        stage ('Exec Maven') {
            steps {
                rtMavenRun (
                    tool: 'MAVEN_DEFAULT', // Tool name from Jenkins configuration
                    pom: 'pom.xml',
                    goals: 'clean install',
                    deployerId: 'MAVEN_DEPLOYER'
                )
            }
        }
    }
}
