//pipeline {agent any stages{stage ('Inicial'){steps {echo 'Estoy en la fase inicial'}}stage ('Etapa 2') {steps {echo 'Hola'}}}}
pipeline {
  agent any 
  tools {
    maven 'maven-curso'
  }
  stages{
    stage ('Build'){
      steps {
        bat 'mvn clean package'
      }
    post { 
      success { 
        echo 'Guardando....' 
        archiveArtifacts artifacts: '**/target/*.war'
      }
    }
  }
    stage ('Paso a pre') {
      steps {
        build job: 'realizar-deploy'
      }
    }
}
}

//pipeline {  agent any   tools {    maven 'maven-curso'  }  stages{    stage ('Build'){      steps {        bat 'mvn clean package'      }    post {       success {         echo 'Guardando....'         archiveArtifacts artifacts: '**/target/*.war'      }    }  }}}
