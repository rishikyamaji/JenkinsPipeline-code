pipeline{

    agent any
    tools{
    
        jdk  'JAVA_HOME'
        maven 'maven'

    }
    options{
        timestamps()
     buildDiscarder(logRotator(artifactDaysToKeepStr: '10', artifactNumToKeepStr: '10', daysToKeepStr: '10', numToKeepStr: '10'))

    }
    stages{
        
        stage('checkout the source code'){
         steps{
             checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://rishikaymaji@bitbucket.org/iwayqtech/javaloginapp.git']]])
                 
         }
        }
        stage('building the source code using maven '){
            steps{
                sh 'mvn clean install package'

            }

        }
        stage('archive artifacts'){
            steps{
              archiveArtifacts artifacts: '**/**/*.war', followSymlinks: false
            }
        }
    }
}
