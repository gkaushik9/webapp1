pipeline {
    agent any 
    stages {
        stage('Clone the repo') {
            steps {
                echo 'clone the repo'
                sh 'rm -fr html'
                sh 'git clone https://github.com/dmccuk/html.git'
            }
        }
        stage('push repo to remote host') {
            steps {
                echo 'connect to remote host and pull down the latest version'
                //sh 'ssh -i ~/working.pem ec2-user@35.176.182.32 sudo git -C /var/www/html pull'
                sh ' git -C /Users/gkaushik/Projects/webapp1 pull https://github.com/gkaushik9/webapp1.git'
            }
        }
        stage('Check website is up') {
            steps {
                echo 'Check website is up'
                //sh 'curl -Is 35.176.182.32 | head -n 1'
                sh 'curl -Is localhost:9090|head -n 1'
            }
        }
        post {
            always {
                // send email to all to inform that job has been run via jenkins
            }
            success {
                // send email only when the job is successful
            }
    }
}
