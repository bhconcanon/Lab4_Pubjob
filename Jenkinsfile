pipeline {
    agent {
        kubernetes {
            yaml '''
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: build
    image: 'maven:3.8.3-jdk-11'
    command:
    - cat
    tty: true
    '''
        defaultContainer 'build'
        }
    }

    stages {
        stage('Sending notification') {
            steps {
                echo 'Sending data for branch to consuming job'
                publishEvent event: jsonEvent('{"lab":"5", "branch":[{"develop", "test", "release", "main"}], "test":[{"enabled", "disabled"}], "deploy":{["enabled", "disabled"]}}')
            }
        }
    }
}