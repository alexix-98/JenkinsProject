node{
  stage('SCM Checkout'){
    git 'https://github.com/alexix-98/JenkinsProject'
  }
  stage('Compile-Package-with-Maven'){
    // Get maven home path
    // Force Update for commit (alex)
    def mvnHome = tool name: 'Maven', type: 'maven'
    sh "${mvnHome}/bin/mvn package"    
  } 
}
