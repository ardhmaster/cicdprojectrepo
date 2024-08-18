pipeline{
    agent{
        node{
            label 'Jenkins_slave_node'
        }
    }
    stages{
        stage('checkout code stage'){
            steps{
                git url: 'https://github.com/ardhmaster/cicdprojectrepo.git', branch: 'main'
            }
        }
        stage('Build docker image'){
            steps{
                sh 'docker build -t myimage .'
            }
        }
        stage('push docker image to dockerhub'){
            steps{
                sh 'docker tag myimage sekhar919/myimage'
                sh 'docker push sekhar919/myimage'
            }
        }
        stage('deploy to kubernetes'){
            steps{
                sh 'kubctl apply -f my-deployment.yml'
            }
        }
    }
}