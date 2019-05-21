node{
  stage('SCM Checkout'){
    git 'https://github.com/alexix-98/JenkinsProject'
  }
  stage('Compile-Package-with-Maven'){
    sh 'mvn package'
  }
}
