node
{

def mavenHome = tool name: "Maven3.8.1"

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])

stage('CheckoutCode')
{
git branch: 'development', credentialsId: '0e496b41-a9f4-482d-bf86-bf15dc964849', url: 'https://github.com/varaprasad9010-cloud/maven-web-application.git'
}

stage('Build')
{
sh "${mavenHome}/bin/mvn clean package"
} 

/*
stage('ExecuteSonarQubeReport')
{
sh "${mavenHome}/bin/mvn sonar:sonar"
} 

stage('UploadArtificatesintoNexus')
{
sh "${mavenHome}/bin/mvn deploy"
} 

stage('DeployAppintoTomcatServer')
{
sshagent(['4c8d04eb-5f98-4b4a-9c7f-28b0ae673a7b']) {
 sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.233.117.13://opt/apache-tomcat-9.0.45/webapps/"
}
} 
*/

stage('SendEmailNotification')
{
emailext body: '''Build Over


Regards,
Prasad''', subject: 'Build over', to: 'varaadams07@gmail.com'
}


}
