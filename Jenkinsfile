//CODE_CHANGES=getGitChanges()
pipeline {
    agent any 
    tools{
    }
    environment {
        NEW_VERSION=’1.3.0’
        //SERVER_CREDENTIALS=credentials('')
    }

    stages {
        stage('Clone the repo') {
            steps {
                echo "clone the repo for version ${NEW_VERSION}"
                
                sh 'rm -fr html'
                sh 'git clone https://github.com/dmccuk/html.git'
            }
        }
        stage('push repo to remote host') {
            when { 
                expression {
                    BRANCH_NAME == 'dev' && CODE_CHANGES == true
                }
            }
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
            failure {
                // send email when the job fails
            }
        }
}
