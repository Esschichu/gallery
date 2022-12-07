pipeline{
    agent any
    tools{
        nodejs "node"
    }

    stages{
        stage('clone git repo'){
            steps {
                git 'https://github.com/Esschichu/gallery'
            }
        }
    stage('Build Project'){
        steps {
            sh 'npm install'
        }
    }

    stage("Test"){
        steps{
            sh "npm test"
        }
    }
        
    }

}