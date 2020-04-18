pipeline {
	agent any

	stages {

		stage ('Compile Stage') {

			steps {
				withMaven(maven: 'maven_3_6_3') {
					sh 'mvn clean compile'
				}
			}
		}

		stage ('SonarQube Analysis'){

			steps {
				withSonarQubeEnv(credentialsId: '07a91e39387d3e1b9a273d72578831c92cfc8826', installationName: 'My SonarQube Server') {
      				sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:2.11:sonar'
				}
			}
		}

		stage ('Deployment Stage'){

            steps {
				withMaven(maven: 'maven_3_6_3') {
					sh 'mvn deploy'
                }
        	}
		}

	}

}
