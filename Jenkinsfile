node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }
   /*
    stage('Build image for Docker Hub') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

    //    app = docker.build("24may/example-app")
    //}
    
    stage('Build image for QUAY Hub') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        app = docker.build("quay.io/andrey_kopitsa/example-app")
    }
    stage('Build image for ECR Hub') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        app = docker.build("0123456789.ecr.eu-west-1.amazonaws.com/example-app")
    }
    stage('Test') {
        app.inside{
            sh 'npm test'
        }
    }
    /*
    stage('Push image to Docker Hub') {
        /* Finally, we'll push the image into Docker Hub */
     
    //    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-creds') {
           /*  app.push("latest") */
	//	app.push("${env.BRANCH_NAME}-latest")
	//	app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
    //    }
    //}
   
    stage('Push image to Quay Hub') {
        /* Finally, we'll push the image into Docker Hub */

        docker.withRegistry('https://quay.io', 'quay-docker-creds') {
           /*  app.push("latest") */
		app.push("${env.BRANCH_NAME}-latest")
		app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
        }
    }
    stage('Push image to ECR Hub') {
        /* Finally, we'll push the image into Docker Hub */

        docker.withRegistry('https://0123456789.ecr.eu-west-1.amazonaws.com', 'ecr:eu-west-1.com:my-aws-creds') {
           /*  app.push("latest") */
		app.push("${env.BRANCH_NAME}-latest")
		app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
        }
    }
}

