pipeline 
 {
   agent any 
   stages
     {
        stage('ContinuousDownload')
          {
          steps
             { 
              git 'https://github.com/intelliqittrainings/maven.git'
             }
         }
   stage('Continuousbuild')
          {
          steps
             { 
              sh'mvn package'
             }
         }
     stage('Continuousdeployemnt')
          {
          steps
             { 
              deploy adapters: [tomcat9(credentialsId: 'ec582733-3a88-419f-9213-c5bbb2bf1afd', path: '', url: 'http://172.31.7.168:8080')], contextPath: 'testapp', war: '**/*.war'
             }
         }
   stage('Continuoustesting')
          {
          steps
             { 
              git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
              sh 'java -jar /home/ubuntu/.jenkins/workspace/DeclarativePipeline1/testing.jar'
             }
         }
         stage('Continuousdelivery')
          {
          steps
             { 
              deploy adapters: [tomcat9(credentialsId: 'ec582733-3a88-419f-9213-c5bbb2bf1afd', path: '', url: 'http://172.31.6.36:8080')], contextPath: 'myprodapp', war: '**/*.war'
             }
         }



    }
}
