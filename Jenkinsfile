node('docker-cloud') {
     def cathodeImage
stage 'Build Docker Image'
    checkout scm
    dir('cathode') {
      //docker.image('kmadel/maven:3.3.3-jdk-8').inside('-v /data:/data') {
          cathodeImage = docker.build "kishorebhatia/cathode:1.0"
      //}
    }
stage 'Publish Docker Image'
  sh "docker -v"
  //use withDockerRegistry to make sure we are logged in to docker hub registry
  withDockerRegistry(registry: [credentialsId: 'docker-hub-kb']) { 
    cathodeImage.push()
  }
}
