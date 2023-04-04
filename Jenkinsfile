node {
         stage("Git Clone"){

         git credentialsId: 'Git-Hub-Credentials', url: "https://github.com/Vaibhav-Ahuja1/bentoml.git"
         
         stage("Docker build"){
             sh 'docker version'
             sh 'pip install -r requirements.txt'
             sh 'python3 train.py'
             sh 'bentoml build .'
             sh 'bentoml containerize xgb_classifier:latest -t vaibhavahuja1/xgb_classifier:latest'
         
         }
         stage("Docker Login"){
                   
             withCredentials([string(credentialsId: 'Dockerhub-pwd', variable: 'Dockerhub-pwd')]) {
        	    sh "docker login -u vaibhavahuja1 -p ${Dockerhub-pwd}"
         }
         }
         stage("Push image to docker hub"){
             sh 'docker push vaibhavahuja1/xgb_classifier:latest'
         }

         stage("Kubernetes deployment"){
             sh 'kubectl apply -f deploymentservice.yaml'
           }

        }
    }
