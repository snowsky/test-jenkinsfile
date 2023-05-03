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
        stage('Install') {
            steps {
                script {
                    tags_extra = "${params.BRANCH}"
                }
                echo "tags_extra: ${tags_extra}"
                scp install.sh username@hostname:/tmp/install.sh
                ssh username@hostname /tmp/install.sh
                #dir("${env.WORKSPACE}") {
                #    sh "${env.WORKSPACE}/install.sh"
                #}
            }
        }
        stage('Build') {
            steps {
                echo "tags_extra: ${tags_extra}"
            }
        }
        stage('Deploy') {
            steps {
                echo "tags_extra: ${tags_extra}"
            }
        }
    }
}
