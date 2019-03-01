pipeline
{
	agent	any
	stages
	{
		stage ("build")
		{
			steps
			{
				echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
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
				sh "rm -rf /home/saurabh/Downloads/netdata/*"
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
				sh "/usr/bin/python3 /home/saurabh/PycharmProjects/netdata/netdata.py"
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
					echo "Artifact Location is:" ${env.WORKSPACE}
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