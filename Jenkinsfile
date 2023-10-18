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
                sh './vendor/bin/phpunit --log-junit logs/unitreport.xml -c tests/phpunnit.xml tests'
            }
		}
	}
	post{
		always{
			junit testReults: 'logs/unitreport.xml'
		}
	}
}