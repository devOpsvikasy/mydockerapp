pipeline{
    agent {label 'slave1'}
    //environment {
      //  PATH = "$PATH:/opt/apache-maven-3.8.2/bin"
    //}
    stages{
       stage('GetCode'){
            steps{
                git 'https://github.com/Sharath8000/mydockerapp.git'
            }
         }        
        stage('Docker image build'){
              steps {
                    sh 'docker build -t firstsapp .'
              }
         }
    }
}
