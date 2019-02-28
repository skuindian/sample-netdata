pipeline
{
	agent	any
	stages
	{
		stage ("build")
		{
			steps
			{
				echo "Building..."
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
				echo "Starting test..."
			}	
		}
		stage ("netdat-end")
		{
			steps
			{
				echo "Capturing netdata report..."
			}	
		}
	}
}
