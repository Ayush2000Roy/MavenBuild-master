node('') {
	stage ('checkout code'){
		checkout scm
	}
	
	stage ('Build'){
		bat "mvn clean install -Dmaven.test.skip=true"
	}

	stage ('Test Cases Execution'){
		bat "mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent install -Pcoverage-per-test"
	}

	stage ('Sonar Analysis'){
		//bat "mvn sonar:sonar -Dsonar.host.url=http://35.153.67.119:9000 -Dsonar.login=77467cfd2653653ad3b35463fbfdb09285f08be5"
	}

	stage ('Archive Artifacts'){
		//archiveArtifacts artifacts: 'target/*.war'
	}
	
	stage ('Deployment'){
		//deploy adapters: [tomcat9(credentialsId: 'TomcatCreds', path: '', url: 'http://3.84.47.228:8080/')], contextPath: 'counterwebapp', war: 'target/*.war'
	}
	
	stage ('Notification'){
		emailext (
		      subject: "Job Completed",
		      body: "Jenkins Pipeline Job for Maven Build got completed !!!",
		      to: "narutoichaichalover69@gmail.com",
		      attachLog: true
		    )
	}
}
