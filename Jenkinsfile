@Library('jenkins-shared-library') // if there is no other commands between @Library('jenkins-shared-library') and pipeline {, must be like @Library('jenkins-shared-library')_
def gv

pipeline {
    agent any
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
                    echo "building jar"
                    //gv.buildJar() // it's from script.groovy
                    buildJar() //it's from shared library
                }
            }
        }
        stage("build image") {
            steps {
                script {
                    echo "building image"
                    //gv.buildImage() // it's from script.groovy
                    buildImage() //it's from shared library
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
