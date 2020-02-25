node{
    echo "GitHub BranhName ${env.BRANCH_NAME}"
  echo "Jenkins Job Number ${env.BUILD_NUMBER}"
  echo "Jenkins Node Name ${env.NODE_NAME}"
  
  echo "Jenkins Home ${env.JENKINS_HOME}"
  echo "Jenkins URL ${env.JENKINS_URL}"
  echo "JOB Name ${env.JOB_NAME}"
    def mavenHome=tool name: "maven3.6.1"
    stage('checkout'){
        
        git credentialsId: 'git-user', url: 'https://github.com/kotasivasrinu/maven-web-application.git'
    }
    stage('build'){
        sh  "${mavenHome}/bin/mvn clean package"
    }
    stage('DeploAppIntoTomcat'){
        sshagent(['tomcat-server']) {
    
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.235.128.43:/opt/tomcat/webapps/"
    }
    stage('SendEmailNotification'){
        mail bcc: '', body: '''hi  abcd efghi jkl mnop qrstu vw
xyz''', cc: 'kotadharshan886@gmail.com', from: '', replyTo: '', subject: 'hiii iam from jenkins pipeline', to: 'kotadharshan886@gmail.com'
    }

    }
}
