pipeline{
    agent any
    environment {
        PATH = "$PATH:/opt/maven/apache-maven-3.9.9/bin"
    }
    stages{
       stage('GetCode'){
            steps{
                git 'https://github.com/ammy-git/hello-world.git'
            }
         }        
       stage('Build'){
            steps{
                sh 'mvn clean package'
            }
         }
        stage('SonarQube analysis') {
//    def scannerHome = tool 'SonarScanner 4.0';
        steps{
        withSonarQubeEnv('sonar') { 
        // If you have configured more than one global server connection, you can specify its name
//      sh "${scannerHome}/bin/sonar-scanner"
        sh "mvn sonar:sonar"
    }
        }
        }
       
    }
}
