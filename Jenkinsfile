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
    }
}