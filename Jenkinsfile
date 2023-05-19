pipeline {
    agent any
    stages{
        stage('gitCheckout'){
            steps{
               git credentialsId: 'mohitjen', url: 'https://github.com/mohit-decoder/onlinebookstore.git'
            }
        }
    }
}