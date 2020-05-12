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
                sshagent(['tomcat']) {
                sh 'scp -o StrictHostKeyChecking=no target/*.war ubuntu@13.232.202.25:/prod/apache-tomcat-8.5.39/webapps/webapp.war'
                }
            }      
        }
    }
}
