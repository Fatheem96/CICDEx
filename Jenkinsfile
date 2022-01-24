pipeline {
  agent any 
  tools {
    maven 'Maven'
  }
  stages {
    stage ('Initialize') {
      steps {
        sh '''
                    echo "PATH = ${PATH}"
                    echo "M2_HOME = ${M2_HOME}"
            ''' 
      }
    }
    stage ('Source Composition Analysis') {
    steps {
      sh 'wget "https://raw.githubusercontent.com/Fatheem96/CICDEx/master/owasp-dependency-check.sh" '
      sh 'chmod +X owasp-dependency-check.sh'
      sh 'bash owasp-dependency-check.sh'
      sh 'cat /var/lib/jenkins/OWASP-Dependency-Check/reports/dependency-check-report.xml'
    }
  }
    stage ('SAST') {
      steps {
        withSonarQubeEnv('sonar') {
          sh 'mvn sonar:sonar -Dsonar.login=b3d9a0a468839346f275efaf7dbea239fc43f5d8'
          sh 'cat target/sonar/report-task.txt'
        }
      }
    }
    stage ('Build') {
      steps {
        sh 'mvn clean package' 
      }
     }
  }
}
    
        
