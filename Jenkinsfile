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
				echo "Deleting older report, stopping/starting netdata..."
				sh """
					sudo rm -rf /home/saurabh/Downloads/netdata/*
					sudo service netdata stop
					sudo admin service netdata start
				"""
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
					/usr/bin/python3 /home/saurabh/PycharmProjects/netdata/netdata.py
				'''
			}
		}
		stage ("archive-report")
		{
			steps
			{
				echo "Archiving netdata report..."
				sh """
					echo "Artifact Location is:" ${env.WORKSPACE} ${env.BUILD_ID}
					mkdir -p ${env.WORKSPACE}/reports/${env.BUILD_ID}
					cp -rf /home/saurabh/Downloads/netdata/* ${env.WORKSPACE}/reports/${env.BUILD_ID}/
				"""
			}
		}
		stage ("netdata-end")
		{
			steps
			{
				echo "Stopping netdata..."
				sh '''
					sudo -u service netdata stop
				'''
			}
		}
	}
}