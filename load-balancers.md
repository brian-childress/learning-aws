### Load Balancers

- Application Load Balancers (ALB)
  - Best suited for balancing HTTP and HTTPS traffic.
  - Operate at Layer 7 and are application aware
    - They are intelligent, can handle advanced request routing, sending specific requests to specific web servers.
    - Need at least 2 public subnets in order to deploy an ALB
- Network Load Balacers
  - Best suited for balancing TCP traffic where extreme performance is required. Operating at the connection level (layer 4)
  - Capable of handling millions of requests per second, while maintaining ultra-low latencies
  - Use for extreme performance
- Classic Load Balancers, formerly Elastic Load Balancer (ELB)
  - Can balance HTTP/HTTPS applications and use layer 7-specific features, such as X-forwarded and sticky sessions.
  - Can use strict layer 4 load balancing for applications that rely purely on TCP protocol.

#### Errors
- 504: ELB will return if the applicaiton stops responding. EX: DB connection error, web server stopped, etc.
  - Identify where application is failing and scale up or out

#### X-Forwarded-For Header

Allows and ELB to have access to the public IP address accessing a site through an ELB by passing the public IP address in a `X-Forwarded-For` header.