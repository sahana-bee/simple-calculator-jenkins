pipeline {
agent any

stages {
stage('SCM Synchronization') {
steps {
echo ' Pulling latest code changes from Git repository...'
checkout scm
}
}

stage('Static Verification') {

steps {
echo ' Checking Maven project layout rules...'
bat 'mvn validate'
}
}

stage('Compilation & Automated Testing') {
steps {
echo ' Compiling class layers and verifying test logic stability...'
bat 'mvn clean package'
}
post {
always {
echo ' Publishing Unit Test trends to Jenkins Dashboard...'
junit '**/target/surefire-reports/*.xml'
}
}
}
}

post {
success {
echo ' CI Pipeline completed flawlessly! Code stability confirmed.'
}
failure {
echo ' CI Pipeline broken. Check console logs for build failures or breaking test
regressions.'
}
}
}