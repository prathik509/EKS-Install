pipeline {
    agent any
    
    environment {
        
        SCANNER_HOME = tool 'sonar-scanner'
    }
    
    stages {
        stage("Git Checkout") {
            steps {
                git branch: 'latest', url: 'https://github.com/prathik509/10-Tier-MicroService-Appliction.git'
            }
        }
        
        stage("SonarQube") {
            steps {
                withSonarQubeEnv('sonar') {
                    sh ''' $scanner_Home/bin/sonar-scanner -Dsonar.projectkey=10-Tier -Dsonar.projectName=10-Tier -Dsonar.java.binaries=. '''
                }
               
            }
        }
        
        stage("adservice") {
            steps {
               scripts{
                   withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                         dir ('/var/lib/jenkins/workspace/10-Tier/src/adservice'){
                               sh "docker build -t lucky509/adservice:latest"
                               sh "docekr push lucky509/adservice:latest"
                               sh "docekr rmi lucky509/adservice:latest"
                        }
                   }
               }
            }
        }
        
        stage("cartservice") {
            steps {
               scripts{
                   withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                         dir ('/var/lib/jenkins/workspace/10-Tier/src/cartservice/src'){
                               sh "docker build -t lucky509/cartservice:latest"
                               sh "docekr push lucky509/cartservice:latest"
                               sh "docekr rmi lucky509/cartservice:latest"
                        }
                   }
               }
            }
        }
        
        stage("checkoutservice") {
            steps {
               scripts{
                   withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                         dir ('/var/lib/jenkins/workspace/10-Tier/src/checkoutservice'){
                               sh "docker build -t lucky509/checkoutservice:latest"
                               sh "docekr push lucky509/checkoutservice:latest"
                               sh "docekr rmi lucky509/checkoutservice:latest"
                        }
                   }
               }
            }
        }
        
        stage("currencyservice") {
            steps {
               scripts{
                   withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                         dir ('/var/lib/jenkins/workspace/10-Tier/src/currencyservice'){
                               sh "docker build -t lucky509/currencyservice:latest"
                               sh "docekr push lucky509/currencyservice:latest"
                               sh "docekr rmi lucky509/currencyservice:latest"
                        }
                   }
               }
            }
        }
        
        stage("emailservice") {
            steps {
               scripts{
                   withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                         dir ('/var/lib/jenkins/workspace/10-Tier/src/emailservice'){
                               sh "docker build -t lucky509/emailservice:latest"
                               sh "docekr push lucky509/emailservice:latest"
                               sh "docekr rmi lucky509/emailservice:latest"
                        }
                   }
               }
            }
        }
        
        stage("frontend") {
            steps {
               scripts{
                   withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                         dir ('/var/lib/jenkins/workspace/10-Tier/src/frontend'){
                               sh "docker build -t lucky509/frontend:latest"
                               sh "docekr push lucky509/frontend:latest"
                               sh "docekr rmi lucky509/frontend:latest"
                        }
                   }
               }
            }
        }
        
        stage("loadgenerator") {
            steps {
               scripts{
                   withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                         dir ('/var/lib/jenkins/workspace/10-Tier/src/loadgenerator'){
                               sh "docker build -t lucky509/loadgenerator:latest"
                               sh "docekr push lucky509/loadgenerator:latest"
                               sh "docekr rmi lucky509/loadgenerator:latest"
                        }
                   }
               }
            }
        }
        
        stage("paymentservice") {
            steps {
               scripts{
                   withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                         dir ('/var/lib/jenkins/workspace/10-Tier/src/paymentservice'){
                               sh "docker build -t lucky509/paymentservice:latest"
                               sh "docekr push lucky509/paymentservice:latest"
                               sh "docekr rmi lucky509/paymentservice:latest"
                        }
                   }
               }
            }
        }
        
        stage("productcatalogservice") {
            steps {
               scripts{
                   withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                         dir ('/var/lib/jenkins/workspace/10-Tier/src/productcatalogservice'){
                               sh "docker build -t lucky509/productcatalogservice:latest"
                               sh "docekr push lucky509/productcatalogservice:latest"
                               sh "docekr rmi lucky509/productcatalogservice:latest"
                        }
                   }
               }
            }
        }
        
        stage("recommendationservice") {
            steps {
               scripts{
                   withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                         dir ('/var/lib/jenkins/workspace/10-Tier/src/recommendationservice'){
                               sh "docker build -t lucky509/recommendationservice:latest"
                               sh "docekr push lucky509/recommendationservice:latest"
                               sh "docekr rmi lucky509/recommendationservice:latest"
                        }
                   }
               }
            }
        }
        
        stage("shippingservice") {
            steps {
               scripts{
                   withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                         dir ('/var/lib/jenkins/workspace/10-Tier/src/shippingservice'){
                               sh "docker build -t lucky509/shippingservice:latest"
                               sh "docekr push lucky509/shippingservice:latest"
                               sh "docekr rmi lucky509/shippingservice:latest"
                        }
                   }
               }
            }
        }
        
        stage("k8.Deployment") {
            steps {
                withkubeConfig(-----------) {
                    sh 'kubectl apply -f deployment-service.yml'
                    sh 'kubectl get pods'
                    sh 'kubectl get svc'
                }
            }
        }
    
    
    
    }
}