pipeline {
    agent any

    stages {
        stage ('Build Image') {
            steps {
                script {
                    // dockerapp = docker.build("fabricioveronez/api-produto:${env.BUILD_ID}", '-f ./src/Dockerfile ./src') 
                    dockerapp = docker.build("bzanf/api-produto", "-v $(which docker):/usr/bin/docker -f ./src/Dockerfile ./src")
                }                
            }
        }

        // stage ('Push Image') {
        //     steps {
        //         script {
        //             docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
        //                 dockerapp.push('latest')
        //                 dockerapp.push("${env.BUILD_ID}")
        //             }
        //         }
        //     }
        // }

        // stage ('Deploy Kubernetes') {
        //     environment {
        //         tag_version = "${env.BUILD_ID}"
        //     }
        //     steps {
        //         withKubeConfig([credentialsId: 'kubeconfig']) {
        //             sh 'sed -i "s/{{tag}}/$tag_version/g" ./k8s/deployment.yaml'
        //             sh 'kubectl apply -f ./k8s/deployment.yaml'
        //         }
        //     }
        // }
    }
}