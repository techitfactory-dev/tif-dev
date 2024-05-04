pipeline {
    agent any
    
    environment {
            
        DOCKERHUB_CREDENTIALS = credentials('docker-creds') // "docker-creds" is the ID of the Jenkins Credential holding your Docker Credentials
        DOCKER_ACCOUNT = '$DOCKERHUB_CREDENTIALS_USR'
        DOCKER_REPOSITORY = 'test-repo1'
        TEMPLATE_PATH = sh(script: 'locate html.tpl', returnStdout: true).trim()
        SCANNER_HOME = tool 'sonar-scanner'
        SONAR_ORGANIZATION = 'techitfactoryb01'
    }
    
    stages {
        
        stage('Git Checkout') {
            steps {
                git branch: 'feature', credentialsId: 'git-creds', url: 'https://github.com/TechITFactoryb01/online-boutique-microservices-code.git'
            }
        }
        
        stage('AdService Sonar Analysis') {
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh "$SCANNER_HOME/bin/sonar-scanner -Dsonar.organization=$SONAR_ORGANIZATION -Dsonar.projectKey=adservice-microservice -Dsonar.sources=./src/adservice -Dsonar.projectName=AdService -Dsonar.java.binaries=. -Dsonar.projectVersion=1.0"
                }
                sleep time: 5, unit: 'SECONDS'
                waitForQualityGate abortPipeline: true
            }
        }
        
        stage('CartService Sonar Analysis') {
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh "$SCANNER_HOME/bin/sonar-scanner -Dsonar.organization=$SONAR_ORGANIZATION -Dsonar.projectKey=cartservice-microservice -Dsonar.sources=./src/cartservice/src -Dsonar.projectName=CartService -Dsonar.projectVersion=1.0"
                }
                sleep time: 5, unit: 'SECONDS'
                waitForQualityGate abortPipeline: true
            }
        }
        
        stage('CheckoutService Sonar Analysis') {
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh "$SCANNER_HOME/bin/sonar-scanner -Dsonar.organization=$SONAR_ORGANIZATION -Dsonar.projectKey=checkoutservice-microservice -Dsonar.sources=./src/checkoutservice -Dsonar.projectName=CheckoutService -Dsonar.projectVersion=1.0"
                }
                sleep time: 5, unit: 'SECONDS'
                waitForQualityGate abortPipeline: true
            }
        }
        
        stage('CurrencyService Sonar Analysis') {
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh "$SCANNER_HOME/bin/sonar-scanner -Dsonar.organization=$SONAR_ORGANIZATION -Dsonar.projectKey=currencyservice-microservice -Dsonar.sources=./src/currencyservice -Dsonar.projectName=CurrencyService -Dsonar.projectVersion=1.0"
                }
                sleep time: 5, unit: 'SECONDS'
                waitForQualityGate abortPipeline: true
            }
        }
        
        stage('EmailService Sonar Analysis') {
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh "$SCANNER_HOME/bin/sonar-scanner -Dsonar.organization=$SONAR_ORGANIZATION -Dsonar.projectKey=emailservice-microservice -Dsonar.sources=./src/emailservice -Dsonar.projectName=EmailService -Dsonar.projectVersion=1.0"
                }
                sleep time: 5, unit: 'SECONDS'
                waitForQualityGate abortPipeline: true
            }
        }
        
        stage('Frontend Sonar Analysis') {
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh "$SCANNER_HOME/bin/sonar-scanner -Dsonar.organization=$SONAR_ORGANIZATION -Dsonar.projectKey=frontend-microservice -Dsonar.sources=./src/frontend -Dsonar.projectName=Frontend -Dsonar.projectVersion=1.0"
                }
                sleep time: 5, unit: 'SECONDS'
                waitForQualityGate abortPipeline: true
            }
        }
        
        stage('Loadgenerator Sonar Analysis') {
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh "$SCANNER_HOME/bin/sonar-scanner -Dsonar.organization=$SONAR_ORGANIZATION -Dsonar.projectKey=loadgenerator-microservice -Dsonar.sources=./src/loadgenerator -Dsonar.projectName=Loadgenerator -Dsonar.projectVersion=1.0"
                }
                sleep time: 5, unit: 'SECONDS'
                waitForQualityGate abortPipeline: true
            }
        }
        
        stage('PaymentService Sonar Analysis') {
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh "$SCANNER_HOME/bin/sonar-scanner -Dsonar.organization=$SONAR_ORGANIZATION -Dsonar.projectKey=paymentservice-microservice -Dsonar.sources=./src/paymentservice -Dsonar.projectName=PaymentService -Dsonar.projectVersion=1.0"
                }
                sleep time: 5, unit: 'SECONDS'
                waitForQualityGate abortPipeline: true
            }
        }
        
        stage('ProductCatalogService Sonar Analysis') {
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh "$SCANNER_HOME/bin/sonar-scanner -Dsonar.organization=$SONAR_ORGANIZATION -Dsonar.projectKey=productcatalogservice-microservice -Dsonar.sources=./src/productcatalogservice -Dsonar.projectName=ProductCatalogService -Dsonar.projectVersion=1.0"
                }
                sleep time: 5, unit: 'SECONDS'
                waitForQualityGate abortPipeline: true
            }
        }
        
        stage('RecommendationService Sonar Analysis') {
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh "$SCANNER_HOME/bin/sonar-scanner -Dsonar.organization=$SONAR_ORGANIZATION -Dsonar.projectKey=recommendationservice-microservice -Dsonar.sources=./src/recommendationservice -Dsonar.projectName=RecommendationService -Dsonar.projectVersion=1.0"
                }
                sleep time: 5, unit: 'SECONDS'
                waitForQualityGate abortPipeline: true
            }
        }
        
        stage('ShippingService Sonar Analysis') {
            steps {
                withSonarQubeEnv('sonar-server') {
                    sh "$SCANNER_HOME/bin/sonar-scanner -Dsonar.organization=$SONAR_ORGANIZATION -Dsonar.projectKey=shippingservice-microservice -Dsonar.sources=./src/shippingservice -Dsonar.projectName=ShippingService -Dsonar.projectVersion=1.0"
                }
                sleep time: 5, unit: 'SECONDS'
                waitForQualityGate abortPipeline: true
            }
        }

        stage('Docker Login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        
        stage('Adservice Docker Build-Tag-Scan-Push') {
            steps {
                script {
                    dir('src/adservice') {
                        
                        sh "docker build -t ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:adservice-${BUILD_NUMBER}.0 ."
                    }   
                       
                       sh 'echo $TEMPLATE_PATH'
                       // Scanning docker image using trivy and saving the output to "adservice-report.html" file  
                       sh """
                       trivy image --format template --template "@${TEMPLATE_PATH}" -o adservice-report.html --timeout 15m ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:adservice-${BUILD_NUMBER}.0
                       """
                        
                       sh "docker push ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:adservice-${BUILD_NUMBER}.0"
                }
            
                publishHTML(target: [
                    allowMissing: true,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: ".",
                    reportFiles: "adservice-report.html", // Make sure this file name matches with the one in the trivy command above
                    reportName: "Trivy Adservice Report", // This will be the name of the report in Jenkins UI, can be changed to any name
                ])
            }
        }
        
        stage('Cartservice Docker Build-Tag-Scan-Push') {
            steps {
                script {
                    dir('src/cartservice/src') {
                        
                        sh "docker build -t ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:cartservice-${BUILD_NUMBER}.0 ."
                    }                     
                       
                       
                      sh """
                      trivy image --format template --template "@${TEMPLATE_PATH}" -o cartservice-report.html ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:cartservice-${BUILD_NUMBER}.0 --timeout 15m
                      """
                        
                      sh "docker push ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:cartservice-${BUILD_NUMBER}.0"
                }
            
                publishHTML(target: [
                    allowMissing: true,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: ".",
                    reportFiles: "cartservice-report.html",
                    reportName: "Trivy Cartservice Report",
                ])
            }
        }

        stage('Checkoutservice Docker Build-Tag-Scan-Push') {
            steps {
                script {
                    dir('src/checkoutservice') {
                        
                        sh "docker build -t ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:checkoutservice-${BUILD_NUMBER}.0 ."
                    }    
                        
                                              
                      sh """
                      trivy image --format template --template "@${TEMPLATE_PATH}" -o checkoutservice-report.html ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:checkoutservice-${BUILD_NUMBER}.0 --timeout 15m
                      """
                        
                      sh "docker push ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:checkoutservice-${BUILD_NUMBER}.0"
                }
            
                publishHTML(target: [
                    allowMissing: true,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: ".",
                    reportFiles: "checkoutservice-report.html",
                    reportName: "Trivy Checkoutservice Report",
                ])
            }
        }

        stage('Currencyservice Docker Build-Tag-Scan-Push') {
            steps {
                script {
                    dir('src/currencyservice') {
                        
                        sh "docker build -t ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:currencyservice-${BUILD_NUMBER}.0 ."
                    }    
                        
                                              
                      sh """
                      trivy image --format template --template "@${TEMPLATE_PATH}" -o currencyservice-report.html ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:currencyservice-${BUILD_NUMBER}.0 --timeout 15m
                      """
                        
                      sh "docker push ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:currencyservice-${BUILD_NUMBER}.0"
                }
            
                publishHTML(target: [
                    allowMissing: true,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: ".",
                    reportFiles: "currencyservice-report.html",
                    reportName: "Trivy Currencyservice Report",
                ])
            }
        }

        stage('Emailservice Docker Build-Tag-Scan-Push') {
            steps {
                script {
                    dir('src/emailservice') {
                        
                        sh "docker build -t ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:emailservice-${BUILD_NUMBER}.0 ."
                    }    
                        
                                             
                      sh """
                      trivy image --format template --template "@${TEMPLATE_PATH}" -o emailservice-report.html ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:emailservice-${BUILD_NUMBER}.0 --timeout 15m
                      """
                        
                      sh "docker push ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:emailservice-${BUILD_NUMBER}.0"
                }
            
                publishHTML(target: [
                    allowMissing: true,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: ".",
                    reportFiles: "emailservice-report.html",
                    reportName: "Trivy Emailservice Report",
                ])
            }
        }

        stage('Frontend Docker Build-Tag-Scan-Push') {
            steps {
                script {
                    dir('src/frontend') {
                        
                        sh "docker build -t ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:frontend-${BUILD_NUMBER}.0 ."
                    }    
                        
                                              
                      sh """
                      trivy image --format template --template "@${TEMPLATE_PATH}" -o frontend-report.html ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:frontend-${BUILD_NUMBER}.0 --timeout 15m
                      """
                        
                      sh "docker push ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:frontend-${BUILD_NUMBER}.0"
                }
            
                publishHTML(target: [
                    allowMissing: true,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: ".",
                    reportFiles: "frontend-report.html",
                    reportName: "Trivy Frontend Report",
                ])
            }
        }

        stage('Loadgenerator Docker Build-Tag-Scan-Push') {
            steps {
                script {
                    dir('src/loadgenerator') {
                        
                        sh "docker build -t ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:loadgenerator-${BUILD_NUMBER}.0 ."
                    }    
                        
                                              
                      sh """
                      trivy image --format template --template "@${TEMPLATE_PATH}" -o loadgenerator-report.html ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:loadgenerator-${BUILD_NUMBER}.0 --timeout 15m
                      """
                        
                      sh "docker push ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:loadgenerator-${BUILD_NUMBER}.0"
                }
            
                publishHTML(target: [
                    allowMissing: true,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: ".",
                    reportFiles: "loadgenerator-report.html",
                    reportName: "Trivy Loadgenerator Report",
                ])
            }
        }

        stage('Paymentservice Docker Build-Tag-Scan-Push') {
            steps {
                script {
                    dir('src/paymentservice') {
                        
                        sh "docker build -t ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:paymentservice-${BUILD_NUMBER}.0 ."
                    }    
                        
                                             
                      sh """
                      trivy image --format template --template "@${TEMPLATE_PATH}" -o paymentservice-report.html ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:paymentservice-${BUILD_NUMBER}.0 --timeout 15m
                      """
                        
                      sh "docker push ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:paymentservice-${BUILD_NUMBER}.0"
                }
            
                publishHTML(target: [
                    allowMissing: true,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: ".",
                    reportFiles: "paymentservice-report.html",
                    reportName: "Trivy Paymentservice Report",
                ])
            }
        }

        stage('Productcatalogservice Docker Build-Tag-Scan-Push') {
            steps {
                script {
                    dir('src/productcatalogservice') {
                        
                        sh "docker build -t ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:productcatalogservice-${BUILD_NUMBER}.0 ."
                    }    
                        
                                             
                      sh """
                      trivy image --format template --template "@${TEMPLATE_PATH}" -o productcatalogservice-report.html ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:productcatalogservice-${BUILD_NUMBER}.0 --timeout 15m
                      """
                        
                      sh "docker push ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:productcatalogservice-${BUILD_NUMBER}.0"
                }
            
                publishHTML(target: [
                    allowMissing: true,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: ".",
                    reportFiles: "productcatalogservice-report.html",
                    reportName: "Trivy Productcatalogservice Report",
                ])
            }
        }

        stage('Recommendationservice Docker Build-Tag-Scan-Push') {
            steps {
                script {
                    dir('src/recommendationservice') {
                        
                        sh "docker build -t ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:recommendationservice-${BUILD_NUMBER}.0 ."
                    }    
                        
                                             
                      sh """
                      trivy image --format template --template "@${TEMPLATE_PATH}" -o recommendationservice-report.html ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:recommendationservice-${BUILD_NUMBER}.0 --timeout 15m
                      """
                        
                      sh "docker push ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:recommendationservice-${BUILD_NUMBER}.0"
                }
            
                publishHTML(target: [
                    allowMissing: true,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: ".",
                    reportFiles: "recommendationservice-report.html",
                    reportName: "Trivy Recommendationservice Report",
                ])
            }
        }

        stage('Shippingservice Docker Build-Tag-Scan-Push') {
            steps {
                script {
                    dir('src/shippingservice') {
                        
                        sh "docker build -t ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:shippingservice-${BUILD_NUMBER}.0 ."
                    }    
                        
                                             
                      sh """
                      trivy image --format template --template "@${TEMPLATE_PATH}" -o shippingservice-report.html ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:shippingservice-${BUILD_NUMBER}.0 --timeout 15m
                      """
                        
                      sh "docker push ${env.DOCKER_ACCOUNT}/${DOCKER_REPOSITORY}:shippingservice-${BUILD_NUMBER}.0"
                }
            
                publishHTML(target: [
                    allowMissing: true,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: ".",
                    reportFiles: "shippingservice-report.html",
                    reportName: "Trivy Shippingservice Report",
                ])
            }
        }
        
        // stage('Docker Images Cleanup') {
        //     steps {
        //         sh 'docker rmi -f $(docker images -q)'
        //     }
        // }
        
        stage('Docker Logout') {
            steps {
                sh 'docker logout'
            }
        }
    }
}
