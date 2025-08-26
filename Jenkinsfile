@Library('jenkins-shared-library') // if there is no other commands between @Library('jenkins-shared-library') and pipeline {, must be like @Library('jenkins-shared-library')_
def gv

pipeline {
    agent any

    tools {
        maven 'maven-3.9'
    }

    stages {
        stage("init") {
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }
        stage("build jar") {
            steps {
                script {
                    buildJar() //it's from shared library
                }
            }
        }
        stage("build image") {
            steps {
                script {
                    buildImage 'tracyhsu57/demo-app:jma-2.2' //it's from shared library
                }
            }
        }
        stage("deploy") {
            steps {
                script {
                    echo "deploying"
                    //gv.deployApp()
                }
            }
        }
    }   
}
