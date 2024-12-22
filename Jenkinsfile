pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout your Node.js application source code
                git 'https://github.com/DevOpsnaman/Klinik.git'
            }
        }

        stage('Deploy to EC2') {
            steps {
                script {

                    // SSH into your EC2 machine and run your Docker image
                    sshagent(['NodeCredentials']) {
                        sh """
                            
                            sudo ssh -o StrictHostKeyChecking=no DevOps@40.82.144.108/ << 
                            EOF
                            sudo scp -r * DevOps@40.82.144.108/var/www/html
                            sudo systemctl restart nginx
                            sudo systectl status nginx

                            EOF
                        """
                    }
                }
            }
        }
    }
}
