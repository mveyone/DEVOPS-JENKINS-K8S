# best-node-ejs-last-mongodb-docker
# pvc-mongodb-app-k8s

node{
    stage('git checkout'){
       git branch: 'main', credentialsId: 'github', url: 'https://github.com/mveyone/DEVOPS-JENKINS-K8S.git'
    }
    stage('sending dockerfile to ansible server'){
        sshagent(['ansible-app']) {
         sh 'ssh -o StrictHostKeyChecking=no ubuntu@172.31.92.42 '
         sh 'scp /var/lib/jenkins/workspace/DEVOPS-CICD/* ubuntu@172.31.92.42:/home/ubuntu '
      }
    }
}
we use the skey pair of aws