pipeline {
    agent any
    tools {
        maven 'Maven'
   }
    stages {
        stage('Build') {
            steps { 
                snDevOpsStep()
                echo 'Build' 
                sh '''
                    export M2_HOME=/opt/apache-maven-3.6.0 # your Mavan home path
                    export PATH=$PATH:$M2_HOME/bin
                    mvn --version
                '''
                sh 'mvn compile' 
            }         
        }
        stage('Test') {
            steps { 
                snDevOpsStep()
                echo 'Test'
                sh '''
                    export M2_HOME=/opt/apache-maven-3.6.0 # your Mavan home path
                    export PATH=$PATH:$M2_HOME/bin
                    mvn --version
                '''
                sh 'mvn verify'
            }
            post {
                success {
                    junit '**/target/surefire-reports/*.xml' 
                }
            }       
        }        
    }
}

