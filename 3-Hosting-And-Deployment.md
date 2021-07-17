# Hosting on AWS

AWS makes it really easy and cheap to set up and host the front-end within a CI/CD environment.

The code base is stored as normal within the AWS CodeCommit secure repo with the following branch structure:

- Master: Production
- Staging: Pre-Production live testing
- Development: Core dev branch with the latest code
- Feature branches
- Hot fix branches

Both Staging and Master branches are hosted within AWS S3 buckets. AWS CloudFront CND is used for fast delivery of the app to users.

AWS Amplify is the CLI/console used to manage the hosting and deployment. Each merge into either the Staging or Master branch triggers the automatic re-build and re-deployment of the front-end. This is done as a hot deploy so there is never any down time of live applications. AWS Amplify provides a powerful CLI as well as the console to easily view and monitor applications.

# Prerequisites

# Build and Deploy

The first time a new product is deployed to AWS:

Once complete we can build the app which creates a `dist` folder that is to be deployed to AWS.

1. Build: ``
