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
				
				bash '''#!/bin/bash
				rm -rf /home/saurabh/Downloads/netdata/*
				'''				
				echo "Starting netdata..."
			}	
		}
	}
}