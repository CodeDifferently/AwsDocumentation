# HOSTING WITH S3
---

### Prequisites

* AWS Account
* Domain name and DNS access

### Steps

* Sign into your AWS console and go to S3 service at `https://console.aws.amazon.com/s3/`. 
* Create two S3 buckets 
	* `www.example.com` and `example.com`
	* When creating a bucket keep all settings default except blocking all public access, *turn that off*
* Upload you website to your `www.example.com` bucket.
* In the same bucket go to **Permissions** then choose **Bucket Policy**
* Copy and paste the following bucket policy, *replace version date with the current date and example.com with the bucket name*

```json
{
   "Version":"2012-10-17",
   "Statement":[
      {
         "Sid":"PublicReadGetObject",
         "Effect":"Allow",
         "Principal":"*",
         "Action":[
            "s3:GetObject"
         ],
         "Resource":[
            "arn:aws:s3:::example.com/*"
         ]
      }
   ]
}

```
* Press Save and BOOM now have public read access so people can view your bucket

Next after applying policy

1. Go to **Properties**
2. Choose **Static Website Hosting**
3. Choose first option *Use this bucket to host a website* 
4. In the **Index Document** box, type the name that you gave your index page then click save.
5. Next go to your other bucket `example.com` and go to **Properties** and **Static Website Hosting** and choose the *Redirect requests* option