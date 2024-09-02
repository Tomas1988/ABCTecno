pipeline {
    agent any
    stages {
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
            post{
                success{
                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy to tomcat server') {
            steps {
                echo "Deployment steps will be added here"
                // Placeholder para futuros pasos
            }
        }
    }
}
