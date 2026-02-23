pipeline{
  agent any
    environment{
      IMAGE_NAME1 = "dockerayush039/frontendapp"
      IMAGE_NAME2 = "dockerayush039/backendapp"
      SERVER_IP = credentials('prod-server-ip')
     }
    stages{
      stage('Log In To Docker'){
        steps{
          withCredentials([
             usernamePassword( credentialsID:'docker-creds', usernameVariable:'USERNAME' , passwordVariable:'PASSWORD')]) {
                sh "echo ${PASSWORD} | docker login -u ${USERNAME} --password-stdin"}
                 echo "Login Successful"
              }
            }
        stage('Build and Push Image'){
          steps{
             dir('frontend'){
                 sh "docker build -t ${IMAGE_NAME1} ."
                 sh "docker push ${IMAGE_NAME1}"
               }
             dir('backend'){
                 sh "docker build -t ${IMAGE_NAME2} ."
                 sh "docker push ${IMAGE_NAME2}"
             }
           }
         }
        stage('SSH to server and deploy redeploy the docker-compose'){
          steps{
            withCredentials([
                 sshUserPrivateKey(credentialsID: 'ssh-key', keyFileVariable: 'MY_SSH_KEY' , usernameVariable: 'username')]) {
                      sh '''ssh -i $MY_SSH_KEY -o StrictHostKeyChecking=no ${username}@${SERVER_IP} << EOF
                         docker-compose down
                         docker-compose up -d
EOF
'''
} } } } }
