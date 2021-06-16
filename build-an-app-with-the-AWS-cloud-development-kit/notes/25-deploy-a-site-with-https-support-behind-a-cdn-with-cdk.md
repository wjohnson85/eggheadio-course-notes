# Deploy a site with HTTPS support behind a CDN with CDK

**[📹 Video](https://egghead.io/lessons/aws-deploy-a-site-with-https-support-behind-a-cdn-with-cdk)**

We want our website to be secure and served on `https` (and not on `http`) - let's fix that.

Also, in the previous lesson, we had to type out the three steps for deploying our frontend:

* Creating a bucket
* Creating a bucket deployment
* Creating a CloudFormation output

 <TimeStamp start="0:36" end="1:09">


We can solve both things by using [CDK-SPA-Deploy](https://github.com/nideveloper/CDK-SPA-Deploy)! It can be used to deploy an SPA (Single Page Application), written in `reactJS` (or Angular/Vue) to `aws` behind SSL (meaning `https`) on CloudFront.

To add it, run:
* `npm install --save cdk-spa-deploy`

🤔 [Cloudfront](https://aws.amazon.com/cloudfront/) is Amazon's CDN (Content Delivery Network).
 
 </TimeStamp>

![CDN Illustration](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1592247660/transcript-images/25-deploy-a-site-with-https-support-behind-a-cdn-with-cdk-cdn.png)


<TimeStamp start="0:36" end="1:09">
 
 <TimeStamp start="1:34" end="2:18">

Import it to the stack file:

* `import { SPADeploy } from "cdk-spa-deploy";`

Then comment out (or remove) the three sections that we wrote in the last time lesson and replace them with:

```ts
new SPADeploy(this, "WebsiteDeployment").createSiteWithCloudfront({
    indexDoc: "index.html",
    websiteFolder: "../frontend/build"
});
```
   </TimeStamp>


🤔 You can check out the source code [here](https://github.com/tlakomy/egghead-aws-cdk-workshop/blob/master/todo-app/lesson_13/lib/todo-app-stack.ts).
