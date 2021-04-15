#!/usr/bin/env groovy

library identifier: 'js-jenkins-shared-library@main', retriever: modernSCM(
        [$class: 'GitSCMSource',
         remote: 'https://github.com/farru1998/js-shared-library-main.git',
         credentialsId: 'git-credentials'
        ]
)

 def gv;

pipeline {
    agent any
    stages {
       stage('init') {
            steps {
                script {
                    gv = load 'script.groovy'
                }
            }
        }
        stage('check branch') {
            steps {
                script {
                    branch()
                }
            }
        }
	stage('build and push image') {
            steps {
                script {
			buildImage 'mfarhan1998/simpleapp:${BUILD_NUMBER}'
                    // dockerLogin()
                    // dockerPush 'armughanahmed/shared-lib-app:sla-3.0'
                }
            }
        } 
    }
}
