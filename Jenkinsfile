pipeline{
   agent any
   stages{
      stage("git clone"){
         steps{
            git url: "https://github.com/Cheerla25/spring-petclinic-test.git", branch: "main"
            }
        }
      stage("build"){
            steps{
                sh "mvn install"
            }
        }
        stage("archeive artifact"){
            steps{
                archiveArtifacts artifacts:"target/**.jar"
            }
        }
        stage("junit publish"){
            steps{
                junit "target/surefire-reports/*.xml"
            }
        }
        stage("sonar-qube"){
            steps{
                withSonarQubeEnv("sonar") {
                    sh "mvn clean install sonar:sonar"
                }

            }
        }
        stage("configuration"){
            steps{
                rtMavenResolver (
                    id: 'maven-resolver',
                    serverId: 'prashjfrog',
                    releaseRepo: libs-release,
                    snapshotRepo: libs-snapshot
                )

            }
        }
        stage('Build Maven Project') {
            steps {
                rtMavenRun (
                    tool: '/usr/share/maven',
                    pom: 'pom.xml',
                    goals: '-U clean install',
                    deployerId: "maven-deployer"
                )
            }
    }
}
