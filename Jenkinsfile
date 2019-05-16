pipeline {
    agent any
	stages {
        stage('master') {
			when {
			    branch 'master'
			}       
			stages {
			    stage('Build') {
			        steps {
			            sh 'mvn clean install'
			        }
			    }
                stage('Deploying') {
                    steps {
                        sh 'Deploying'
                    }
                }
			}
		}
        stage('Development') {
            when {
                branch 'Development'
            }
            stages {
                stage('Build') {
                    steps {
                        sh 'mvn clean install -DskipTests'
                    }
				}
				stage('Test') {
				 	steps {
						 sh 'mvn test'
					}
				}
				stage('Deploying') {
					steps {
						sh 'Development Branch Deployment'
					}
				}
                
            }
        }
        stage('Release') {
            stages {
                stage('Build') {
                    steps {
                        sh 'mvn clean package -DskipTests'
                    }
                }
                stage('Deploying') {
                    steps {
                        sh 'Deploying'
                        sh 'cp target/*.war /home/yashu/'
                    }
                }
            }
        }
	}
}
