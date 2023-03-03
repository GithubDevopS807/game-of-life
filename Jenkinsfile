pipeline{
    agent { node {label 'JDK-8'} }
    tools {
        jdk 'JDK8' 
    }
    parameters{
        choice(name: 'BRANCH_TO_BUILD', choices: ['master', 'dcpipeline'], description: 'this is parameter')
        string(name: 'mvn_goal', defaultValue: 'package', description: 'this is maven goal')
    }
    stages{
        stage('VCS'){
            steps{
                git branch: '${params.BRANCH_TO_BUILD}', url: 'https://github.com/GithubDevopS807/game-of-life.git'
            }
        }
        stage('BUILD'){
            steps{
               sh 'mvn ${params.mvn_goal}'
            }
        }
        stage('POST'){
            steps{
               junit '**/surefire-reports/*.xml'
            }
        }
    }
}