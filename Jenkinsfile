node
{
  def mavenHome = tool name: "maven3.6.3"
stage('CodeCheckout')
{
git branch: 'development', credentialsId: '586f68f7-14ac-4139-b5e9-70c7c3e7ba4f', url: 'https://github.com/venkatavellampali/maven-web-application.git'
}
  stage('Build')
  {
    sh "${mavenHome}/bin/mvn clean package"
  }
  stage('SonarQubeReport')
        {
          sh "${mavenHome}/bin/mvn sonar:sonar"
        }
  stage('UploadArtifact')
  {
    sh "${mavenHome}/bin/mvn deploy"
  }
  stage('DeplyAppintoTomcat')
  {
   sshagent(['9bf5a77a-a31e-46a8-bc3b-8e27c341656e']) 
    {
      sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@13.235.69.78:/opt/apache-tomcat-9.0.29/webapps/"
    } 
  }
}
