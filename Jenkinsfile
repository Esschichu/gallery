pipeline{
    agent any
    tools{
        nodejs "node"
    }

    stages{
        stage('clone git repo'){
            steps {
                git  branch: 'master', credentialsId: 'Hello@12345567', url: "https://github.com/Esschichu/gallery.git"
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
    post {
        success {
            emailext attachLog: true, 
                body:
                    """
                    <p>EXECUTED: Job <b>\'${env.JOB_NAME}:${env.BUILD_NUMBER})\'</b></p>
                    <p>
                    View console output at 
                    "<a href="${env.BUILD_URL}">${env.JOB_NAME}:${env.BUILD_NUMBER}</a>"
                    </p> 
                    <p><i>(Build log is attached.)</i></p>
                    """,
                subject: "Status: 'SUCCESS' -Job \'${env.JOB_NAME}:${env.BUILD_NUMBER}\'", 
                to: 'achiengesther96@gmail.com'
        }
        failure {
            emailext attachLog: true, 
                body:
                    """
                    <p>EXECUTED: Job <b>\'${env.JOB_NAME}:${env.BUILD_NUMBER})\'</b></p>
                    <p>
                    View console output at 
                    "<a href="${env.BUILD_URL}">${env.JOB_NAME}:${env.BUILD_NUMBER}</a>"
                    </p> 
                    <p><i>(Build log is attached.)</i></p>
                    """,
                subject: "Status: FAILURE -Job \'${env.JOB_NAME}:${env.BUILD_NUMBER}\'", 
                to: 'achiengesther96@gmail.com'
        }
}
        
    }

}