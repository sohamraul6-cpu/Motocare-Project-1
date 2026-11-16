pipeline{
    agent any

    stages{

        // step1: github connection testing
        stage('github connection test'){
            steps{
                git branch: 'main',
                credentialsId: 'Motocare-Jenkins-ID',
                url: 'https://github.com/sohamraul6-cpu/Motocare-Project-1.git'

                echo 'github connection successful'
            }
        }

        // step2: checking all files
        stage('check files'){

            steps{

                sh 'ls -la'
            }
        }

        // step3: latest code from github 
        stage('checkout'){

            steps{
                checkout scm
                echo 'code downloaded from github'
            }
        }

        // step4: validation 
        stage('validate code'){
            steps{
                sh 'ls -la'
                sh 'test -f index.html'
                sh 'test -f Dockerfile'
                echo 'validation successful'
            }
        }

        // step5: docker image build 
        stage('docker image build'){
            steps{
                sh 'docker build -t motocare:latest .'
                echo 'docker image created'
            }
        }

        // step6: running docker container
        stage('deployment'){
            steps{
                sh 'docker rm -f motocare || true'
                sh 'docker run -d --name motocare --restart unless-stopped -p 80:80 motocare:latest'
                echo 'website deployment successful'

            }
        }
    }
}