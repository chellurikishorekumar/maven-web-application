node{
    
def mavenHome = tool name: 'maven3.9.6'

properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])

echo "Build Number is: ${env.BUILD_NUMBER}"
echo "Job Name is: ${env.JOB_NAME}"
echo "Node Name is: ${env.NODE_NAME}"
echo "Jenkins Home dir is: ${env.JENKINS_HOME}"
echo "Build url is: ${env.BUILD_URL}"
echo "Jenkins url is: ${env.JENKINS_URL}"

stage ('CheckOutCode'){
git branch: 'development', credentialsId: '594fecf6-6315-4d98-ba09-edde637c3a1f', url: 'https://github.com/chellurikishorekumar/maven-web-application.git'
}
stage ('Build'){
sh "${mavenHome}/bin/mvn clean package"
}
 /* 
stage ('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn clean sonar:sonar"
}
stage ('UploadArtifactsIntoNexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}
stage ('DeployAppIntoTomcat'){
sshagent(['f32329b0-091e-45d6-8e32-d98d6610aa15']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.19.61:/opt/apache-tomcat-9.0.86/webapps/"
}
}
*/
}
