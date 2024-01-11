---
title: "Day 67: AWS S3 Bucket Creation and Management"
datePublished: Thu Jan 11 2024 14:19:04 GMT+0000 (Coordinated Universal Time)
cuid: clr9apddp000109l76dn03uar
slug: day-67-aws-s3-bucket-creation-and-management
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1704982164651/06a04428-0dfc-448d-92e2-a61a66351a9b.jpeg

---

## AWS S3 Bucket

Amazon S3 (Simple Storage Service) is an object storage service that offers industry-leading scalability, data availability, security, and performance. It can be used for a variety of use cases, such as storing and retrieving data, hosting static websites, and more.

In this task, you will learn how to create and manage S3 buckets in AWS.

## Task

* Create an S3 bucket using Terraform.
    

```plaintext
resource "aws_s3_bucket" "my_bucket" { 
bucket = "<unique_bucket_name>" 
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703244745025/94781abe-4531-44a2-a058-ae59fcde3383.png?auto=compress,format&format=webp align="left")

The declaration of aws\_s3\_bucket resource results in the creation of a new S3 bucket. The identifier "my\_bucket" uniquely represents this resource within your Terraform code and can be customized to suit your preference. Initialize the working directory and download necessary providers by executing the terraform init command.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703244747901/c4f01fba-3bf7-4d14-bc04-63734c2727aa.png?auto=compress,format&format=webp align="left")

Generate an execution plan with terraform plan to analyze the changes required for achieving the desired infrastructure state.

Apply the changes using terraform apply to create or update resources as necessary.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703244750340/e7cb302a-8ad9-483c-97de-a667f1feae40.png?auto=compress,format&format=webp align="left")

The S3 bucket has been successfully created.

### **2\. Configure the bucket to allow public read access.**

Step-01: Begin by creating a new file named "public\_[**access.tf**](https://pmgoriya.hashnode.dev/aws-s3-bucket-creation-and-management-using-terraform#heading-2-configure-the-bucket-to-allow-public-read-access)" and insert the following Terraform code:

```plaintext
resource "aws_s3_bucket_public_access_block" "example" {
  bucket = aws_s3_bucket.devops_name_bucket_1.id

  block_public_acls       = false
  block_public_policy     = false
  ignore_public_acls      = false
  restrict_public_buckets = false
}

resource "aws_s3_bucket_acl" "bucket_acl" {
  bucket = aws_s3_bucket.devops_name_bucket_1.id
  acl    = "public-read"
}
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703244068553/f50b5371-f1f9-4f48-a7d1-da2c9a8b2d6a.png?auto=compress,format&format=webp align="left")

In this Terraform configuration:

* The `aws_s3_bucket_public_access_block` resource configures the control of public access to the "devops\_name\_bucket\_1" S3 bucket. It explicitly allows public ACLs, public policies, and public bucket access.
    
* The `aws_s3_bucket_acl` resource defines an Access Control List (ACL) for the "devops\_name\_bucket\_1" S3 bucket, setting it to "public-read." This setup grants public read access to objects within the bucket.
    

Step-02: Proceed to the AWS S3 bucket, navigate to Permissions, and enable ACLs by editing object permissions.

<mark>Note</mark>\- This is done so that we do not get access denied error.

Step-03: Apply the Terraform code using the command:

```plaintext
terraform apply
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703244053975/fa62507b-b46b-41e4-a860-266f66b98ab9.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703244057011/749d2232-f99a-44ca-b13f-33b60eea2a05.png?auto=compress,format&format=webp align="left")

Step-04: Check the AWS Console to verify that the S3 bucket is now public as intended

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1704982675632/17803634-dfc4-4347-9ecd-4fc90386b010.png align="center")

### **3\. Enable versioning on the S3 bucket.**

The versioning configuration is specified, with the "enabled" attribute set to true. This activates versioning for the S3 bucket, ensuring that multiple versions of each object stored in the bucket are retained.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703246408687/7271ca9c-dc11-406e-8f6e-cd250614c9d8.png?auto=compress,format&format=webp align="left")

Versioning for the bucket has been successfully enabled.

### **4\. Create an S3 bucket policy that allows read-only access to a specific IAM user.**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703247702034/7034d471-2497-4b9e-9b08-aa2bfc22239b.png?auto=compress,format&format=webp align="left")

```plaintext
resource "aws_s3_bucket_policy" "bucket_policy" {
  bucket = aws_s3_bucket.my_bucket.id
  policy = data.aws_iam_policy_document.allow_read_only_access.json
}

data "aws_iam_policy_document" "allow_read_only_access" {
  statement {
    principals {
      type        = "AWS"
      identifiers = ["683633011377"]
    }

    actions = [
      "s3:GetObject",
      "s3:ListBucket",
    ]

    resources = [
      aws_s3_bucket.my_bucket.arn,
      "${aws_s3_bucket.my_bucket.arn}/*",
    ]
  }
}
```

To grant read-only access to a designated IAM user or role, the configuration establishes an S3 bucket policy through the "aws\_s3\_bucket\_policy" resource. This policy is linked to the S3 bucket resource "aws\_s3\_[**bucket.my**](https://pmgoriya.hashnode.dev/aws-s3-bucket-creation-and-management-using-terraform#heading-2-configure-the-bucket-to-allow-public-read-access)\_bucket" using the "bucket" parameter, while the "policy" parameter references the Terraform data source "[**data.aws**](https://pmgoriya.hashnode.dev/aws-s3-bucket-creation-and-management-using-terraform#heading-2-configure-the-bucket-to-allow-public-read-access)\_iam\_policy\_document.allow\_read\_only\_access.json," defining the policy document.

The policy document creation involves the "data" block, constituting a Terraform data source. Within "[**data.aws**](https://pmgoriya.hashnode.dev/aws-s3-bucket-creation-and-management-using-terraform#heading-2-configure-the-bucket-to-allow-public-read-access)\_iam\_policy\_document.allow\_read\_only\_access," the policy document outlines permissions in JSON syntax, allowing read-only access to the specified S3 bucket for a designated IAM user or role.

This policy document features a single "statement" block, detailing the permissions granted. Specifically, it permits "s3:GetObject" and "s3:ListBucket" actions for the designated bucket and its objects. The "principals" block identifies the AWS user or role, with the "identifiers" field specifying the AWS account ID of the recipient of read-only access.

Execute `terraform apply` to implement the configuration.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703247683495/2a132ca1-03c1-453e-b322-6c3bde53e54a.png?auto=compress,format&format=webp align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703247694644/01a2c255-35a6-4310-a160-b023dca4da4c.png?auto=compress,format&format=webp align="left")

A tailored S3 bucket policy has been established, granting read-only access to the specified IAM user. Check in Permissions panel &gt; Bucket Policy

These practical steps provide a solid foundation for understanding and managing AWS S3 buckets, ensuring that you can effectively handle your cloud-based data storage needs while maintaining security and accessibility.

Keep exploring the vast world of AWS services and stay curious about the ever-evolving technology landscape.