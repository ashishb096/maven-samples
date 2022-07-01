node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def mvn = tool 'Default Maven';
    withSonarQubeEnv() {
      bat 'mvn clean verify sonar:sonar -Dsonar.projectKey=sonar'
    }
  }
}
