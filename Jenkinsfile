node{
	stage('SCM Checkout'){
		git branch: 'smtpjenkins', url: 'https://github.com/Beenod1/devopsprojects.git'
	}
	stage('Compile-Package'){
		def mvnHome = tool name: 'maven', type: 'maven'
		sh "${mvnHome}/bin/mvn package"
	}
	stage('Deploy to Tomcat'){
		sshagent(['tomcat-dev']) {
		sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@18.212.57.157:/opt/tomcat9/webapps/'
		}
	}
	stage('Slack Notification'){
	slackSend baseUrl: 'https://hooks.slack.com/services/', channel: '#jenkinslab', color: '#439FE0', message: 'New Build deployed', teamDomain: 'intelycore8', tokenCredentialId: 'slack-secret'
	}
	stage('Email Notification'){
	mail bcc: '', body: 'This is body', cc: '', from: 'binod.maharjan.nepal@gmail.com', replyTo: 'binod.maharjan.nepal@gmail.com', subject: 'This is Subject', to: 'binod.maharjan.nepal@gmail.com'
	}

}

