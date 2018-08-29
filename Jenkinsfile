pipeline {
    agent {
        docker {
            image 'hello-world'
            args '-p 3000:3000 -p 5000:5000'
        }
    }
    environment {
        CI = 'true'
    }
    stages {
        stage('Run integration') {
            when {
                branch 'integration'
            }
            steps {
                docker build -t integration .
            }
        }
        stage('Run master') {
            when {
                branch 'master'
            }
            steps {
                docker build -t master .
                echo "build through master branch code"
            }
        }
    }
}