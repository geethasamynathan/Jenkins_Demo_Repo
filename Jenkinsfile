pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps { checkout scm }
    }

    stage('Build') {
      steps {
        bat '''
          if exist out rmdir /s /q out
          mkdir out
          dir /s /b src\\*.java > sources.txt
          javac -d out @sources.txt
        '''
      }
    }

    stage('Run') {
      steps {
        bat '''
          java -cp out HelloJenkins
        '''
      }
    }
  }
}
