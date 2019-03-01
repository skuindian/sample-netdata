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
				rm -rf /home/saurabh/Downloads/netdata/*
				echo "Starting netdata..."
				#killall netdata &
				#/usr/sbin/netdata &
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
				python3 /home/saurabh/PycharmProjects/netdata/netdata.py
			}
		}
		stage ("archive-report")
		{
			steps
			{
				echo "Archiving netdata report..."
				cd /home/saurabh/Downloads/netdata/
				tar -cvf netdata.tar *
				echo "Artifact Location is:" ${env.WORKSPACE}
				#mkdir -p ${env.WORKSPACE}/reports/${env.BUILD_ID}
				#cp -rf /home/saurabh/Downloads/netdata/ ${env.WORKSPACE}/reports/${env.BUILD_ID}
			}
		}
		stage ("netdata-end")
		{
			steps
			{
				echo "Ending netdata..."
				#killall netdata &
			}
		}
	}
}
