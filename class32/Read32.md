# Serverless

Serverless is a cloud computing execution model where the cloud provider dynamically manages the allocation and provisioning of servers

available cloud services
1. AWS Lambda
2. Google Cloud Functions
3. Azure Functions
4. IBM OpenWhisk
5. Alibaba Function Compute
6. Iron Functions
7. Auth0 Webtask
8. Oracle 7n Project
9. Kubeles9

* For years our applications have run on servers which we had to patch,update As long as you managed them, the whole responsibility of their proper functioning was on you but every thing changed by serverless you just need upload you app .

let's look for this advantages:

1. using Serverless is reduced cost 
2. in networking The downside is that Serverless functions are accessed only as private APIs.
3. for dependency we must package these dependencies into the application itself,
4. Setting up different environments for Serverless is easy
5. With Serverless computing, there’s a hard 300-second timeout limit.
6. Scaling process for Serverless is automatic and seamless

## FaaS
FaaS is an implementation of Serverless architectures where engineers can deploy an individual function or a piece of business logic

Principles of FaaS:
1. Complete management of servers
2. Invocation based billing
3. Event-driven and instantaneously scalabl2

properties of FaaS
1. With Serverless, everything is stateless
2. Ephemeral
3. functions can be invoked directly,
4. Scalable by default
5. Fully managed by a Cloud vendor


* A Serverless solution consists of a web server, Lambda functions (FaaS), security token service (STS), user authentication and database

![ Serverless App](https://miro.medium.com/max/1400/0*oTFla168vkxDc_zR)


## Benefits of Serverless Architecture

![Benefits](https://s7280.pcdn.co/wp-content/uploads/2018/01/key.png)


## Serverless Frameworks
1. Serverless Framework (Javascript, Python, Golang)
2. Apex (Javascript)
3. ClaudiaJS (Javascript)
4. Sparta (Golang)
5. Gordon (Javascript)
6. Zappa (Python)
7. Up (Javascript, Python, Golang, Crystal)

# AWS Amplify

AWS Amplify is a set of tools and services that can be used together or on their own, to help front-end web and mobile developers build scalable full stack applications

### Benefits
1. Configure backends fast
2. Seamlessly connect frontends
3. Deploy in a few clicks
4. Easily manage content


# API (GRAPHQL)

helps you quickly create backends for your web and mobile applications on AWS. With the GraphQL Transform

define your application’s data model using the GraphQL Schema Definition Language (SDL) and the library handles converting your SDL definition into a set of fully descriptive AWS CloudFormation templates that implement your data model.

### Create a GraphQL API
1. `amplify init`
2. `amplify add api`
   * Select GraphQL
   * When asked if you have a schema, say No
   * Select one of the default samples; you  can change this later
   * Choose to edit the schema and it will open the new schema.graphql in your editor
3. `amplify push`

for updatting schema `amplify api gql-compile` then `amplify push`

   