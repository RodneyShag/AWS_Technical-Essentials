Notes on Amazon's [AWS Technical Essentials](https://acloud.guru/learn/aws-technical-essentials) course.

## 10000 ft Overview 1: Networking & Compute

- __Region__ - a geographic location with 2-3 availability zones
- __Availability zone__ - a data center
- __Edge Location__
    - a Content Delivery Network (CDN) endpoint for CloudFront
    - Example: Caches very large media (pictures, video).
    - Many more edge locations than there are regions.
- __VPC__
    - a virtual data center where you can deploy your assets.
    - Can have multiple VPCs per region.
- __Route 53__
    - Amazon's DNS Service
    - called Route 53 since port 53 is the DNS port.
- __Cloud Front__ - consists of edge locations that will cache assets such as video
- __Direct Connect__ - connects your physical data centers to AWS directly, using a dedicated (telephone) line, instead of through the internet. Could be done for security, but most of the time it's for having a reliable connection
- __EC2__ - just virtual machines in the cloud
- __EC2 Container Service__ - A container management service supporting "docker" containers. Allows you to run applications on a managed cluster of Amazon EC2 instances. Eliminates need for you to install/operate/scale your own cluster management infrastructure
- __Elastic Beanstalk__ - You can deploy your code here and it will provision all underlying infrastructure for it.
- __Lambda__ - _So EC2 is a virtual machine. You can access it using SSH and install things on there. So you have access to the operating system. Lambda is serverless, so you dont go into the operating system, you don't do anything with the underlying host. You just upload your code, and your code will respond to events._
- __Lightsail__ - out of the box cloud. Deploys wordpress, Juno sites. For people who don't know AWS.

## 10000 ft Overview 2: Storage, Databases, Migration & Analytics

### Storage

- __S3__ (Simple Storage Service)
    - a virtual disk in the cloud where you can store objects (files, like word/powerpoint documents, pictures, movies, text files)
    - don't install database here, or an application. installing computer games or database would not be in S3, it would be in "block-based storage"
- __Glacier__
    - you archive your files off of S3 into here.
    - extremely low cost
    - takes 3-4 hours to retrieve your data
- __EFS__ (Elastic File Service)
    - File-based storage, and you can share it.
    - You could install your databases/applications here, and share it with multiple virtual machines
- __Storage Gateway__
    - A way of connecting S3 to your on-premise data center

### Databases

- __RDS__ (Relational Database Service)
    - MySQL, SQL Server, Oracle, etc.
- __DynamoDB__
    - a non-relational database (NoSQL database)
- __Redshift__
    - Amazon's data warehousing solution. When you have a ton of data and you want to store it in a warehouse and only query it when you want to run reports. (You wouldn't want to query your production database since it would slow it down)
- __Elasticache__
    - caching your data in the cloud.

### Migration

- __Snowball__ - moving terabytes of data into cloud using a giant briefcase of data physically mailed to you.
- __DMS__ (Database Migration Service) - Move from 1 database (such as Oracle) into AWS
- __Server Migration Service (SMS)__ - for moving VMWare Virtual Machines

### Analytics

- __Athena__
    - allows you to run SQL queries on S3
    - Example: if you have bunch of CSV or JSON files in S3 buckets, you can write SQL queries on these
- __Elastic Map Reduce (EMR)__
    - for big data processing(such as log analysis, web indexing, or analyzing financial markets)
    - Uses Hadoop
- __Cloud Search / Elastic Search__
    - similar products
    - Used if you need to create a search engine.
    - Cloud Search is fully-managed by AWS
    - Elastic Search is open-source
- __Kinesis__
    - way of streaming/analyzing real-time data
- __Data Pipeline__
    - service that lets you move data from 1 place to another
    - Example move data from S3 into DynamoDB (or vice versa)
- __Quick Sight__
    - a business analytic tool that lets you create visualizations and rich dashboards for your data that exists in AWS.
    - Can analyze data in S3, DynamoDB, RDS, Redshift, etc.

## 10000 ft Overview 3: Security, Management, Tools, Application Services

### Security & Identity

- __IAM__ (Identity Access Management)
    - for signing into AWS, assign new users, how you assign users permissions, how you group users (administrative group, developer group, read-only group)
- __Inspector__ - inspects virtual machines and does security reporting of what's going on
- __Certificate Manager__ - gives you free SSL certificates for your domain names
- __Directory Service__ - Can connect "Active Directory" to AWS.
- __WAF__ (Web Application Firewall)
    - Gives you application-level protection to your website
- __Artifact__ - this is where you get your documentation in the AWS console (compliance documents). Very simple.

### Management Tools

- __Cloud Watch__ - used to monitor performance of your AWS environment
- __Cloud Formation__- a way of turning infrastructure into code. A document that describes your AWS environment. He loves it.
- __Cloud Trail__ - a way of auditing your AWS resources
- __Opsworks__ - automating deployments
- __Config__ (Config Manager)
    - monitors your environment and gives you warnings if your environment might break
- __Service Catalog__ - allows an enterprise to do authorizing.
- __Trusted Advisor__ - an automated way of getting automated tips for your environment.

### Application Services

- __Step Functions__ - a way of visualizing what's going on in your application, and what microservices its using
- __SWF__ (Simple Workflow Service) - a way of coordinating automated tasks and human tasks.
- __API Gateway__
    - allows you to create/publish/maintain/monitor/secure APIs at scale. A door for your apps to access backend data.
    - Example: AngularJS in client device makes call to API Gateway, then API Gateway triggers lambda functions to respond to the requests.
- __AppStream__ - a way of streaming desktop applications to your users
- __Elastic Transcoder__ - changes video format to work with all devices

### Developer Tools

- __CodeCommit__ - basically github
- __CodeBuild__ - a way of compiling your code
- __CodeDeploy__ - a way of deploying your code to EC2 instances, in a very automated and regular fashion.
- __CodePipeline__ - a way of keeping track of different versions of code.

### Mobile Services

 - __Mobile Hub__
     - lets you add, configure, and design features for your mobile apps. This includes user authentication, data storage, backend logic, push notifications, content delivery, and analytics.
     - you have AWS console, but Mobile Hub is it's own console for mobile apps, which contains thing such as AWS Cognito.
- __Cognito__
    - makes it easy for you to have users sign up and sign into your apps.
    - can sign in using Gmail.
    - First name, surname, email address would be stored in Cognito
    - Example: Instagram style client using AWS clients...You take a photo, and app stores photo in S3, writes metadata to dynamoDB, triggers lambda functions to generate thumbnails of that photo, stores people's user data in Cognito
- __Device Farm__ - lets you test your app on 100s of devices.
- __Mobile Analytics__ - collect and analyze app usage data.
- __Pinpoint__ - lets you understand and engage with your application users (Kind of like Google Analytics for mobile apps. See what users are doing with your app. Targeted marketing campaigns: who to engage, what notifications to send)

### Business Productivity

- __WorkDocs__ - securely storing your important work documents in the cloud, with security
- __WorkMail__ - a way of sending/receiving email

### Internet of Things
- __iOT__
    - huge service
    - millions of devices. Keeping track of them.

### Desktop & App Steaming

- __Workspaces__ - lets you have your desktop in the cloud
- __AppStream 2.0__ - a way of streaming desktop applications to your users

## 10000 ft Overview 4: AI, Messaging & Conclusion

### Artificial Intelligence

- __Polly__ - takes any text and changes into voice (such as into an mp3 file)
- __Machine Learning__ - give AWS a data set, and tell AWS the outcomes of that data set, and you can use this to predict outcomes for future data.
- __Rekognition__ - image recognition service

### Messaging

- __SNS__ (Simple Notification Service) - a way of notifying you by email, text message, etc.
- __SQS__
    - a way of decoupling your applications. A queue system. Post jobs to a queue.
    - Example: Lets say u have a website that generates memes, and somebody uploads a picture to the website, and puts some funny writing across it. SQS will store that as a job, and the EC2 instance that creates a picture and puts text across it will poll the SQS queue looking for jobs. If your EC2 instance dies while trying to make this, the message will still stay in the SQS queue.
- __SES__ (Simply Email Service) - A way of sending/receiving emails using AWS.
