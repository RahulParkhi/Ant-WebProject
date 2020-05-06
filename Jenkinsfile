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
          sh 'ant init'
        }
      }
    }
  }
}
