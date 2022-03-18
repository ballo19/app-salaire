node{
    stage('Clone git') {
        checkout scm
    }
    stage('Prerequis'){
        sh apk add ansible sshpass
        sh echo '172.25.169.157 app-salaire.form' > /etc/hosts
        sh rm -rf /root/.ssh
        sh ssh-keygen -q -t rsa -N '' -f ~/.ssh/id_rsa
        sh sshpass -p 'centos' ssh-copy-id -o stricthostkeychecking=no root@app-salaire.form
    }
    stage('Ansible') {
      ansiblePlaybook (
          colorized: true,
          playbook: 'playbook.yaml',
