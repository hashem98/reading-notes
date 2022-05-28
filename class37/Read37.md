# Amazon S3

Amazon Simple Storage Service (Amazon S3) is storage for the Internet. It is designed to make web-scale computing easier

## Advantages of using Amazon S3

- Creating buckets : is a container for objects stored in Amazon S3
- Storing data
- Downloading data
- Permissions 
- Standard interfaces

*Objects*: Objects consist of object data and metadata.
*Keys* : A key is the unique identifier for an object within a bucket.
*Regions* : You can choose the geographical AWS Region where Amazon S3 will store the buckets that you create

## Amazon S3 data consistency model
Amazon S3 provides strong read-after-write consistency for PUTs and DELETEs of objects in your Amazon S3 bucket in all AWS Regions.

Amazon S3 achieves high availability by replicating data across multiple servers within AWS data centers. If a PUT request is successful, your data is safely stored. Any read (GET or LIST) that is initiated following the receipt of a successful PUT response will return the data written by the PUT

### Amazon S3 features
- Amazon S3 offers a range of storage classes designed for different use cases
- Bucket policies provide centralized access control to buckets and objects based on a variety of conditions, including Amazon S3 operations, requesters, resources, and aspects of the request

* You can use AWS Identity and Access Management (IAM) to manage access to your Amazon S3 resources.

* You can control access to each of your buckets and objects using an access control list (ACL)

* You can use versioning to keep multiple versions of an object in the same bucket.

### Common operations
- Create a bucket
- Write an object
- Read an object
- Delete an object
- List keys

### Amazon S3 application programming interfaces (API)

* it's provides a REST and a SOAP interface

*The REST interface*
The REST API is an HTTP interface to Amazon S3. Using REST, you use standard HTTP requests to create, fetch, and delete buckets and objects.

*The SOAP interface*
The SOAP API provides a SOAP 1.1 interface using document literal encoding. The most common way to use SOAP is to download the WSDL

### Related services
- Amazon Elastic 

- Amazon EMR 

- AWS Snowball

# S3 with Amplify

AWS Amplify storage module provides a simple mechanism for managing user content for your app in public, protected or private storage buckets. The storage category comes with built-in support for Amazon S3 (Simple Storage Service).

When you run `amplify add storage`, the CLI will configure appropriate IAM policies on the bucket using a Cognito Identity Pool Role. You will have the option of adding CRUD (Create, Update, Read and Delete) based permissions as well, so that Authenticated and Guest users will be granted limited permissions within these levels

you can 
1. upload file using different ways
2. Download file using `Amplify.Storage.downloadFile`
3. You can list all of the objects uploaded under a given prefix

```
Amplify.Storage.list("/",
    result -> {
        for (StorageItem item : result.getItems()) {
            Log.i("MyAmplifyApp", "Item: " + item.getKey());
        }
    },
    error -> Log.e("MyAmplifyApp", "List failure", error)
);
```

4. To delete an object uploaded to S3, use` Amplify.Storage.remove` and specify the key


[resources1](https://docs.amplify.aws/lib/storage/getting-started/q/platform/android/) 
[resources2](https://docs.aws.amazon.com/AmazonS3/latest/userguide/Welcome.html)