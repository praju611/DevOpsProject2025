@Library('my-shared-library') _

pipeline{
    
    agent any
    parameters{

        choice(name: 'action', choices: 'create\ndelete', description: 'Choose create/Destroy')
    }
    stages{

        stage("Git Checkout"){
                    when { expression {  params.action == 'create' } }    
            steps{
            gitCheckout(
                branch: "main",
                url: "https://github.com/RutujaPawal/DevOps-Project-2023.git"
            )
            }
        }
        stage("Unit Test Maven"){
                when { expression {  params.action == 'create' } }
            steps{
               script{  
                   mvnTest()
               }
            }       
        }
        stage("Integration Test maven"){
            when { expression {  params.action == 'create' } }
            steps{
               script{  
                   mvnIntegrationTest()
               }
            }       
        }
        stage("Static code analysis: Sonarqube Test maven"){
            when { expression {  params.action == 'create' } }
            steps{
               script{  
                   statiCodeAnalysis()
               }
            }       
        }

        
    }    
}