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
        
        stage('Sonar Analysis') {
            steps {
                withSonarQubeEnv('sonar') {
                    sh ''' 
                    $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=10-tier -Dsonar.java.binaries=. -Dsonar.projectKey=10-tier '''
                }
            }
        }
        
        stage('adservice') {
            steps {
                script {
                withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                      dir('/var/lib/jenkins/workspace/10-tier/src/adservice') {
                           sh "docker build -t lucky509/adservice:latest ."
                           sh "docker push lucky509/adservice:latest"
                           sh "docker rmi lucky509/adservice:latest"
                        }
                   }
               }
            }
        }
        
        stage('checkoutservice') {
            steps {
                script {
                withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                      dir('/var/lib/jenkins/workspace/10-tier/src/checkoutservice') {
                           sh "docker build -t lucky509/checkoutservice:latest ."
                           sh "docker push lucky509/checkoutservice:latest"
                           sh "docker rmi lucky509/checkoutservice:latest"
                        }
                   }
               }
            }
        }
        
        stage('currencyservice') {
            steps {
                script {
                withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                      dir('/var/lib/jenkins/workspace/10-tier/src/currencyservice') {
                           sh "docker build -t lucky509/currencyservice:latest ."
                           sh "docker push lucky509/currencyservice:latest"
                           sh "docker rmi lucky509/currencyservice:latest"
                        }
                   }
               }
            }
        }
        
        stage('emailservice') {
            steps {
                script {
                withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                      dir('/var/lib/jenkins/workspace/10-tier/src/emailservice') {
                           sh "docker build -t lucky509/emailservice:latest ."
                           sh "docker push lucky509/emailservice:latest"
                           sh "docker rmi lucky509/emailservice:latest"
                        }
                   }
               }
            }
        }
        
        stage('frontend') {
            steps {
                script {
                withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                      dir('/var/lib/jenkins/workspace/10-tier/src/frontend') {
                           sh "docker build -t lucky509/frontend:latest ."
                           sh "docker push lucky509/frontend:latest"
                           sh "docker rmi lucky509/frontend:latest"
                        }
                   }
               }
            }
        }
        
        stage('loadgenerator') {
            steps {
                script {
                withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                      dir('/var/lib/jenkins/workspace/10-tier/src/loadgenerator') {
                           sh "docker build -t lucky509/loadgenerator:latest ."
                           sh "docker push lucky509/loadgenerator:latest"
                           sh "docker rmi lucky509/loadgenerator:latest"
                        }
                   }
               }
            }
        }
        
        stage('paymentservice') {
            steps {
                script {
                withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                      dir('/var/lib/jenkins/workspace/10-tier/src/paymentservice') {
                           sh "docker build -t lucky509/paymentservice:latest ."
                           sh "docker push lucky509/paymentservice:latest"
                           sh "docker rmi lucky509/paymentservice:latest"
                        }
                   }
               }
            }
        }
        
        stage('productcatalogservice') {
            steps {
                script {
                withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                      dir('/var/lib/jenkins/workspace/10-tier/src/productcatalogservice') {
                           sh "docker build -t lucky509/productcatalogservice:latest ."
                           sh "docker push lucky509/productcatalogservice:latest"
                           sh "docker rmi lucky509/productcatalogservice:latest"
                        }
                   }
               }
            }
        }
        
        stage('recommendationservice') {
            steps {
                script {
                withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                      dir('/var/lib/jenkins/workspace/10-tier/src/recommendationservice') {
                           sh "docker build -t lucky509/recommendationservice:latest ."
                           sh "docker push lucky509/recommendationservice:latest"
                           sh "docker rmi lucky509/recommendationservice:latest"
                        }
                   }
               }
            }
        }
        
        stage('shippingservice') {
            steps {
                script {
                withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                      dir('/var/lib/jenkins/workspace/10-tier/src/shippingservice') {
                           sh "docker build -t lucky509/shippingservice:latest ."
                           sh "docker push lucky509/shippingservice:latest"
                           sh "docker rmi lucky509/shippingservice:latest"
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
    
    
    
