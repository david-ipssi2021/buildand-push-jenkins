def pipelineContext = [:]
node {

   def registryProjet='davidbarbosaleal:5000/'
   def IMAGE="${registryProjet}apache:version-${env.BUILD_ID}"

    stage('Clone') {
          checkout scm
    }

    def img = stage('Build') {
          docker.build("$IMAGE",  '.')
    }

    stage('Run') {
          img.withRun("--name run-$BUILD_ID -p 8000:80") { c ->
       
          }
    }

    stage('Push') {
          docker.withRegistry('htttps://registry.hub.docker.com', 'registry_id') {
              img.push 'latest'
              img.push()
          }
    }

}

