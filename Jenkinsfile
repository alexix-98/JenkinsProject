#!groovy

final GIT_URL = 'https://github.com/alexix-98/JenkinsProject'

stage('SCM Checkout') {
  node {
    git GIT_URL
  }
}

stage('Compile-Package-with-Maven') {
  // Get maven home path
  node {
    def mvnHome = tool name: 'Maven', type: 'maven'
    sh "${mvnHome}/bin/mvn package"    
  }
}

stage('Dir Creation') {
  node {
    stage "Create build output"
    sh "mkdir -p output_jenkins"
    writeFile file: "output_jenkins/file_1.txt", text: "Esto es una prueba de escritura de fichero."
    writeFile file: "output/file_2.md", text: "Esto es un fichero sin importancia."
    stage "Archive build output"
    
    archiveArtifacts artifacts: 'output/*.txt', exludes: 'output/*.md'
  }
}
