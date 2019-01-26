pipeline {
    agent any
    
        environment {
             NEXUS_URL = 'http://localhost:8081'
    }
        stages {

            stage('Prueba echo') {
                steps {

                    sh 'echo "Hola Mundo"'

                } 
            }

            stage('Prueba maven'){
                steps{

                    withMaven(maven:'maven-3.2.5'){
                    
                        sh 'mvn --version'
                    }
                }
            }

            stage('compile'){

                steps{
                    withMaven(maven:'maven-3.2.5'){
                        sh 'mvn clean compile -U'
                    }
                }

            }

            stage('Test'){

                steps{
                    withMaven(maven:'maven-3.2.5'){
                        sh 'mvn test'
                    }

                }

            }

            stage('Deploy to Nexus'){
                steps{
                    withMaven(maven:'maven-3.2.5'){
                        sh 'mvn clean deploy -Dmaven.test.skip=true'
                    }

                }

            }

        }

}