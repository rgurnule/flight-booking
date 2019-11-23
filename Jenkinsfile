pipeline {
	agent any
	tools {
		jdk 'localJDK'
		maven 'localMaven'
	}
	stages {
		stage("Maven-Build"){
			steps {
				sh 'mvn -Dmaven.test.skip=true install'
			}
		}
		stage ("Docker-Login") {
			steps {
				sh 'docker login -u satyendrasingh -p Password@123'
			}
		}
		stage ("Docker-Build-Services") {
			steps {
				sh "docker build -t search:0.${env.BUILD_ID} search/"
				sh "docker build -t book:0.${env.BUILD_ID} book/"
				sh "docker build -t checkin:0.${env.BUILD_ID} checkin/"
				sh "docker build -t fares:0.${env.BUILD_ID} fares/"
				sh "docker build -t website:0.${env.BUILD_ID} website/"
			}
		}
	}
}
