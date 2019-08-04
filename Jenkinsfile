node {
    stage('Code Checkout') { // for display purposes
     echo 'Checout Code and clone it inside jenkins workspace.'
     git 'https://github.com/imransheik96/sonar-maven.git'
   //}
   stage('Build Test & Package') {
      echo 'Build the package'
      withMaven(jdk: 'java', maven: 'maven') {
       sh 'mvn clean install'
     }
   }
   stage('SonarScan') {
      //withSonarQubeEnv('SonarQube') {
         withMaven(jdk: 'java', maven: 'maven') {
             //sh 'mvn clean package sonar:sonar' 
             sh 'mvn org.jacoco:jacoco-maven-plugin:prepare-agent package sonar:sonar' +
             ' -Dsonar.host.url=https://sonarcloud.io '+
             ' -Dsonar.organization=itrainavengers '+ 
             ' -Dsonar.login=c1f3a8036d378aacc1f6e6e2fc6dcd7de2ebae5d '   
         //}
      }
   }
   stage('Artifacts') {
       echo 'package the project artifacts..'
       withMaven(jdk: 'java', maven: 'maven') {
       sh 'mvn package'
     }
   
   }
   stage('Deploy to Dev'){
       echo 'Deploy to Dev environment'
   }
   stage('Deploy to Test'){
       echo 'Deploy to Test environment'
   }
      stage('Test Automation'){
       echo 'Deploy to Dev environment'
   }
   
}
