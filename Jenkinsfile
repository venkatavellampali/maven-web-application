node
{
  def mavenHome = tool name: "maven3.6.3"
stage('CodeCheckout')
{
git branch: 'development', credentialsId: '586f68f7-14ac-4139-b5e9-70c7c3e7ba4f', url: 'https://github.com/venkatavellampali/maven-web-application.git'
}
  stage('Build')
  {
    sh "${mavenName}/bin/mvn clean package
  }
  
}
