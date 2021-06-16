# Attach an API Gateway to a lambda function deployed with AWS CDK

**[📹 Video](https://egghead.io/lessons/aws-attach-an-api-gateway-to-a-lambda-function-deployed-with-aws-cdk)**


<TimeStamp start="0:19" end="0:57">


Now let's figure out how to trigger our function!

We need to attach an [API Gateway](https://aws.amazon.com/api-gateway/) which will allow us to call our `lambda` function from the internet.

![API Gateway Illustration](https://res.cloudinary.com/dg3gyk0gu/image/upload/v1592247659/transcript-images/08-attach-an-api-gateway-to-a-lambda-function-deployed-with-aws-cdk-api-gateway.png)

Run:
* `npm install --save @aws-cdk/aws-apigateway`

Then import it to the stack file:
`import * as apiGateway from "@aws-cdk/aws-apigateway";`
    
 </TimeStamp> 
 
 <TimeStamp start="1:01" end="1:41">


Now we will use `apiGateway` to create a REST API for our application.

Add the following before the closing of the `TodoAppStack` constructor:

```ts
new apiGateway.LambdaRestApi(this, "Endpoint", {
    handler: helloLambda
});
```
</TimeStamp>


 <TimeStamp start="1:43" end="1:55">

Let's also update the `body` of our handler inside our `lambda` function to:

`body: 'Hello, egghead friends! You've hit ${event.path}\n'`
    
</TimeStamp>
    
 <TimeStamp start="1:56" end="2:21">

Run `cdk diff` (a lot of changes will be displayed - this will be the code added by `cdk` due to adding `apiGateway`), then `cdk deploy`.
    
</TimeStamp>
    
 <TimeStamp start="2:32" end="2:53">

Once you've deployed successfully, the terminal will output a URL. Click on it to see your `lambda` function live on the internet.
 </TimeStamp>
   
 <TimeStamp start="3:11" end="3:29">

You can also check your newly created resources in the `aws` console. If you click on your `lambda` function you'll also see that this function now has a trigger (API Gateway) associated with it.
     </TimeStamp>

