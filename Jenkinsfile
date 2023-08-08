// INSTALL THE BELOW PLUGINS
// Pipeline plugin
// Docker plugin for a docker container
// Docker pipeline plugin for pipeline stages of the container
pipeline {
    agent {
        label {
            label 'master'
            customWorkspace "${JENKINS_HOME}/${BUILD_NUMBER}/"
        }
    }
    environment {
        Go111MODULE='on'
    }
    stages {
        stage('Clone ') {
            steps {
                git 'https://github.com/kodekloudhub/go-webapp-sample.git'
            }
        }
        // stage('test'){
        //     steps {
        //         sh 'go test ./...'
        //     }
        // }
         stage('Build Docker image'){
            steps {
                script{
                    image = docker.build("adminturneddevops/go-webapp-sample")
                    sh "docker run -p 8090:8000 -d adminturneddevops/go-webapp-sample" // Deploy with above container image to prod
                }
            }
        }
    }
    
}
