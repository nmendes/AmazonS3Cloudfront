# Amazon S3 CloudFront Module for ProcessWire 2.4+

This module/plugin provides a way to synchronize, serve and backup to Amazon S3/ CloudFront all the page assets uploaded through the Admin of ProcessWire.

## Requirements

- ProcessWire 2.4;
- Amazon AWS PHP SDK (included);
- AWS account with S3 and CloudFront services enabled;
- A S3 Bucket and a user with the proper privileges over it: "s3:PutObject", "s3:GetObject", "s3:DeleteObject" and "s3:PutObjectAcl";
- A CloudFront distribution pointing to the S3 Bucket.

## Installation 

Put all the files inside /site/modules/AmazonS3Cloudfront/ and go to Admin>Modules>Check for New Modules and install. 

You'll need to configure the module by entering your AWS Access and Secret keys and the name of the S3 Bucket you'll use to store the assets.

## How does it work

The module/plugin uploads the assets to S3 immediately as you add them to the pages in the admin of ProcessWire. It mimics the PW asset structure inside the S3 Bucket you defined. (/S3BUCKET/PAGE_ID/files).

The deleted files on PW pages are also deleted immediately from S3 but you have the option to create a backup to another folder on S3 for backup purposes.

The Module supports the use of image thumbnails created by the [Thumbnails module (FieldtypeCropImage)](http://modules.processwire.com/modules/fieldtype-crop-image/) 1.0.3 by Antti Peisa ([@apeisa](https://github.com/apeisa)) and uploads and modifies the thumbnails accordingly if this module is installed.

Note: The thumbnails natively created by the PW Admin (ex: filename_0x100.jpg) are served from the local assets folder and not uploaded to S3.

The module can automatically serve the content from Amazon CloudFront if a distribution is created for the S3 bucket used with this module. The assets URL's are automatically replaced. 

## Issues

The module will only handle new assets uploaded after the installation. If you already have assets on your pages you'll definitely have errors. 

## Notes

THIS PROCESSWIRE MODULE/ PLUGIN IS PROVIDED AS IS AND IT SHOULD ONLY BE USED FOR TEST PURPOSES. USE AT YOUR OWN RISK. THE AUTHOR IS NOT RESPONSIBLE FOR ANY DATA LOSSES OR COSTS ASSOCIATED WITH THE USE OF AMAZON AWS.

Copyright 2014 by Nelson Mendes [E-mail](mailto:nelsonmendes@gmail.com)

Built for [ProcessWire](http://processwire.com/)
