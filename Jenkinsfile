pipeline {
    agent any
    stages{
        stage('gitCheckout'){
            steps{
                scripts{
                    git branch: 'master', url: 'https://github.com/mohit-decoder/onlinebookstore.git'
                }
            }
        }
    }
}