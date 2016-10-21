node ('linux'){
   wrap([$class: 'TimestamperBuildWrapper']) {
   // Mark the code checkout 'stage'....
   stage 'Checkout'
      
      checkout scm

   // Get some code from a GitHub repository
   //git url: 'https://github.com/InfostretchRajendra/awesome-git-folder.git'
   sh "echo SCM clone succcessful"

   // Get the maven tool.
   // ** NOTE: This 'M3' maven tool must be configured
   // **       in the global configuration.           
   // mvnHome = tool 'M2'

   // Mark the code build 'stage'....
   stage 'Build'
   // Run the maven build
   //sh "mvn -Dmaven.test.failure.ignore clean package"
   sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
   step([$class: 'JUnitResultArchiver', testResults: '**/target/surefire-reports/TEST-*.xml'])
   step([$class: 'WsCleanup', notFailBuild: true])
   }
}
