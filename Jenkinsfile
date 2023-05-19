@Library('my-shared-library') _ 

pipeline {
    agent any

    parameters{
        choice(name: 'action', choices: 'create\ndelete', description: 'create/Destroy')
    }
    stages{
        stage('gitCheckout'){
            when { expression { params.action == 'create'}}
            steps{
              script{
              gitCheckout(
                    branch:"master",
                    url:"https://github.com/mohit-decoder/onlinebookstore.git"
                )
              }
            }
        }
       
        stage('Unit test Maven'){
            when { expression { params.action == 'create'}}
            steps{
              script{
                    mvnTest()
              }
            }
        }
        
        stage('Integration Test Maven'){
            when { expression { params.action == 'create'}}
            steps{
              script{
                    mvnIntegrationTest()
              }
            }
        }
        
        stage('Static code analysis: SonarQube'){
            when { expression { params.action == 'create'}}
            steps{
              script{
                   staticCodeAnalysis()
              }
            }
        }
    }
}

// pipeline {
//     agent any
//     stages{
//         stage('gitCheckout'){
//             steps{
//                git 'https://github.com/mohit-decoder/onlinebookstore.git'
//             }
//         }
//     }
// }