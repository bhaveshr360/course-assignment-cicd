pipeline{
    agent {
        label 'app'
    }
    options{
        buildDiscarder(logRotator(daysToKeepStr: '2'))
        retry(2)
    }
    parameters{
        string(name: 'BRANCH', defaultValue: 'main')
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
