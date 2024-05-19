pipeline {
    
	agent any

    tools {
        jdk 'jdk17'
        maven 'maven3'
    }
	
    environment {
        NEXUS_VERSION = "nexus3"
        NEXUS_PROTOCOL = "http"
        NEXUS_URL = "http://13.233.196.7:8081"
        NEXUS_REPOSITORY = "vprofile-release"
	    NEXUS_REPOGRP_ID = "vprofile-grp-repo"
        NEXUS_CREDENTIAL_ID = "nexus-cred"
        ARTVERSION = "${env.BUILD_ID}"
    }
    
    
    stages {    
        stage('Build'){
            steps {
                sh 'mvn -s settings.xml -DskipTests install'
            }
        }
    }    
}        
        
   
		
