- build v
- test  v
- code analysis v
- deploy v >> PWS
- regression ???


Agenda:
- create a file called pipeline.yml
- define a build plan (pipeline) http://concourse.ci/build-plans.html
  - create a job to build the app
  - define a job plan
  - set the pipeline and show the box -- there are no actions yet
  - A job plan consists of a set of inputs and outputs, and sequence of tasks that can be executed on the inputs/outputs.
    - In concourse terminology: input and output are resources
    - A resource in something that is external to my pipeline but it's necessary to run
      - for example: a git repo, an s3 bucket or the "time"
      - to see the set of predefined resource types, check http://concourse.ci/resource-types.html
  - First, we need to clone the sprint petclinic from github
    - for that, we'll need to define a git resource that knows where to find the git repo
    - once we have the resource defined, we can make our job to "get" this resource
  - set pipeline: fly -t zumba set-pipeline -p spring-petclinic-ci -c ci/pipeline.yml
  - run the build job -- watch it go green
  - add trigger true to the "get" of the source code
  - create a new job called test and connect it after the build job
