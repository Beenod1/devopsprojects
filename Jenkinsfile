node{
	stage('SCM Checkout'){
		git branch: 'wartomcat', url: 'https://github.com/Beenod1/devopsprojects.git'
	}
	stage('Compile-Package'){
		def mvnHome = tool name: 'maven', type: 'maven'
		sh "${mvnHome}/bin/mvn package"
	}
	stage('Deploy to Tomcat'){
		sshagent(['tomcat-dev']) {
		sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@54.152.112.113:/opt/tomcat9/webapps/'
	}
	}
}
