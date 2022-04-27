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
  { sshagent (credentials: ['deploy-to-tomcat']) 
    {
       sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@172.31.11.116:/var/lib/tomcat/webapps/'
  }}}
 


}
}
