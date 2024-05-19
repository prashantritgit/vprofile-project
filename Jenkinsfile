pipeline {
    
	agent any

    tools {
        jdk 'jdk11'
        maven 'maven3'
    }
	
    environment {
        SNAP_REPO = 'vprofile-snapshot'
        NEXUS_USER = 'admin'
        NEXUS_PASS = 'jeet'
        RELEASE_REPO = 'vprofile-release'
        CENTRAL_REPO = 'vpro-maven-central'
        NEXUSIP = '13.233.196.7'
        NEXUSPORT = '8081'
	    NEXUS_GRP_REPO = 'vpro-maven-group'
        NEXUS_login = "nexus-cred"
        
    }
    
    
    stages {    
        stage('Build'){
            steps {
                sh 'mvn -s settings.xml -DskipTests install'
            }
            post {
                success {
                    echo "Now Archiving."
                    archiveArtifacts artifacts: '**/*.war'
                }
            }
        }
        stage('Tests') {
            steps {
                sh "mvn test"
            }
        }

        stage('Checkstyle Analysis') {
            steps {
                sh "mvn checkstyle:checkstyle"
            }
        } 
    }    
}        
        
   
		
