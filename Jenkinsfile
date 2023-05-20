@Library('my-shared-library') _ 

pipeline {
    agent any

    parameters{
        choice(name: 'action', choices: 'create\ndelete', description: 'create/Destroy')
        string(name: 'ImageName', description: "name of the docker build", defaultValue: 'javapp')
        string(name: 'ImageTag', description: "tag of the docker build", defaultValue: 'v1')
        string(name: 'DockerHubUser', description: "name of the Application", defaultValue: 'mohitdecoder')
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
        // stage('Unit test Maven'){
        //     when { expression { params.action == 'create'}}
        //     steps{
        //       script{
        //             mvnTest()
        //       }
        //     }
        // }
        
        // stage('Integration Test Maven'){
        //     when { expression { params.action == 'create'}}
        //     steps{
        //       script{
        //             mvnIntegrationTest()
        //       }
        //     }
        // }
        // stage('Static code analysis: SonarQube'){
        //     when { expression { params.action == 'create'}}
        //     steps{
        //       script{
        //            staticCodeAnalysis()
        //             // def SonarQubecredentialsId ='sonar'
        //             // staticcodeanalysis(SonarQubecredentialsId) 
        //       }
        //     }
        // }
        // stage('Quality Gate Status Check: SonarQube'){
        //     when { expression { params.action == 'create'}}
        //     steps{
        //       script{
        //            def SonarQubecredentialsId ='sonar'
        //            QualityGateStatus(SonarQubecredentialsId) 
        //       }
        //     }
        // }
        stage('Maven- Build'){
            when { expression { params.action == 'create'}}
            steps{
              script{
                    mvnBuild()
              }
            }
        }
        stage('Docker-Image_build'){
            when { expression { params.action == 'create'}}
            steps{
              script{
                    dockerBuild("${params.ImageName}","${params.ImageTag}","${params.DockerHubUser}")
              }
            }
        }
        stage('Docker-Image_scan'){
            when { expression { params.action == 'create'}}
            steps{
              script{
                    dockerBuild("${params.ImageName}","${params.ImageTag}","${params.DockerHubUser}")
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