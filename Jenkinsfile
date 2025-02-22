pipeline {
  agent any
  tools { 
        maven 'Maven_3_5_2'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=asgbuggywebapp -Dsonar.organization=asgbuggywebapp -Dsonar.host.url=https://sonarcloud.io -Dsonar.token=932558e169d66a8f1d1adf470b908a46156f5844'
			}
    }

	stage('RunSCAAnalysisUsingSnyk') {
           steps {		
    sh 'SNYK_TOKEN=9b0132f6-2f59-4750-ace4-bc1aecd0c65b mvn snyk:test -fn'
}

    }		
  }
}
