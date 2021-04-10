# sample-springboot-pipeline
# Modify the files according to your requirements.
CloudFormation template will create the required infrastructure on AWS. Jenkins, Ansible and required dependencies will also get installed.
Jenkins file will fetch the code and build the artefact and store it locally.
Ansible playbook will copy the created jar file on the private server and deploy it.
