pipeline
{
agent any
stages

{ stage ('scm checkout')
 { steps {git branch: 'master', url: 'https://github.com/chits09/maven_project.git'}         //use pipeline syntax generator to generate script
 }


  stage ('code compile' )
  {steps {  withMaven(jdk: 'JAVA_HOME', maven: 'MAVEN_HOME') 
   { sh 'mvn package'}
   }}
 
 
 stage('dev-deployment')
{steps 
  { sshagent (['ec2-user']) 
    {
       sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/jenkins-ci-cd/webapp/target/*.war ec2-user@34.224.27.138:/var/lib/tomcat/webapps/'
  }}}
 


}
}
