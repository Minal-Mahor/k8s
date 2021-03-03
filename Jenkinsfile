node {
    stage('Get Source'){
        git 'https://github.com/Minal-Mahor/k8s.git'
    }
   
    stage('Docker-push'){
        docker.withRegistry('https://registry.hub.docker.com','dockerHub'){
            def customImage = docker.build('minalmahor/mycluster')
            customImage.push()
        }
    }
    stage('Authenticate'){
        
            bat ''' ibmcloud login --apikey Vbm-YT7nOx5vONApyYx0wdycgVn9_hxRd5a4GHvDqnop  -r  us-south -g Default
            ibmcloud plugin install -f container-service
            ibmcloud plugin install -f container-registry
            ibmcloud plugin install -f observe-service
            ibmcloud plugin list
            ibmcloud ks cluster config --cluster c0rj4r1d0huad5id0ut0
                    
             '''
        
    }
    
    stage('Kubernetes pod'){
        bat "ibmcloud ks cluster config --cluster c0rj4r1d0huad5id0ut0"
        bat "kubectl config current-context"
        bat 'kubectl apply -f servicepy.yaml'
        bat 'kubectl apply -f flask-deployment.yaml'
        bat 'kubectl get pods'
    }
}
