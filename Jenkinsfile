node {
    agent {
        docker {
            image 'node:16-buster-slim' 
            args '-p 3000:3000' 
        }
    }
    stage('Build') {
        if (env.BRANCH_NAME == 'react-app') {
            sh 'npm install'
        } else {
            echo 'I execute elsewhere'
        }
    }
}