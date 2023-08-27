node {
    // Define the Docker agent
    def dockerImage = 'node:16-buster-slim'
    def dockerArgs = '-p 3000:3000'
    
    // Run the pipeline stages
    stage('Build') {
        // Run the build steps inside the Docker container
        docker.image(dockerImage).inside(dockerArgs) {
            // Execute 'npm install' command
            sh 'npm install'
        }
    }
    stage('Test') {
        // Run the build steps inside the Docker container
        docker.image(dockerImage).inside(dockerArgs) {
            sh './jenkins/scripts/test.sh'
        }
    }
    stage('Manual Approval') {
        // Run the build steps inside the Docker container
        docker.image(dockerImage).inside(dockerArgs) {
            input message: 'Lanjutkan ke tahap Deploy?'
        }
    }
    stage('Deploy') {
        // Run the build steps inside the Docker container
        docker.image(dockerImage).inside(dockerArgs) {
            sh './jenkins/scripts/deliver.sh'
            def proceed = true
            try {
                timeout(time: 1, unit: 'MINUTES')  {
                    node {
                        sh './jenkins/scripts/kill.sh'
                    }
                }
            } catch (err) {
                proceed = false
            }

            if (proceed) {
                currentBuild.result = "SUCCESS"
            }
        }
    }
}