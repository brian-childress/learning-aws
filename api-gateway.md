# API Gateway

- Publish, maintain, monitor, and secure APIs at scale
- API acts as a 'front door' for applications to access data, business logic, or functionality from back-end services such as EC2, Lambda, etc.
- Enable caching to:
  - Reduce number of calls to endpoint
  - Improve latency
  - Improve performance
  - Caching for a specified TTL instead of repeated calls to endpoint
- Low cost & efficient
- Can log all requests to CloudWatch
- Scales effortlessly
- Can throttle requests to help prevent attacks

## Same Origin Policy
- Web applications must share the same origin in order for scripts to execute
  - Can enable CORS on API Gateway