pipeline
{
  agent any
  stages
  {
    stage ('download the source code from SCM')
    {
      steps
      {
        git branch: 'master', url: 'https://github.com/RahulParkhi/Ant-WebProject.git'
      }
    }
    stage ('Compile the code')
    {
      steps
      {
        withAnt(installation: 'Ant', jdk: 'Java')
        {
          sh 'ant war'
        }
      }
    }
	stage ('Deploy the artifact')
	{
		steps
		{
			sshagent(['TomcatSSH'])
			{
				sh 'scp -o StrictHostKeyChecking=no */war/*.war ec2-user@172.31.89.0:/opt/apache-tomcat-9.0.34/webapps'
			}
		}
	}
  }
}
