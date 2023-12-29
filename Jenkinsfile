pipeline {
    agent {
        label 'staging'
    }
    environment{
        ssh_key = credentials('ssh_key')
    }
    stages {

    
        stage('ssh connection'){
            steps{
                script{
                def sshCommand = """ssh -i ${ssh_key} ubuntu@ec2-3-110-170-110.ap-south-1.compute.amazonaws.com"""
                sh '$sshCommand'   
                }
            }
        }
        
        stage('checkout') {
             steps {
               git branch: 'staging', credentialsId: 'c95654d9-bda3-4cdc-a75d-6951e4211bfd', url: 'https://github.com/yadasManisha/jenkins.git'
                }
        }
        // stage('deploy') {
        //     steps {
        //         sh '''                    
        //             cd /home/jenkins/workspace/flaskapp
        //             pip3 install flask
        //             nohup python3 app.py
        //             ''' }
        // }
        
    }
    
}
