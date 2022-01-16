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
    stage ('Check-Git-Secrets') {
      steps {
        sh 'rm trufflehog || True'
        sh 'docker run gesellix/trufflehog --json https://github.com/Fatheem96/CICDEx.git > trufflehog'
        sh 'cat trufflehog'
      }
    }
    
    stage ('Build') {
      steps {
        sh 'mvn clean package' 
      }
     }
    }
   }
        
