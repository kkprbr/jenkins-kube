      node {
	  
          stage('Clone Github repository') {
		     git branch: 'main', credentialsId: 'git-creds', url: 'https://github.com/kkprbr/jenkins-kube.git'
		   
    		   }	  
          stage('Apply Kubernetes files') {
          withKubeConfig([credentialsId: 'kube-creds', serverUrl: 'https://192.168.0.4:6443']) {
		sh 'kubectl apply -f deployment.yaml'
	        sh 'kubectl apply -f service.yaml'
		  sh '''#!/bin/bash
			          kubectl patch svc service-website -n default -p '{"spec": {"type": "LoadBalancer", "externalIPs":["192.168.0.4"]}}
		         '''
		      }
		    }	  
	   }
