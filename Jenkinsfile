pipeline {
agent any
stages {
stage('Compile') {
steps {
dir('/home/felipe/Documentos/DEVOPS/MODULO3/MAVEN/ejemplo-maven'){
sh './mvnw clean compile -e'
}
}
}
stage('Unit Test') {
steps {
dir('/home/felipe/Documentos/DEVOPS/MODULO3/MAVEN/ejemplo-maven'){
sh './mvnw clean test -e'
}
}
}
stage('Package') {
steps {
dir('/home/felipe/Documentos/DEVOPS/MODULO3/MAVEN/ejemplo-maven'){
sh './mvnw clean package -e'
}
}
}
stage('Run') {
steps {
dir('/home/felipe/Documentos/DEVOPS/MODULO3/MAVEN/ejemplo-maven'){
sh 'nohup bash mvnw spring-boot:run &'}
}
}
stage('Test') {
steps {
script{
dir('/home/felipe/Documentos/DEVOPS/MODULO3/MAVEN/ejemplo-maven'){
sleep 60
final String url =
'http://localhost:8081/rest/mscovid/test?msg=testing'
final String response = sh(script: "curl -X GET $url",
returnStdout: true).trim()
echo response
}
}
}
}
}
}
