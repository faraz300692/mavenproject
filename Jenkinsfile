pipeline {
    agent any
    tools { 
        maven 'Maven1' 
        jdk 'jdk' 
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
                sh 'sudo cp -r /var/lib/jenkins/workspace/maven1/multi-module/webapp/target/*.war /usr/local/apache-tomcat-9.0.24/webapps/'       
                }
        
    }
}
}
