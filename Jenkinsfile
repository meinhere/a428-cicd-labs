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
}