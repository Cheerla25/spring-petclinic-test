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
    }
}
