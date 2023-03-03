pipeline{
    agent { node {label 'JDK-8'} }
      tools {
        jdk 'JDK8' 
    }
    stages{
        stage('VCS'){
            steps{
                git branch: 'dcpipeline', url: 'https://github.com/GithubDevopS807/game-of-life.git'
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