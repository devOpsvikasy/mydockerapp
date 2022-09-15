pipeline{
    agent {label 'slave1'}
    //environment {
      //  PATH = "$PATH:/opt/apache-maven-3.8.2/bin"
    //}
    stages{
       stage('GetCode'){
            steps{
               git 'https://github.com/devOpsvikasy/mydockerapp.git'
            }
         }        
        stage('Docker image build'){
              steps {
                    sh '''
                    
                    echo " *********** Building the image **************"
                    docker build -t firstsapp . 
                    
                    echo " ********** Login to Nexus DTR ************* "
                    docker login -u admin -p admin@123 http://34.228.78.173:9001/repository/dockerdtr/
                    
                    echo " ********** Tagging the image ************"
                    docker tag firstapp 34.228.78.173:9001/repository/dockerdtr/sharath-vikas-dtr/vikas-sharath:myapp.1.1                  
                    
                    echo "********** Push to Nexus DTR *************"
                    docker push http://34.228.78.173:9001/repository/dockerdtr/sharath-vikas-dtr/myfirstapp
                    
                    echo " ********** Logging out from  Nexus DTR *********** "
                    docker logout http://34.228.78.173:9001/repository/dockerdtr/
                    
                    echo "Image has been pushed to Nexus DTR"
                    
                    
                    
                    '''
              }
         }
    }
}
