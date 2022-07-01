node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def mvn = tool 'maven';
    withSonarQubeEnv() {
      bat 'mvn clean compile verify' sonar:sonar -Dsonar.projectKey=sonar"
    }
  }
}
