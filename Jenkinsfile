node {
    stage('Build') { 
        try {
            sh 'npm install'
        }
        catch (exc) {
            echo 'npm error!!'
            throw
        }
    }
    stage('Test') {
        try {
            sh './jenkins/scripts/test.sh'
        }
        catch (exc) {
            echo 'test error!!'
            throw
        }
    }
}