# Command Line Interface (CLI)

Accessing Instance Metadata 
In EC2 instance
`curl http://169.254.169.254/latest/meta-data/`
`curl http://169.254.169.254/latest/user-data/`

Can then write to a text file, copy to s3, Lambda is triggered to make updates to Route53
 