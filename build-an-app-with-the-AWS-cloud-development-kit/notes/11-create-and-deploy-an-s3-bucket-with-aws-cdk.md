# Create and deploy an S3 bucket with AWS CDK

**[📹 Video](https://egghead.io/lessons/aws-create-and-deploy-an-s3-bucket-with-aws-cdk)**

<TimeStamp start="0:08" end="0:18">


We'll need storage for our static files (`HTML`, `CSS`, images etc). Let's use [Amazon S3](https://aws.amazon.com/s3/) for that.
    
 </TimeStamp>

![S3 Buckets Illustration](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1592247658/transcript-images/11-create-and-deploy-an-s3-bucket-with-aws-cdk-s3-buckets.png)

<TimeStamp start="0:35" end="1:34">


We'll create a new `aws` bucket to store our data!

Run:

* `npm install --save @aws-cdk/aws-s3`

Import it into our stack document:

* `import * as s3 from "@aws-cdk/aws-s3";`

Let's create a new bucket for storing a logo:

```ts
const logoBucket = new s3.Bucket(this, "LogoBucket", {
    // we will fill this out later
});
```

Run:
*  `cdk diff` and `cdk deploy`.
    
</TimeStamp>

<TimeStamp start="1:36" end="1:45">

You can find the bucket under `aws` resources (search for `s3`). 
    </TimeStamp>

