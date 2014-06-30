# Amazon S3 CloudFront Module for ProcessWire 2.4+

This module/plugin provides a way to synchronize, serve and backup to Amazon S3/ CloudFront all the page files uploaded through the Admin of ProcessWire.

## Requirements

- ProcessWire 2.4;
- Amazon AWS PHP SDK (included);
- AWS account with S3 and CloudFront services enabled;
- A S3 Bucket and a user with the proper privileges over it: "s3:PutObject", "s3:GetObject", "s3:DeleteObject" and "s3:PutObjectAcl";
- A CloudFront distribution pointing to the S3 Bucket.

## Installation 

Put all the files inside /site/modules/AmazonS3Cloudfront/ and go to Admin>Modules>Check for New Modules and install. 

You'll need to configure the module by entering your AWS Access and Secret keys and the name of the S3 Bucket you'll use to store the files. I've set up a [video](http://youtu.be/Hpj7AA0Rz14) and a [user policy document](https://gist.github.com/nmendes/9053e1c3347dec7741d8) to help you out if you don't know how to do this.

## How does it work

The module/plugin uploads the files to S3 immediately as you add them to the pages in the admin of ProcessWire. It mimics the PW asset structure inside the S3 Bucket you defined. (/S3BUCKET/PAGE_ID/files).

The deleted files on PW pages are also deleted immediately from S3 but you have the option to create a backup to another folder on S3 for backup purposes.

The Module supports the use of image thumbnails created by the [Thumbnails module (FieldtypeCropImage)](http://modules.processwire.com/modules/fieldtype-crop-image/) 1.0.3 by Antti Peisa ([@apeisa](https://github.com/apeisa)) and uploads and modifies the thumbnails accordingly if this module is installed.

Note: The thumbnails natively created by the PW Admin (ex: filename_0x100.jpg) are served from the local assets folder and not uploaded to S3.

The module can automatically serve the content from Amazon CloudFront if a distribution is created for the S3 bucket used with this module. The files URL's are automatically replaced. 

You can set a number of seconds to set the Cache-Control Directive and handle the cache time for both the browser and CloudFront. See more information [here](http://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Expiration.html).

There's an option for file versioning to use with CloudFront that automatically renames all the files uploaded by adding a timestamp like: yourfilename-v1403782033.jpg. This will make every filename unique so it's easier to manage the caching of files. I recommend that you use this option or it can become very hard to replace files already cached by Amazon.

## Issues

This version of the module will only handle new files uploaded after the installation. If you already have files on your pages they will not be uploaded to S3 and you can get errors because the files inside PW will not match the files on S3.

If you use the native size() method of ProcessWire (ex: $image->size(232, 176))to create image thumbnails, they will not be uploaded to S3 automatically. This issue should be solved soon as the dev branch of PW already has this method hookable. 

## Notes

THIS PROCESSWIRE MODULE/ PLUGIN IS PROVIDED AS IS AND IT SHOULD ONLY BE USED FOR TEST PURPOSES. USE AT YOUR OWN RISK. THE AUTHOR IS NOT RESPONSIBLE FOR ANY DATA LOSSES OR COSTS ASSOCIATED WITH THE USE OF AMAZON AWS.

Copyright 2014 by Nelson Mendes [E-mail](mailto:nelsonmendes@gmail.com)

Built for [ProcessWire](http://processwire.com/)