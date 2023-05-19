@Library{'my-shared-library'} _ 

pipeline {
    agent any
    stages{
        stage('gitCheckout'){
            steps{
              script{
                gitCheckout{
                    branch: "master",
                    url: "https://github.com/mohit-decoder/onlinebookstore.git"
                }
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