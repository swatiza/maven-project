pipeline
{
agent any
    stages
    {
        stage('scm checkout'){
            steps{
                git branch: 'master', url: 'https://github.com/swatiza/maven-project/'
        }
        stage('execute umit test framework'){
            steps{
                withMaven(globalMavenSettingsConfig: '33a86476-a5a1-457b-b286-5c6a1b66cd7e', jdk: 'localjdk', maven: 'localmaven', mavenSettingsConfig: '88f23039-03a5-484a-81d3-043fdbf0bc3e', traceability: true) {
   sh 'mvn test'
}
            }
         }
stage('build the code'){
            steps{
                withMaven(globalMavenSettingsConfig: '33a86476-a5a1-457b-b286-5c6a1b66cd7e', jdk: 'localjdk', maven: 'localmaven', mavenSettingsConfig: '88f23039-03a5-484a-81d3-043fdbf0bc3e', traceability: true) {
   sh 'mvn package'
}
            }
        }
stage('docker image creation')
{
steps{ sh 'docker build -t swatizambre/tomcat2023:latest .'}
}
stage('docker push to docker registry')
{steps{withDockerRegistry(credentialsId: 'dockerhubaccount', url: ' https://index.docker.io/v1/') {
    sh 'docker push swatizambre/tomcat2023:latest'
}}
}
}
}
