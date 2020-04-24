podTemplate(label: 'mypod', containers: [
    containerTemplate(name: 'python', image: 'python:3-alpine', command: 'cat', ttyEnabled: true),
  ],
  volumes: [
    hostPathVolume(mountPath: '/var/run/docker.sock', hostPath: '/var/run/docker.sock'),
  ]
  ) {
    node('mypod') {
        stage('Check Python version') {
            container('python') {
                sh 'python --version'
            }
        }
        stage('Pull source') {
          checkout scm // pull the git repo of the Jenkinsfile
        }
        stage('Test') {
            container('python') {
                sh 'pip install pytest'
                sh 'pytest my_test.py'
            }
        }
    }
}
