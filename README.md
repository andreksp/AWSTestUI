# AWSTestUI

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 13.1.2.

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
