pipeline{
    agent any
    tools {
        jdk 'jdk11'
        maven 'maven3'
    }
    environment {
        PRAGRA_INSTRUCTOR='Atin Singh'
    }
    options {
        buildDiscarder(logRotator(numToKeepStr: '3')) 
    }
    parameters { 
        choice(name: 'DEPLOY_ENV', 
        choices: ['UAT1', 'UAT2', 'UAT3'], 
        description: 'Select the env you want to deploy') 
    }
    stages {
        stage('Compile'){
            steps {
                sh 'mvn compile'
            }
        }
        
        stage('Test'){
            steps {
                sh 'mvn test'
            }
        }

        stage('Package'){
            steps {
                sh 'mvn package'
            }
        }
        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
    }


}