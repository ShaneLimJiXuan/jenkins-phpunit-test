pipeline {
	agent {
		docker {
			image 'composer:latest'
		}
	}
	stages {
		stage('Build') {
			steps {
				sh 'composer install'
			}
		}
		stage('Test') {
			steps {
                sh './vendor/bin/phpunit tests --log-junit logs/unitreport.xml -c test/phpunnit.xml test'
            }
		}
	}
	Post{
		always{
			junit testReults: 'logs/unitreport.xml'
		}
	}
}