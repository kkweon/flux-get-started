podTemplate(label: 'mypod', containers: [
    containerTemplate(name: 'git', image: 'alpine/git', ttyEnabled: true, command: 'cat'),
    containerTemplate(name: 'python', image: 'python:3-alpine', command: 'cat', ttyEnabled: true),
    containerTemplate(name: 'docker', image: 'docker', command: 'cat', ttyEnabled: true)
  ],
  volumes: [
    hostPathVolume(mountPath: '/var/run/docker.sock', hostPath: '/var/run/docker.sock'),
  ]
  ) {
    node('mypod') {
        stage('Check running containers') {
            container('docker') {
                sh 'docker --version'
            }
        }
        stage('Pull source') {
          checkout scm // pull the git repo of the Jenkinsfile
        }
        stage('Check workspace') {
            container('docker') {
                sh 'ls -ahl'
                sh 'ls -ahl ${WORKSPACE}'
            }
        }
    }
}
