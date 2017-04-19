node("launchpad-maven") {
  checkout scm
  def sso_url
  stage("Deploy SSO") {
    sh "cd sso; mvn fabric8:deploy"
    sso_url = "java -jar target/sso-client.jar --displaySSOURL".execute().text
    sso_url = ( sso_url =~ /Using auth server URL: (.+)/)
    sso_url = sso_url[0][1]
  }
  stage("Build") {
    sh "cd app; mvn -DSSO_AUTH_SERVER_URL=${sso_url} fabric8:deploy -Popenshift -DskipTests"
  }
  stage("Deploy")
}

