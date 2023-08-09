pipeline{
    agent any
    tools {
        maven 'Maven'
    }
    stages{
        stage("Test"){
            steps{
                echo "mvn test"
            }

        }

        stage("Build"){
            steps{
                echo "Build"
                sh "mvn package"
            }

        }
    
        stage("stage"){
            steps{
                echo "Deploy to stage"
                deploy adapters: [tomcat9(credentialsId: '9a688351-aad6-4278-ae6a-67f385f942b4', path: '', url: 'http://146.148.58.195:8080')], contextPath: '/app', war: '**/*.war'
            }

        }
    
        stage("Production"){
            steps{
                echo "Deploy to production"
            }

        }
    }

    
    
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }   
    }
}
