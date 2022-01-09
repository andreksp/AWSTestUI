# AWSTestUI

1) Deploy the application directly on S3 Bucket
2) Set permission on S3 bucket for public access
3) buildspec.yml will cleanup the bucket before the deploy
4) AWS Pipeline will update the bucket after build
5) Enable S3 bucket for host a web site.

## Development server

Run `ng serve`
Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.
Run `ng e2e` to execute the end-to-end tests via a platform of your choice. To use this command, you need to first add a package that implements end-to-end testing capabilities.

## Allow PipeLine to change S3 Bucket

'''
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowDeleteFromPipeline",
            "Effect": "Allow",
            "Principal": {
                "AWS": "*"
            },
            "Action": "s3:*",
            "Resource": "arn:aws:s3:::aws-test-ui-bucket/*"
        }
    ]
}
'''
