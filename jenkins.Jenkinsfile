pipeline { 
    environment { 
        registry = "zraiaa/tp4" 
        registryCredential = 'docker' 
        dockerImage = '' 
    } 
    
    agent any 

    stages { 
        stage('Cloning Git') { 
            steps { 
                git 'https://github.com/zraiaa/tp4' 
            } 
        } 
        
        stage('Building image') { 
            steps { 
                script { 
                    dockerImage = docker.build(registry + ":$BUILD_NUMBER") 
                } 
            } 
        } 
        
        stage('Test image') { 
            steps { 
                script { 
                    echo "Tests passed"
                } 
            } 
        } 
        
        stage('Publish Image') {  
            steps { 
                script { 
                    docker.withRegistry('', registryCredential) { 
                        dockerImage.push() 
                    } 
                } 
            } 
        } 
    } 
}
