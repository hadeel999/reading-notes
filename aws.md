# AWS Cloud Servers

## AWS EC2

### What is an EC2 Instance ?
Secure and resizable compute capacity for virtually any workload.

**Amazon Elastic Compute Cloud** (Amazon EC2) offers the broadest and deepest compute platform, with over 500 instances and choice of the latest processor, storage, networking, operating system, and purchase model to help you best match the needs of your workload. 

### Use Cases
- Run cloud-native and enterprise applications.
- Scale for HPC applications.
- Develop for Apple platforms.
- Train and deploy ML applications.

### AWS vs Heroku
Heroku is suitable for smaller cloud apps. Depending on your project, Heroku can be expensive if the app is intensive on traffic.

AWS is perfect for medium and large businesses. It should be chosen when one needs flexibility right from the initial application deployment.

## EC2 For Humans

### Where can we find EC2 on the AWS Console ?
To connect to your instance using the browser-based client from the Amazon EC2 console:
- Open the Amazon EC2 console at https://console.aws.amazon.com/ec2/.
- In the navigation pane, choose Instances.
- Select the instance and choose Connect.
- Choose EC2 Instance Connect.
- Verify the user name and choose Connect to open a terminal window.

### Difference between T2 Micro and X1
T2 instances are a low-cost, general purpose instance type that provides a baseline level of CPU performance with the ability to burst above the baseline when needed.

X1 Instances are a part of the Amazon EC2 memory-optimized instance family and are designed for running large-scale and in-memory applications in the AWS Cloud.

Compared to other EC2 instances, X1 instances have one of the lowest price per GiB of RAM, and are ideal for running in-memory databases like SAP HANA, big data processing engines like Apache Spark or Presto, and high-performance computing (HPC) applications.

### [Learn More](https://www.youtube.com/watch?v=lZMkgOMYYIg) 

## Elastic Beanstalk

Elastic Beanstalk is an easy-to-use service that deploys managesand scales web apps and sevices for you.

### Relationship Between EC2 and Elastic Beanstalk
Elastic Beanstalk is one layer of abstraction away from the EC2 layer. Elastic Beanstalk will setup an "environment" for you that can contain a number of EC2 instances, an optional database, as well as a few other AWS components such as a Elastic Load Balancer, Auto-Scaling Group, Security Group.

### Benefits of Using Elastic Beanstalk
- Timesaving server configuration.
- Powerful customization.
- Cost-effective price point.

## References:

[AWS EC2](https://aws.amazon.com/ec2/)

[EC2 For Humans](https://www.youtube.com/watch?v=lZMkgOMYYIg)

[Elastic Beanstalk](https://www.youtube.com/watch?v=SrwxAScdyT0)


### [Home Page](./README.md)

