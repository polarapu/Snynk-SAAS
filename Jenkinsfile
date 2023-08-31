pipeline {
  agent any
  tools { 
        maven 'Maven'  
    }
   stages{
    stage('CompileandRunSonarAnalysis') {
            steps {	
		sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=devsecopstest1 -Dsonar.organization=devsecopstest1 -Dsonar.host.url=https://sonarcloud.io -Dsonar.login=88b64b5d604cc911905e0de343cc4fe9af13104e'
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
