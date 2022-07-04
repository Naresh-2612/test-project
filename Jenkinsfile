//lines 1-28 pretty basic for a CICD setup. The new stage for certificate starts after line# 28

pipeline {
agent any
stages {
stage('Build Application') {
steps {
sh 'mvn clean install'
}
}
stage('Test') {
steps {
echo 'Application in Testing Phase…'
sh 'mvn test'
}
}
stage('Deploy CloudHub') {
environment {
ANYPOINT_CREDENTIALS = credentials('anypointPlatform')
}
steps {
echo 'Deploying mule project due to the latest code commit…'
echo 'Deploying to the configured environment….'
 sh 'mvn package deploy -DmuleDeploy -Dusername=${ANYPOINT_CREDENTIALS_USR} -Dpassword=${ANYPOINT_CREDENTIALS_PSW} -DworkerType=Small -Dworkers=1 -Dregion=us-west-2'
}
}



}
}
