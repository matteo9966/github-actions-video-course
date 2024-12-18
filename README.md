# github-actions-video-course
This is a repository I am using to follow a tutorial on github


## Workflow environment variables

To set up a workflow-level environment variable, we must define it at the top level of the YAML file. Let’s add the following underneath the NAME variable at the top of the file:

`
env:
  NAME: 'Snyk Demo'
`
This code defines an environment variable called NAME that we can now access anywhere within our workflow. To access this variable, we must use a specific syntax similar to that used when accessing UNIX environment variables. To use our NAME variable, we must prefix it with a dollar sign, changing the variable to $NAME.

`
- name: Print name
  run: echo "Hello $NAME"
`

## Job environment variables
Now, let’s look at setting up job and step environment variables. These can be set up the same way as our workflow environment variables, but we define them within the relevant section.

For our job variable, we want to define the Java version as follows:

`
jobs:
  build:
    env:
        JAVA_VERSION: '21'
`

`
steps:
- uses: actions/checkout@v3
- name: Set up JDK ${{env.JAVA_VERSION}}
  uses: actions/setup-java@v3
  with:
    java-version: ${{env.JAVA_VERSION}}
    distribution: 'temurin'
    cache: maven
`