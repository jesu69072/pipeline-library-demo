# pipeline-library-demo
pipeline-library-demo
Demonstrates how to use a Shared Library in Jenkins pipelines. This repository defines a single function, sayHello, which will echo a greeting.

Setup instructions
In Jenkins, go to Manage Jenkins → Configure System. Under Global Pipeline Libraries, add a library with the following settings:

Name: pipeline-library-demo
Default version: Specify a Git reference (branch or commit SHA), e.g. master
Retrieval method: Modern SCM
Select the Git type
Project repository: https://github.com/monodot/pipeline-library-demo.git
Credentials: (leave blank)
Then create a Jenkins job with the following pipeline (note that the underscore _ is not a typo):

@Library('pipeline-library-demo')_

stage('Demo') {

  echo 'Hello World'

  sayHello 'Dave'

}
This will output the following from the build:

[Pipeline] stage
[Pipeline] { (Demo)
[Pipeline] echo
Hello world
[Pipeline] echo
Hello, Dave.
[Pipeline] }
[Pipeline] // stage
[Pipeline] End of Pipeline
Finished: SUCCESS
