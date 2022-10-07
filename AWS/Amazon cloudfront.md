## Amazon cloudfront
A web service that speeds up distribution of static and dynamic web content, html, css, js. and image files. Delivers content trough worlwide network data centers called edge locations. When a user requests content that you're serving with CloudFront, the request is routed to the edge location that provides the lowest latency.

CloudFront speeds up the distribution of your content by routing each user request through the AWS backbone network to the edge location that can best serve your content.

Users get lower latency—the time it takes to load the first byte of the file—and higher data transfer rates.

### How configure CloudFront
1. You specify _origin servers_, like an Amazon S3 bucket or your own HTTP server. Your HTTP server can run on an Amazon Elastic Compute Cloud (Amazon EC2) instance or on a server that you manage; these servers are also known as _custom origins._
2. Upload your files to your origin server. This files are also known as objects. 
3. Create a CloudFront distribution: which tells CloudFront which origin servers to get your files from when users request the files through your web site or application.
4. CloudFront assigns a domain name to your new distribution that you can see in the CloudFront console, or that is returned in the response to a programmatic request.
5. CloudFront sends your distribution's configuration (but not your content) to all of its _edge locations_ or _points of presence_ (POPs)

Optionally, you can configure your origin server to add headers to the files, to indicate how long you want the files to stay in the cache in CloudFront edge locations. By default, each file stays in an edge location for 24 hours before it expires. The minimum expiration time is 0 seconds; there isn't a maximum expiration time.

- **Accelerate static website content delivery** : A simple approach for storing and delivering static content is to use an Amazon S3 bucket. Using S3 together with CloudFront has a number of advantages, including the option to use [origin access control](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/private-content-restricting-access-to-s3.html) to easily restrict access to your S3 content.

**Customize at the edge** : Running serverless code at the edge opens up a number of possibilities for customizing the content and experience for viewers, at reduced latency. For example, you can return a custom error message when your origin server is down for maintenance, so viewers don't get a generic HTTP error message. Or you can use a function to help authorize users and control access to your content, before CloudFront forwards a request to your origin.