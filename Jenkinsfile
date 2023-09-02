node(){

	// def sonarHome = tool name: 'SonarScanner', type: 'hudson.plugins.sonar.SonarRunnerInstallation'
	
	// stage('Code Checkout'){
	// 	checkout changelog: false, poll: false, scm: scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'GitHubCreds', url: 'https://github.com/anujdevopslearn/MavenBuild']])
	// }
	stage('checkout code'){
		checkout scm
	}
	stage('Build Automation'){
		sh """
			ls -lart
			mvn clean install
			ls -lart target

		"""
	}
	// stage('Build'){
		// sh "mvn clean install -Dmaven.test.skip=true"
	// }
	// stage('Code Scan'){
	// 	withSonarQubeEnv(credentialsId: 'SonarQubeCreds') {
	// 		sh "${sonarHome}/bin/sonar-scanner"
	// 	}
		
	// }
	
	// stage('Code Deployment'){
	// 	deploy adapters: [tomcat9(credentialsId: 'TomcatCreds', path: '', url: 'http://54.197.62.94:8080/')], contextPath: 'Planview', onFailure: false, war: 'target/*.war'
	// }
	stage('Code Deployment'){
		deploy adapters: [tomcat9(credentialsId: 'TomcatCreds', path: '', url: 'http://localhost:9090/')], contextPath: 'counterwebapp', war: 'target/*.war'
	}
}
