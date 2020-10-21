pipeline {
    agent any
        
    stages {
        stage('Build') {
            steps {
                echo 'Hello from Build, This is common stage for all branches.'
            }
        }
        stage('Test') {
            steps {
                echo 'Hello from Test,  This is common stage for all branches.'
            }
        }
		stage('Not feature') {
			when { 
				not { 
					//branch 'feature' 
					expression {
						BRANCH_NAME ==~ /feature\/[0-9]+\.[0-9]+\.[0-9]+\.[A-Z]+\.[a-z]+/
					}
				}
			}
            steps {
                echo 'This is common stage for all branches except feature branch.'
            }
        }
        stage('Deliver for Release') {
            when {
                branch 'release'
            }
            steps {
                echo 'Hello from Release,  This is only for release branch.'
            }
        }
        stage('Deploy for Master') {
            when {
                branch 'master'
            }
            steps {
                echo 'Hello from master,  This is only for master branch.'
            }
        }
    }
}
