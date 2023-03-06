Decentralized managed Authentication sign-up, sign-in for your apps. 

### Cognito User Pools
User directory with authentication to IpD to grant access to your app.

### Cognito Identity Pools
Provide temporary credentials for users to access AWS services.

### Cognito Sync
Syncs user data and preferences accross all devices.

## Web Identity Federation and IpD

### Web Identity federation
To exchange identity and security information between an identity provider (IdP) and an application.

### Identity Provider
A trusted provider of your users identity that lets you use authente to access other services.

## Types of identity providers

Security Assertion Markup Language (SAML) or Single Sign On (SSO)

OpenID Connect (OIDC) or OAuth


## Cognito User Pools
Are user directories used to manage the actions for web and mobile apps such as :
 - Sign-up
 - Sign-in 
 - Account recovery
 - Account confirmation
Allows users to sign-in directly to the users pool, or using web identity federation
Uses AWS cognito as the identity broker between AWS and identity providers.
Successful user authentication generates a JSON web token (JWTs).
User Pools can be thought of as the account used to access the system (i.e email addres and password)

## Identity Pools
Provides temporary credentials to access services eg. s3, DynamoDB 
Can be thought of as the actual mechanism authorizing access to the AWS resources.

## Cognito Sync
Syncs user data and preferences across devices with one line of code 
Cognito uses push synchronization to push updates and synchronize data. 
It uses Simple Notification Service (SNS) to send notifications to all users devices when data in the cloud changes.