node{
echo "The Job name is: ${env.JOB_NAME}"
echo "The Node name is: ${env.NODE_NAME}"
echo  "The build number is: ${env.BUILD_NUMBER}"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])

def mavenHome = tool name: 'maven3.9.8'

stage('CheckOutCode'){
git branch: 'development', credentialsId: 'b1bd42d1-b7db-454d-8146-de47c79bbbc9', url: 'https://github.com/devops-training-git-sept-2024/maven-web-application.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}

/*
stage('ExecuteSonarqubeReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}
stage('UploadArtificatsIntoNexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}
stage('DeployAppIntoomcatServer'){
sshagent(['91e47dd4-c777-4ea4-b001-823808e30c4e']) {
   sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@35.178.249.109:/opt/tomcat9/webapps/"
}
}
*/

}
