# Cold start

Cold start has always been the most important performance factor in @amilochau applications. Using serverless technologies, with the lowest CPU and memory needed, require the applications to be as optimized as possible.

The @amilochau applications are designed with the following considerations:
- We expect that each request reaching the back-end is the first request - so that we pay the cold start for each request
- We want to keep a high level of security, including encryption (at rest, in transit) and authentication (from clients, to dependencies; secretless)
- The applications must be scalable, so that millions of request work as well as single request per day
- Pay-as-you-go pricing model is used everywhere - we don't want fixed costs

With these considerations in mind, some solutions are easily eliminated, as caches (high cost) or SSL certificates non-validation. Some solutions have already been implemented, are regularly maintained, including:
- Using latest .NET version
- Using `al.2023` base image for AWS Lambda
- Using native AOT compilation
- Re-writing AWS SDK to remove useless code, remove code reflection, rewrite serializers
- Re-writing AWS Lambda and AWS XRay libraries

The following table summarizes the most important challenges faced to improve cold start.

| Topic | Description | Solutions |
| ----- | ----------- | --------- |
| Instance creation | Each time a serverless application scales, a new instance is created. To be created, the application artifact (as a Docker image or a ZIP with binaries) must be downloaded, and mounted in memory. | Don't use containers; reduce the size of binaries as much as possible |
| Binaries size | The size of the application has a direct effect on cold start (10 MB ~= 1000 ms cold start). | Reduce dependencies number as much as possible; use tree-shaking; split in simple microservices; simplify code with low-level configuration |
| JIT | Just-in-time compilation has performance impacts on first call. | Build applications to native code - as with native AOT for .NET |
| TLS handshake | The first request to a dependency using TLS is slow to validate certificate. | |

Possible solutions are summarized in the next table - with their tradeoffs.

| Topic | Description | Tradeoffs |
| ----- | ----------- | --------- |
| S3 for binaries | Use an S3 bucket, instead of functions code storage, to store application binaries | Pay S3 storage; performance impact tested on 2024 Q1 as negative. |
| Group endpoints | Use a single function to handle multiple HTTP routes, or multiple event types. | Binary size increases, logics is harder to test |
| Expose databases | Read on databases instead of HTTP endpoints for internal services. | Database structure becomes the API; logics is harder to enforce |
| Increase CPU | Giving more CPU to functions could help them perform the TLS handshake. | Huge cost implication |

Expected improvements from providers, in the coming months or years, can help on cold start.

| Provider | Topic | Description | Block | Documentation |
| -------- | ----- | ----------- | ----- | ------------- |
| GitHub | ARM/x64 | Using ARM instances can improve performances and decrease costs. | GitHub has to host ARM runners for GitHub actions | [GitHub issue](https://github.com/github/roadmap/issues/970) |
| AWS | HTTP/2 support for DynamoDB | DynamoDB is the main dependency in our applications. Supporting HTTP/2 (or higher) can help improve performances, for TLS handshake and when sending multiple requests. | HTTP/2 is not supported by AWS DynamoDB | [Stackoverflow question](https://stackoverflow.com/questions/68779122/does-amazon-dynamodb-supports-http-2) |
