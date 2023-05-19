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
          //  steps {
          //  }
        }
        stage('Tests-on-dev') {
          //  steps {
          //  }
        }
        stage('Deploy-to-staging') {
           // steps {
          //  }
        }
        stage('Tests-on-staging') {
           // steps {
           // }
        }
        stage('Deploy-to-preprod') {
           // steps {

           // }
        }
        stage('Tests-on-preprod') {
           // steps {
            
           // }
        }
        stage('Deploy-to-prod') {
           // steps {
            
           // }
        }
        stage('Tests-on-prod') {
            //steps {
            
           // }
        }
    }
}



def build(){
    echo "“Installing all required depdendencies.."
    git branch: 'main', url: 'https://github.com/AdrianaaM01/PrakD_Jenkins.git'
    bat "cd"
    bat "pip install -r requirements.txt"

}

def deploy(String environment, int port){
    echo "Deployment to ${environment} has started.."
    git branch: 'main', url: 'https://github.com/AdrianaaM01/sample-book-app.git'
    bat "npm install"
    bat "pm2 delete \"books-${environment}\""
    bat "pm2 start -n \"books-${environment}\" index.js -- ${port}"
}

def test(String test_set, String environment){
    echo "Testing ${test_set} test set on ${environment} has started.."
    git branch: 'main', poll: false, url: 'https://github.com//AdrianaaM011/course-js-api-framework.git'
    bat "cd"
    bat "npm install"
    bat "npm run ${test_set} ${test_set}_${environment}"
}


// Būvējuma izveidi;
// Būvējuma izvietošanu “DEV” vidē;
// Testu izpildi “DEV” vidē;
// Būvējuma izvietošanu “STG” vidē;
// Testu izpildi “STG” vidē;
// Būvējuma izvietošanu “PRD” vidē;
// Testu izpildi “PRD” vidē;
