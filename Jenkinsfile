pipeline
{
	agent	any
	stages
	{
		stage ("build")
		{
			steps
			{
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
		stage ("netdata-end")
		{
			steps
			{
				echo "Capturing netdata report..."
			}
		}
	}
}
