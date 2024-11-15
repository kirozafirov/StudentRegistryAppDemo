pipeline{
    agent any
    
    stages{
        stage('Checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/kirozafirov/StudentRegistryAppDemo'
            }
        }

        stage("Install dependencies"){
            step{
                script{
                    bat "npm install"
                }
            }
        }

        stage("Start application and run tests"){
            steps{
                script{
                    bat 'npm start &'
                    bat 'wait-on http://localhost:8090'
                    bat 'npm test'
                }
            }
        }
    }

    post{
        always{
            echo "CI pipeline completed"
        }
    }


}