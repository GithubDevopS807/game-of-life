pipeline{
    agent { node {label 'JDK-8'} }
      tools {
        jdk 'JDK8' 
    }
    stages{
        stage('VCS'){
            steps{
                git 'https://github.com/wakaleo/game-of-life.git'
            }
        }
        stage('BUILD'){
            steps{
               sh 'mvn package'
            }
        }
        stage('POST'){
            steps{
               junit '**/surefire-reports/*.xml'
            }
        }
    }
}