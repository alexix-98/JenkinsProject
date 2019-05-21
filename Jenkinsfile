#!groovy

final GIT_URL = 'https://github.com/alexix-98/JenkinsProject'

stage('SCM Checkout') {
  node {
    git GIT_URL
  }
}

stage('Compile-Package-with-Maven') {
  // Get maven home path
  def mvnHome = tool name: 'Maven', type: 'maven'
  sh "${mvnHome}/bin/mvn package"    
}
