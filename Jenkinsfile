@Library('My-Jenkins-SharedLibrary') _ 

pipeline {
   agent any
   
   stages {
       
        stage('EnterUserInput') {
         steps {
             script {
                 
                 def userInputTxt = input(
                                     id: 'inputTextbox', message: 'Please enter JOB Description', parameters: [
                                     [$class: 'TextParameterDefinition', description: 'String or Integer etc..',name: 'input']
                                    ])
                    echo ("JOB Description is: ${userInputTxt}")
                     
             }}   
        }
        
         stage('Upload a CSV') {
         steps {
             script {
                 
                        def inputCSVPath = input message: 'Upload file', parameters: [file(name: 'Release_Status.CSV.csv', description: 'Upload only CSV file')]
                        def csvContent = readFile "${inputCSVPath}"
                        
                         echo ("CSV FILE PATH IS : ${inputCSVPath}")
                         echo("CSV CONTENT IS: ${csvContent}") 
        }
                 
                 echo env.STAGE_NAME
                 echo '=========== Release_Status.CSV.csv=============='
           
                
                        
         }
      }
      stage('Email alert'){
         steps {
            
          emailext body: '', subject: 'upload completed csv file', to: 'jeevan010202@gmail.com'
         }
      }  
   }
  }
