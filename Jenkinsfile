pipeline
{
	agent	any
	stages
	{
		stage ("build")
		{
			steps
			{
				echo "Running Jenkin Job ID:${env.BUILD_ID} on ${env.JENKINS_URL}"
				echo "Building the code..."
			}	
		}
		stage ("deploy")
		{
			steps
			{
				echo "Deploying into container..."
			}	
		}
		stage ("netdata-init")
		{
			steps
			{
				echo "Deleting older report..."
				sh 'rm -rf /home/saurabh/Downloads/netdata/*'
				echo "Starting netdata..."
			}	
		}
		stage ("test")
		{
			steps
			{
				echo "Starting test execution..."
			}	
		}
		stage ("netdata-capture")
		{
			steps
			{
				echo "Capturing netdata report..."
				sh '''
					pip3 install selenium --proxy=194.138.0.25:9400
					sh "/usr/bin/python3 /home/saurabh/PycharmProjects/netdata/netdata.py"
				'''
			}
		}
		stage ("archive-report")
		{
			steps
			{
				echo "Archiving netdata report..."
				sh """
					cd /home/saurabh/Downloads/netdata/
					tar -cvf netdata.tar *
					echo "Artifact Location is:" ${env.WORKSPACE} ${env.BUILD_ID}
				"""
			}
		}
		stage ("netdata-end")
		{
			steps
			{
				echo "Ending netdata..."
			}
		}
	}
}