pipeline{
    agent { node {label 'JDK-8'} }
    tools {
        jdk 'JDK8' 
    }
    parameters{
        choice(name: 'BRANCH', choices: ['master', 'dcpipeline'], description: 'this is parameter')
        string(name: 'mvn', defaultValue: 'package', description: 'this is maven goal')
    }
    triggers{
        pollscm ('* * * * *')
    }
    stages{
        stage('VCS'){
            steps{
                git branch: "${params.BRANCH}", url: 'https://github.com/GithubDevopS807/game-of-life.git'
            }
        }
        stage('BUILD'){
            steps{
               sh "mvn ${params.mvn}"
            }
        }
        stage('POST'){
            steps{
               junit '**/surefire-reports/*.xml'
            }
        }
    }
}