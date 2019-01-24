pipeline {
    agent any

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

            stage('install'){

            	steps{
            		withMaven(maven:'maven-3.2.5'){
            			sh 'mvn install'
            		}
            	}

            }

        }

}