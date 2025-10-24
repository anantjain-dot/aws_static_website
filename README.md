AWS S3 Static Website Sample
A simple sample and guide for hosting a static website on AWS S3. This repository includes a sample /Website directory you can deploy.

Prerequisites
An active AWS Account

Deployment Steps
Create an S3 Bucket

In the AWS S3 console, click Create bucket.

Provide a globally unique name (e.g., my-example-static-site).

Choose your desired Region.

Upload Your Website Files

Open your new bucket and upload the contents of the /Website folder (e.g., index.html, error.html, and the css/images folders) to the bucket's root.

Configure Public Access

Go to your bucket's Permissions tab.

Edit Block public access (bucket settings) and uncheck "Block all public access." Save the changes.

Go to Bucket policy and paste the following JSON, replacing [YOUR_BUCKET_NAME] with your actual bucket name:

JSON

{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::[YOUR_BUCKET_NAME]/*"
        }
    ]
}
Click Save changes.

Enable Static Website Hosting

Go to the Properties tab for your bucket.

Scroll to the bottom and edit Static website hosting.

Select Enable.

Set the Index document to index.html.

Set the Error document to error.html.

Click Save changes.

Access Your Site

Return to the Properties tab and scroll back down to the Static website hosting section.

Your website is now live at the Bucket website endpoint URL provided.
