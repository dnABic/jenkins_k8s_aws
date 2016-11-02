node {
  def project = 'jenkins_k8s_aws'
  def appName = 'instance-info'
  def imageTag = "bla/${project}/${appName}:${env.BRANCH_NAME}.${env.BUILD_NUMBER}"

  checkout scm

  stage 'Build image'

  sh("echo 'test'")
  sh("sleep 4")
}

podTemplate(label: 'mypod', containers: [
    containerTemplate(name: 'golang', image: 'golang:1.6.3-alpine', ttyEnabled: true, command: 'cat')
  ])
{
    node ('mypod') {
        stage 'Get a Golang project'
        container('golang') {
            stage 'Build a Go project'
            sh """
            mkdir -p /go/src/github.com/hashicorp
            """
        }
    }
}
