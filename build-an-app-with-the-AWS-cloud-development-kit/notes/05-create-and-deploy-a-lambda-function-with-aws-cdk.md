# Create and deploy a lambda function with AWS CDK

**[📹 Video](https://egghead.io/lessons/aws-create-and-deploy-a-lambda-function-with-aws-cdk)**

Time to build our serverless backend!

<TimeStamp start="0:09" end="0:22">


We'll be writing our first `lambda` function. In order to do that, let's run:

* `npm install --save @aws-cdk/aws-lambda`

Since we are using `typescript` we'll also:

* `npm install --save @types/aws-lambda`
    
 </TimeStamp>
 
 <TimeStamp start="0:23" end="0:37">


👍 We needed to install `aws-lambda` separately because it's not part of the core aws package. See which other constructs/packages are available in CDK [here](https://docs.aws.amazon.com/cdk/api/latest/docs/aws-lambda-readme.html).
 </TimeStamp>

 <TimeStamp start="0:58" end="1:22">

Inside our `todo-app` will create a new directory called `lambda` and inside of it, a `hello.ts` file with the following contents.

```ts
// we are going to call this function via APIGatewayEvent which is used for http requests
exports.handler = async function(event: AWSLambda.APIGatewayEvent) {
    // this is a neat trick to prettify the console log
    console.log("request:", JSON.stringify(event, null, 2));

    // this is what calling this lambda function will return
    return {
        statusCode: 200,
        headers: { "Content-Type": "text/plain" },
        body: `Hello, egghead friends!`
    };
};
```
 </TimeStamp>
    

 <TimeStamp start="1:47" end="2:27">

We need to import the lambda function into our stack file:
* `import * as lambda from "@aws-cdk/aws-lambda";`

Then we'll create an instance of our lambda construct, with three arguments:

1. scope (in which the construct is created): usually `this`
2. `id`
3. `props` objects (`code`, `handler` and `runtime` are obligatory)

```ts
const helloLambda = new lambda.Function(this, "HelloLambda", {
  // where our code is located (inside the lambda directory)
    code: lambda.Code.fromAsset("lambda"),
    // the function executed whenever this lambda function is triggered (the handler function inside hello.ts file)
    handler: "hello.handler",
    // most recent node
    runtime: lambda.Runtime.NODEJS_12_X,
});
```
</TimeStamp>

 <TimeStamp start="3:25" end="3:47">

Run `cdk diff` to see the two new resources:

```
Resources
[+] AWS::IAM::Role HelloLambda/ServiceRole
[+] AWS::Lambda::Function HelloLambda
```

Then `cdk deploy`
 </TimeStamp>
   

👍 Note, if you get the following error (I did): `Error: This stack uses assets, so the toolkit stack must be deployed to the environment`, run `cdk bootstrap` to finish configuring your account and avoid this error in the future.
