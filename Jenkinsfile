pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Task: Build the code using Maven.'
                echo 'Tool: Maven'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Task: Run unit tests and integration tests.'
                echo 'Tools: JUnit for unit tests, TestNG for integration tests'
            }
            post {
                always {
                    script {
                        def status = currentBuild.currentResult
                        emailext(
                            subject: "Jenkins Pipeline - Unit and Integration Tests Status: ${status}",
                            body: """\
Testing Pipeline after 1st Commit. The Unit and Integration Tests stage has finished with status: ${status}.

Build URL: ${env.BUILD_URL}
""",
                            to: 'muhammad.mv06@gmail.com',
                            attachmentsPattern: '**/test-*.log',
                            replyTo: 'muhammad.mv06@gmail.com'
                        )
                    }
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Task: Analyze the code to ensure it meets industry standards.'
                echo 'Tool: SonarQube'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Task: Perform a security scan on the code to identify vulnerabilities.'
                echo 'Tool: OWASP Dependency-Check'
            }
            post {
                always {
                    script {
                        def status = currentBuild.currentResult
                        emailext(
                            subject: "Jenkins Pipeline - Security Scan Status: ${status}",
                            body: """\
Testing Pipeline after 1st Commit. The Security Scan stage has finished with status: ${status}.

Build URL: ${env.BUILD_URL}
""",
                            to: 'muhammad.mv06@gmail.com',
                            attachmentsPattern: '**/dependency-check-*.xml',
                            replyTo: 'muhammad.mv06@gmail.com'
                        )
                    }
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Task: Deploy the application to a staging server.'
                echo 'Example Deployment: AWS EC2 instance'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Task: Run integration tests on the staging environment.'
                echo 'Tools: Selenium or other integration test tools'
            }
            post {
                always {
                    script {
                        def status = currentBuild.currentResult
                        emailext(
                            subject: "Jenkins Pipeline - Integration Tests on Staging Status: ${status}",
                            body: """\
Testing Pipeline after 1st Commit. The Integration Tests on Staging stage has finished with status: ${status}.

Build URL: ${env.BUILD_URL}
""",
                            to: 'muhammad.mv06@gmail.com',
                            attachmentsPattern: '**/test-*.log',
                            replyTo: 'muhammad.mv06@gmail.com'
                        )
                    }
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Task: Deploy the application to a production server.'
                echo 'Example Deployment: AWS EC2 instance'
            }
        }
    }
}