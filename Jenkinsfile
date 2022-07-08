node{

   def tomcatWeb = 'C:\\Program Files\\Apache-tomcat\\apache-tomcat-8.5.81-windows-x64\\apache-tomcat-8.5.81\\webapps'
   def tomcatBin = 'C:\\Program Files\\Apache-tomcat\\apache-tomcat-8.5.81-windows-x64\\apache-tomcat-8.5.81\\bin'
   def tomcatStatus = ''
   stage('SCM Checkout'){
     git 'https://github.com/Nehanaren/JenkinsPipeline_Demo.git'
   }
   stage('Compile-Package-create-war-file'){
      // Get maven home path
      def mvnHome =  tool name: 'MAVEN_HOME', type: 'maven'   
      bat "${mvnHome}/bin/mvn package"
      }
/*   stage ('Stop Tomcat Server') {
               bat ''' @ECHO OFF
               wmic process list brief | find /i "tomcat" > NUL
               IF ERRORLEVEL 1 (
                    echo  Stopped
               ) ELSE (
               echo running
                  "${tomcatBin}\\shutdown.bat"
                  sleep(time:10,unit:"SECONDS") 
               )
'''
   }*/
   stage('Deploy to Tomcat'){
     bat "copy target\\JenkinsPipeline.war \"${tomcatWeb}\\JenkinsPipeline.war\""
   }
      stage ('Start Tomcat Server') {
         sleep(time:5,unit:"SECONDS") 
         bat "${tomcatBin}\\startup.bat"
         sleep(time:100,unit:"SECONDS")
   }
}
