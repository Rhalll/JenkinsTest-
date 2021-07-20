pipeline
{
  agent any
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
  }
  post
  {
    success
    {
      archiveArtifacts 'result.txt'
    }
  }
}
