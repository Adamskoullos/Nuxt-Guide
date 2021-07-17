# Hosting on AWS

AWS makes it really easy and cheap to set up and host the front-end within a CI environment.

The code base is stored as normal within the AWS CodeCommit secure repo with the following branch structure:

- Master: Production
- Staging: Pre-Production live testing
- Development: Core dev branch with the latest code
- Feature branches
- Hot fix branches

Both Staging and Master branches are hosted within AWS S3 buckets. AWS CloudFront CND is used for fast delivery of the app to users.

AWS Amplify is the console used to manage the hosting and creates a static site environment where every merge into either the Staging or Master branch triggers the automatic re-build and re-deployment of the front-end. This is done as a hot deploy so there is never any down time of live applications.

# Build and Deploy
