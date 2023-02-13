pipeline {
    agent {
        node any
    }

    stages {
        stage('Build Maven'){
            steps{
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/Tajamul-7/saliq.git']])
                sh 'mvn clean install'
            }
        }


        stage('Build Image') {
                steps{
                        script{
                                sh 'docker build -t saliqsyed/appimage1 .'
                        }
                }
        }



            // Jenkins Stage to Build the Docker Image.



        stage('Publish Image') {
                steps{
                        script{
                                 withCredentials([string(credentialsId: 'saliqsyed', variable: 'dockerhubpwd')])
                                                    sh 'docker push javatechie/devops-integration'


            // Jenkins Stage to Publish the Docker Image to Dockerhub.

                        }
                }

        }

}

