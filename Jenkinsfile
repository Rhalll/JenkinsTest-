library identifier: 'JenkinsTest-@main',
        retriever: modernSCM([$class: 'gitSCMSource',remote: 'https://github.com/Rhalll/JenkinsTest-.git'])
pipeline
{
  agent any
  parameters{booleanParam(name: "RC",defaultValue: false,description: "Is this RC?")}
  environment
  {
    buildnumber = "1.1.1"
  }
  stages
  {
    stage("Prepare")
    {
      steps
      {
        echo "Im preparing!"
      }
    }
    stage("Build")
    {
      environment
      {
        LogLevel = "Info"
      }
      steps
      {
        echo "I am building build ${buildnumber} with log level ${LogLevel}"
      }
    }
    stage("Test")
    {
      steps
      {
        echo "Testing build ${buildnumber}"
        writeFile file: "result.txt", text: "passed"
      }
    }
    stage("Publish")
    {
      when{
        expression{return params.RC}
      }
      steps
      {
        publishStuff()
      }
    }
  }
  post
  {
    success
    {
      archiveArtifacts 'result.txt'
    }
  }
}
