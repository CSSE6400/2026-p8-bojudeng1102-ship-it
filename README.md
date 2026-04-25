	1.	Added structured logging and correlation IDs to CloudWatch.
	2.	Deployed the application to AWS and ran the provided k6 scenarios.
	3.	Verified that POST and DELETE requests can succeed through logs and manual testing.
	4.	Observed repeated timeout failures on GET /api/v1/todos during load testing.
	5.	Concluded that the bottleneck is primarily read-side concurrency handling rather than simple API correctness.


    Load testing results show that the main bottleneck is not average request latency, but the application’s ability to handle large numbers of concurrent GET /api/v1/todos requests. Structured logs with correlation IDs confirmed that POST and DELETE requests can complete successfully, while many GET requests fail with timeout errors under load. Since successful requests still have relatively low latency, the main issue appears to be request throughput under concurrency rather than slow execution of individual successful requests.