pipeline {
    agent any
    stages {

        stage('Build') {
            steps {
                echo "Building the war"
            }
        }

        stage("Deploy to QA") {
            steps {
                echo "Deploying to QA"
            }
        }
        

        stage('Pull Docker Image') {
                    steps {
                        bat 'docker pull ashwinibhawar2892/gorestapicicd:1.0'
                    }
        }

        stage('Run API Test Case') {
                    steps {
                        bat 'docker run -v "%cd%\\newman:/app/newman" ashwinibhawar2892/gorestapicicd:1.0'
                    }
        }

        stage('Publish HTML Extra Report') {
                    steps {
                        publishHTML([
                            allowMissing: false,
                            alwaysLinkToLastBuild: false,
                            keepAll: true,
                            reportDir: 'newman',
                            reportFiles: 'gorest.html',
                            reportName: 'GoRestAPIReport',
                            reportTitles: ''
                        ])               
					}
        }

        stage("Deploy to PROD") {
            steps {
                echo "Deploying to PROD"
            }
        }
    }
}
