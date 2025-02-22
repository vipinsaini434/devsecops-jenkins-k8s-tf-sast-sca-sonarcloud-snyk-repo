pipeline {
  agent any
  tools { 
        maven 'Maven_3_5_2'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
             steps {	
		sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=secchampquantum -Dsonar.organization=secchampquantum -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=93650f4e4920a3da1eeb0ccaa5a303906088686c'
			}
        } 

	stage('RunSCAAnalysisUsingSnyk') {
          steps {		
				withCredentials([string(credentialsId: 'SNYK_TOKEN', variable: 'SNYK_TOKEN')]) {
					sh 'mvn snyk:test -fn'
				}
			}

    }		
  }
}
