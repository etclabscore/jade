# Jenkins

# Why Jenkins?
You might wonder why jenkins is the winner here and not something like circleci or travis. We believe that the developer and devops and everyone should be able to run the pipeline on their own machine.

### Pipeline As Code with Jenkins
With the intro of the [Pipline plugin](https://wiki.jenkins-ci.org/display/JENKINS/Pipeline+Plugin) you can implement a projects entire build/test/deploy pipeline in a `Jenkinsfile` in your repository. This treats your pipeline as just another piece of code. Check it in.

## Getting Started

You can boot your own jenkins via `docker-compose -f docker-compose.jenkins.yml up`.

open [http://localhost:8080/blue](http://localhost:8080/blue), and log in with `admin/admin`.

Once logged in, follow the wizard to add your repo to the pipeline. It should auto set up and run your Pipieline as code as defined in your repositorys `Jenkinsfile`.

Example pipeline:

```
pipeline {
  agent any
  stages {
    stage('commitlint') {
      steps {
        sh 'npm install -g commitlint'
        sh 'nodenv rehash'
        sh 'commitlint --config=commitlint.config.json .'
      }
    }
  }
}
```

## Docker
Docker is installed on the machine by default. you can use it in a pipeline like this:

```
pipeline {
  agent any
  stages {
    stage('hello world') {
      steps {
        sh 'docker run hello-world'
      }
    }
  }
}
```

## What is installed on the Jenkins box:
`docker`, `nodenv` and `node 8.12.0` are installed by default

## Adding A Dependency
Adding a global jenkins dependency, like `nodenv` should be done in [bin/jenkins/Dockerfile](bin/jenknis/Dockerfile). Plugins are added to Jenkins via the `install-plugins.sh` line in [bin/jenkins/Dockerfile](bin/jenkins/Dockerfile)


