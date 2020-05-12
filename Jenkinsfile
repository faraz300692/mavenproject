pipeline {
    agent any
    tools { 
        maven 'maven' 
        jdk 'java' 
    }
    stages {
        stage ('Initialize') {
            steps {
                sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
                ''' 
            }
        }


        stage('SCM Checkout'){
            steps {
                git 'https://github.com/faraz300692/mavenproject.git'
            }
        }
        
        stage ('Compile Stage') {
            steps {
                sh 'mvn clean compile'
                echo 'Build Compile Successful'
                }
            }
        
        
        stage ('Build') {
            steps {
                sh 'mvn install'
                echo 'This is a minimal pipeline.'
            }
        }
        
        
        stage ('Deploy to Tomcat'){
            steps {
           sshagent(['tomcat']) {
                sh 'scp -o StrictHostKeyChecking=no **/*.war ubuntu@18.141.186.191:/usr/local/bin/apache-tomcat-9.0.34/webapps/webapp.war'
               }
            }      
        }
    }
}
