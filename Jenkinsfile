node{
	stage('SCM Checkout'){
		git branch: 'wartomcat', url: 'https://github.com/Beenpd1/devopsprojects.git'
	}
	stage('Compile-Package'){
		def mvnHome = tool name: 'maven', type: 'maven'
		sh "${mvnHome}/bin/mvn package"
	}
	stage('Deploy to Tomcat'){
		sshagent(['ec2-user']) {
		sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@34.207.88.179:/opt/tomcat9/webapps/'
	}
	}
}
