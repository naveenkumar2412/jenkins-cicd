pipeline {
    environment {
    imagename = "backend"
    jenkinsProject = 'calculator-webapp-backend'
  }

    agent any
    stages {

        stage('Git production'){

            steps{

                checkout([$class: 'GitSCM', branches: [[name: '*/prod']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-multi', url: 'https://https://github.com/naveenkumar2412/jenkins-cicd']]])

            }
        }


        stage('Build image and Run image ') {

            steps{
                sh 'sudo su - jenkins -s/bin/bash'
                //sh 'sudo docker stop $imagename'
                //sh 'sudo docker rm $imagename'
                //sh 'sudo docker rmi $imagename'
                sh 'sudo docker image build -t  $imagename .'

            }

        }
        
        stage('Run image ') {

            steps{
                sh 'sudo docker run -p5000:5000 --restart=always --name $imagename  -itd $imagename'

            }

        }
        

        
    }
}
