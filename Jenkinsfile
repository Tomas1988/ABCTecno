pipeline {
    agent any
    tools {
        maven 'mymaven'  // Asegúrate de que 'mymaven' esté correctamente configurado en Jenkins
    }
    stages {
        stage('Build') {  // Nuevo stage para la compilación del código
            steps {
                sh 'mvn clean install'  // Ejecuta el comando de Maven para compilar el proyecto
            }
        }
        stage('Compile') {
            steps {
                build job: 'ABC_Compile_Code'
            }
        }
        stage('Test') {
            steps {
                build job: 'ABC_Test_Code'
            }
        }
        stage('Package') {
            steps {
                build job: 'ABC_PACK_Code'
            } 
            post {
                success {
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy to tomcat server') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'dfe13bbf-bc15-485c-89bb-f952292e7a2b', path: '', url: 'http://3.128.76.83:8080/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
