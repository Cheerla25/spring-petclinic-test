pipeline{
agent any
stages{
    stage("git clone"){
        stages{
            git url: "https://github.com/Cheerla25/spring-petclinic-test.git",branch: "main"
        }
    }
    stages("build"){
        stage{
            steps{
                sh "mvn install"
            }
        }
    }
}
}