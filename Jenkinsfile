pipeline{
    agent any
    options{
        buildDiscarder(logRotator(daysToKeepStr: '2'))
        retry(1)
    }
    parameters{
        string(name: 'REPO', defaultValue: 'Bhavesh')
    }
    stages{
        stage('Git Checkout') {
            steps {
                checkout scm
            }
        }
        stage("Build the docker image and push to repository"){
            steps{
                sh "docker build -t myapp:latest ."
            }   
        }
        stage("deploy the app into the app host"){
            steps{
                sh "echo \"i'm done\""
            }
        }
    }
    post{
        always{
            sh "echo \"from always\""
            deleteDir()
        }
        failure{
            echo "from failure"
        }
    }
}
