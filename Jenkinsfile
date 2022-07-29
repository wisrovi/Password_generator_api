import groovy.json.JsonSlurperClassic

def jsonParse(def json) {
    new groovy.json.JsonSlurperClassic().parseText(json)
}
pipeline {
  agent { label 'principal' }
   parameters {
        string(name: 'name_project', defaultValue: 'demo', description: 'nombre del proyecto')
        string(name: 'version', defaultValue: '1.0', description: 'version del proyecto')
    }
    environment {
        appName = "${name_project}:${version}"
    }
    stages {
    stage("pre-start"){     
        steps {
            script {			
                sh "echo 'Iniciando despliegue proyecto ${appName})'"
            }
        }
    }
    stage("stop"){     
        steps {
            script {			
                sh "docker-compose down"
            }
        }
    }
    stage("build"){     
        steps {
            script {			
                sh "docker-compose build"
            }
        }
    }
    stage("start"){     
        steps {
            script {			
                sh "docker-compose up -d"
            }
        }
    }
  }
  post {
        always {          
            deleteDir()
            sh "echo 'fase always'"
        }
        success {
            sh "echo 'fase success'"
        }

        failure {
            sh "echo 'fase failure'"
        }      
  }
}  
