pipeline
{
  agent any
  environment
  {
    buildnumber = "1.1.1"
  }
  stages
  {
    Stage("Prepare")
    {
      Steps
      {
        echo "Im preparing!"
      }
    }
    Stage("Build")
    {
      Environment
      {
        LogLevel = "Info"
      }
      Steps
      {
        echo "I am building build ${buildnumber} with log level ${LogLevel}"
      }
    }
    Stage("Test")
    {
      Steps
      {
        echo "Testing build ${buildnumber}"
        writeFile file: "result.txt", text: "passed"
      }
    }
  }
  Post
  {
    success
    {
      archiveArtifacts 'result.txt'
    }
  }
}
