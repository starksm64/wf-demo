node("launchpad-maven") {
  checkout scm
  stage("Deploy SSO") {
    sh "cd sso; mvn fabric8:deploy"
  }
  stage("Build") {
    sh "cd app; mvn fabric8:deploy -Popenshift -DskipTests"
  }
  stage("Deploy")
}

