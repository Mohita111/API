# What is Amazon VPC?

With Amazon Virtual Private Cloud (Amazon VPC), you can launch AWS resources in a logically isolated virtual network that you've defined. This virtual network closely resembles a traditional network that you'd operate in your own data center, with the benefits of using the scalable infrastructure of AWS.

The following diagram shows an example VPC. The VPC has one subnet in each of the Availability Zones in the Region, EC2 instances in each subnet, and an internet gateway to allow communication between the resources in your VPC and the internet.

# Why Amazon VPC Lattice?

Amazon VPC Lattice automatically manages network connectivity and application layer routing between services across different VPCs and AWS accounts. It also enables connectivity to TCP resources, such as databases, domain names, and IP addresses across VPCs and accounts. You can operate your network without having to manage underlying network connectivity, frontend load balancers, or sidecar proxies next to every workload. Amazon VPC Lattice integrates with AWS Identity and Access Management (IAM) to provide you the same familiar authentication and authorization capabilities when using other AWS services. By using Amazon VPC Lattice, you can choose from different compute types, such as instances, containers, and serverless, for a given service, helping you modernize from a monolithic application architecture to a microservices architecture. This capability also helps improve scalability and cost efficiency.

Amazon VPC Lattice manages all of your service-to-service and service-to-resource connectivity, security, and monitoring needs so that you can focus on your application logic and deliver applications faster.
