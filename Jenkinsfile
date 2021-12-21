pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                echo 'building global-api'
                sh 'npm install -g npm@latest'
                sh 'node --version'
                sh 'npm --version'
                sh 'npm install'
                
            }
        }

        stage('test') {
            steps {
                echo 'testing global-api'
                sh 'npm run test'
            }
        }

        stage('dockerize') {
            steps {
                echo 'building global-api'
                script {

                    checkout scm

                    docker.withRegistry('https://registry.hub.docker.com', '5efdc081-eaa6-41c3-85b6-52f9497e6fe4') {

                        def customImage = docker.build("snave020/global-api")

                        /* Push the container to the custom Registry */
                        customImage.push()
                    }
                }
            }

            

           
        }

    }
       
    
}
