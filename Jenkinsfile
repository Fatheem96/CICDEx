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
    stage ('Source Composition Analysis')
    steps {
      sh 'wget "https://raw.githubusercontent.com/Fatheem96/CICDEx/master/owasp-dependency-check.sh" '
      sh 'chmod +X owasp-dependency-check.sh'
      sh 'bash owasp-dependency-check.sh'
    }
  }
    stage ('Build') {
      steps {
        sh 'mvn clean package' 
      }
     }
    }
   }
        
