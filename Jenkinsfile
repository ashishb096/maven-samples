node {
  stage('SCM') {
    checkout scm
  }
 notify('started')
    try
    {
        stage('checkout') 
            {
                git 'https://github.com/ashishb096/maven-samples.git'
            }
        stage('compiling,testing,verify') 
            {
                bat 'mvn clean compile verify package'
               
            }
        stage('archiving') 
            {
                
               step([$class: 'JUnitResultArchiver', allowEmptyResults: true, checksName: '', testResults: 'single-module/target/surefire-reports/TEST*.xml'])
                archiveArtifacts artifacts: 'single-module\\target\\*.jar', followSymlinks: false
            }
            notify('Success')
    }
    catch (err) 
    {
        echo "Caught: ${err}"
        currentBuild.result = 'FAILURE'
    }
}
    def notify(status)
    {
        emailext body: 'hi how are you douing', subject: 'test', to: 'bishtashish0965@gmail.com'
    }

  
}
