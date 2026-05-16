pipeline{
    agent any
    stages{
        stage("checkout"){
            steps{
                echo "========executing checkout========"
                checkout scm
            }
        }  

        stage('Install Dependencies'){
            steps{
                script{
                    bat 'python -m pip install -r requirements.txt'
                }
            }
        }          
        stage("build docker image"){
            steps{
                script{
                  echo "========executing settingup environment========"
                  bat 'docker build -t flask-jenkins-sqlite-image:latest .'
                }
            }
        }
        
        stage("Deploy Docker Container"){
            steps{
                script{
                  bat 'docker run -d -p 9091:5000 --name flask-sqlite-container flask-jenkins-sqlite-image:latest'
                }
            }
        }
    }
}     
    
        