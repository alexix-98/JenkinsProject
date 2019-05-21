#!groovy

final GIT_URL = 'https://github.com/alexix-98/JenkinsProject'

stage('SCM Checkout') {
  node {
    git url: GIT_URL
  }
}

stage('Compile-Package-with-Maven') {
  // Get maven home path
  node {
    //def mvnHome = tool name: 'Maven', type: 'maven'
    //sh "${mvnHome}/bin/mvn package"    
    def server = Artifactory.server "SERVER_ID"
    def rtMaven = Artifactory.newMavenBuild()
    def buildInfo
    rtMaven.tool = "Maven-3.3.9"
    rtMaven.deployer releaseRepo:'libs-release-local', snapshotRepo:'libs-snapshot-local', server: server
    rtMaven.resolver releaseRepo:'libs-release', snapshotRepo:'libs-snapshot', server: server
    buildInfo = rtMaven.run pom: 'maven-example/pom.xml', goals: 'clean install'
    server.publishBuildInfo buildInfo
  }
}

stage('Dir Creation') {
  node {
    stage "Create build output"
    sh "mkdir -p output_jenkins"
    writeFile file: "output_jenkins/file_1.txt", text: "Esto es una prueba de escritura de fichero."
    writeFile file: "output_jenkins/file_2.md", text: "Esto es un fichero sin importancia."
    stage "Archive build output"
    
    archiveArtifacts artifacts: 'output_jenkins/*.txt', exludes: 'output/*.md'
  }
}
