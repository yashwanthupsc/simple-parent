pipeline{
        agent any
		stages
			{
                         stage('Checkout')
                              {
                               steps{checkout scm}
                              }
                         stage('Build')
                              {
                               steps{sh 'mvn clean install sonar:sonar'}
                              }
                        }
        }
