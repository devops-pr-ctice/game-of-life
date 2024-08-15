pipeline {
    agent any
    tools{
        jdk 'jdk-8'
        maven 'MAVEN_3.9.8'
    }
    stages{
        stage('checkout'){
            steps{
                git branch: 'master',
                    url: 'https://github.com/wakaleo/game-of-life.git'
            }
        }
        stage('build'){
            steps{
                sh 'mvn clean package'
            }
        }
    }
    post{
        success{
            archiveArtifacts artifacts: '**/target/*.war'
            junit '**/target/surefire-reports/TEST-*.xml'
        }
    }
}