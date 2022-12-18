pipeline{
    agent any
    stages{
        stage('Git Checkout'){
            steps{
                script{
                    git branch: 'main', url: 'https://github.com/99North/kubernetes_java_deployment-praveen1994dec.git'
                }
            }
        }
    
        stage('Parallel Build'){
            parallel{
                stage('Poductcatlogue mvn Build'){
                    steps{
                        script{
                            sh 'cd /var/lib/jenkins/workspace/java-deployment/productcatalogue/ && mvn clean install -DskipTests'
                        }
                    }
                }
                stage('Shopfront mvn Build'){
                    steps{
                        script{
                            sh 'cd /var/lib/jenkins/workspace/java-deployment/shopfront/ && mvn clean install -DskipTests'
                        }
                    }
                }
                
                stage('Stockmanager mvn Build'){
                    steps{
                        script{
                            sh 'cd /var/lib/jenkins/workspace/java-deployment/stockmanager/ && mvn clean install -DskipTests'
                        }
                    }
                }
            }
        }
        
        stage('Docker Image Build of Productcatlogue'){
                    steps{
                        script{
                        sh 'cd /var/lib/jenkins/workspace/java-deployment/productcatalogue/ '
                        sh 'docker image build -t $JOB_NAME:v1.$BUILD_ID   /var/lib/jenkins/workspace/java-deployment/productcatalogue/ '
                        sh 'docker image tag $JOB_NAME:v1.$BUILD_ID debiprasad007/productcatlogue:latest'
                        sh 'docker rmi $JOB_NAME:v1.$BUILD_ID'
                    }
                    }
                }
                
        stage('Docker Image Build of Shopfont'){
                    steps{
                        script{
                        sh 'cd /var/lib/jenkins/workspace/java-deployment/shopfront/ '
                        sh 'docker image build -t $JOB_NAME:v1.$BUILD_ID   /var/lib/jenkins/workspace/java-deployment/shopfront/ '
                        sh 'docker image tag $JOB_NAME:v1.$BUILD_ID debiprasad007/shopfront:latest'
                        sh 'docker rmi $JOB_NAME:v1.$BUILD_ID'
                    }
                    }
                }
                
        stage('Docker Image Build of Stockmanager'){
                    steps{
                        script{
                        sh 'cd /var/lib/jenkins/workspace/java-deployment/stockmanager/ '
                        sh 'docker image build -t $JOB_NAME:v1.$BUILD_ID   /var/lib/jenkins/workspace/java-deployment/stockmanager/ '
                        sh 'docker image tag $JOB_NAME:v1.$BUILD_ID debiprasad007/stockmanager:latest'
                        sh 'docker rmi $JOB_NAME:v1.$BUILD_ID'
                    }
                    }
                }
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
        
    }
}
