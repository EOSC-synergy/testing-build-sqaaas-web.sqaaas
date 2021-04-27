@Library(['github.com/indigo-dc/jenkins-pipeline-library@release/2.1.0']) _

def projectConfig

pipeline {
    agent any

    stages {
        stage('SQA baseline criterion: qc_doc') {
            steps {
                script {
                    projectConfig = pipelineConfig(
                        configFile: '.sqa/config.yml',
                        scmConfigs: [ localBranch: true ]
                    )
                    buildStages(projectConfig)
                }
            }
            post {
                cleanup {
                    cleanWs()
                }
            }
        }
        stage('non-JePL stage') {
            steps {
                sh 'hostname'
                sh 'docker-compose ps'
            }
            post {
                cleanup {
                    cleanWs()
                }
            }
        }
    }
}
