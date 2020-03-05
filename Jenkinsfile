pipeline {
    agent {
        label 'testagent'
    }
    stages {
        stage ('Copying code to workspace') {
            steps{
			checkout scm 
                }
			 post {
                success {
                    echo "code copied to workspace"
                }
                failure {
                    echo "scm checkout stage failed"
                }
            }
        }
		stage ('Test') {
            steps{
               testcompletetest commandLineArguments: '/r /Exportlog:Z:\\Result.txt /ExportLogToXMLAlso /ExportSummary:Z:\\Summary /exit', generateMHT: true, suite: 'Orders_C#_Python.pjs', useTCService: true, userName: 'CandP', userPassword: 'Myaccount@123'
            }
			post {
                success {
                    echo "Test executed successfully"
                }
                failure {
                    echo "Test Execution failed"
                }
            }
        }
    }
}