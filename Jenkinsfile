
node{
    
properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '5', daysToKeepStr: '', numToKeepStr: '5')), [$class: 'JobLocalConfiguration', changeReasonComment: ''], pipelineTriggers([pollSCM('* * * * *')])])
   
def mavenHome = tool name: "maven3.9.0"

stage('CheckoutCode'){
git branch: 'development', credentialsId: '41bd3833-d2d1-4449-9b2d-70209179e50b', url: 'https://github.com/RajashekharKategoud/maven-web-application.git'
}

stage('Build'){
sh "${mavenHome}/bin/mvn clean package"
}
/*
stage('ExecuteSonarQubeReport'){
sh "${mavenHome}/bin/mvn clean package sonar:sonar"
}

stage('UploadArtifactIntoNexus'){
sh "${mavenHome}/bin/mvn clean deploy"
}

stage('DeployApplicationIntoTomcatServer'){
sshagent(['073074b2-a5b0-422c-9965-04f56e5a55da']) {
    sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@172.31.46.153:/opt/apache-tomcat-9.0.82/webapps/" 
}
}
*/
}
