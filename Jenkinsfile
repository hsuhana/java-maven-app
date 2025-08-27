// @Library('jenkins-shared-library-start@master') // if there is no other commands between @Library('jenkins-shared-library') and pipeline {, must be like @Library('jenkins-shared-library')_

// for project scope libraries
library identifier: 'jenkins-shared-library-start@master', retriever: modernSCM([
    $class: 'GitSCMSource',
    remote: 'https://github.com/hsuhana/jenkins-shared-library-start.git',
    credentialsId: 'Github-repo'
])
// @Library('enkins-shared-library@master') -> this is optional

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
        stage("build and push image") {
            steps {
                script {
                    buildImage 'tracyhsu57/demo-app:jma-2.3' //it's from shared library
                    dockerLogin()
                    dockerPush 'tracyhsu57/demo-app:jma-2.3'
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
