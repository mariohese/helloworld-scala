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

            stage('Watching Maven creentials'){

                steps{
                    withMaven(maven:'maven-3.2.5'){
                        sh 'mvn help:effective-settings'
                    }

                }

            }

            stage('Deploy to Nexus'){
                steps{
                    withMaven(maven:'maven-3.2.5'){
                        //sh 'mvn clean deploy -Dmaven.test.skip=true'
                        sh 'mvn deploy -DskipTests -DaltDeploymentRepository=snapshots::default::$NEXUS_URL/repositories/snapshots/'
                    }

                }

            }

        }

}