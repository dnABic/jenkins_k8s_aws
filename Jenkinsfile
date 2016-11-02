node {
  def project = 'jenkins_k8s_aws'
  def appName = 'instance-info'
  def imageTag = "bla/${project}/${appName}:${env.BRANCH_NAME}.${env.BUILD_NUMBER}"

  checkout scm

  stage 'Build image' {
    sh("docker build -t ${imageTag} .")
  }
}
