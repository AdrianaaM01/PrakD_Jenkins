pipeline {
    agent any
    

    stages {
        stage('Install-pip-deps') {
            steps {
                script{
                    build()
                }  
            }
        }
        stage('Deploy-to-dev') {
            steps {
                script{
                    deploy("DEV", 7001)
                }
            }
        }
        stage('Tests-on-dev') {
            steps {
                script{
                    test("GREET", "DEV")
                }
            }
        }
        stage('Deploy-to-staging') {
            steps {
                script{
                    deploy("STG", 7002)
                }
            }
        }
        stage('Tests-on-staging') {
            steps {
                script{
                    test("GREET", "STG")
                }
            }
        }
        stage('Deploy-to-preprod') {
            steps {
                script{
                    deploy("PPRD", 7003)
                }

            }
        }
        stage('Tests-on-preprod') {
            steps {
                script{
                    test("GREET", "PPRD")
                }
            }
        }
        stage('Deploy-to-prod') {
            steps {
                script{
                    deploy("PRD", 7004)
                }
            
            }
        }
        stage('Tests-on-prod') {
            steps {
                script{
                    test("GREET", "PRD")
                }
            
            }
        }
    }
}



def build(){
    echo "“Installing all required depdendencies.."
    git branch: 'main', url: 'https://github.com/AdrianaaM01/python-greetings.git'
    bat "cd"
    bat "Pip install virtualenv"
    bat "Pip freeze > requirements.txt "
    bat "pip install -r requirements.txt"

}

def deploy(String environment, int port){
    echo "Deployment to the ${environment} is starting.."
    git branch: 'main', url: 'https://github.com/AdrianaaM01/python-greetings.git'
    bat "pm2 delete greetings-app-${environment} & set errorlevel=0"
    bat "pm2 start app.py --name greetings-app-${environment} -- --port ${port}"
}

def test(String test_set, String environment){
    echo "Testing ${test_set} test set on ${environment} is starting.."
    git branch: 'main', poll: false, url: 'https://github.com/AdrianaaM01/python-greetings.git'
    bat "cd"
    bat "npm install"
    bat "npm run greetings greetings_${environment}"
}



