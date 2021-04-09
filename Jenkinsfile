timestamps {
node("${env.JENKINS_NODE_NAME}") {
stage('CLONE SCM') {
sh '''
rm -rf spring-petclinic
git clone https://github.com/honey2104/sample-springboot-pipeline.git
mv sample-springboot-pipeline/* .
rm -rf sample-springboot-pipeline
git clone ${SCM_REPOSITORY_URL}

'''
}
stage('BUILD ARTIFACT') {
sh '''
cd spring-petclinic
pwd
./mvnw package
sudo cp ${WORKSPACE}/spring-petclinic/target/spring-petclinic-2.4.2.jar /mnt/artefact/
'''
}
stage('DEPLOY ARTIFACT') {
sh '''
pwd
sed -i s/REMOTEHOST/${REMOTEHOST}/g ansibleUtils/hosts
ansible-playbook -i ansibleUtils/hosts ansibleUtils/playbook.yaml 


'''
}
stage('TEST APPLICATION') {
sh '''
echo "Waiting for 60 secs for application to come up"
sleep 60
curl http://${REMOTEHOST}:8080 2>/dev/null
'''
}
}
}
