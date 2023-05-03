#!/usr/bin/env groovy
pipeline {
    agent any
    
    environment {
        GIT_TAG_COMMIT = sh(script: 'git describe --tags --always', returnStdout: true).trim()
    }
    
    parameters {
        string(name: 'BRANCH', defaultValue: 'main', description: 'Git Branch Name for Jenkins Builds')    
    }
    
    stages {
        stage('stage one') {
            steps {
                script {
                    tags_extra = "${params.BRANCH}"
                }
                echo "tags_extra: ${tags_extra}"
            }
        }
        stage('stage two') {
            steps {
                echo "tags_extra: ${tags_extra}"
            }
        }
        stage('stage three') {
            when {
                expression { tags_extra != 'bla' }
            }
            steps {
                echo "tags_extra: ${tags_extra}"
            }
        }
    }
}
