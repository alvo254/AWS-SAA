Manages acccess of AWS users and resources.

## I am Core Components 

- IAM Users - End user who logs into the console or interacts with AWS resources programmatically 
- IAM Groups - Group up your users so they all share permission level of the groups eg Administration, Developers, Auditors
- IAM roles - Associate permissions to a role and then assign this to a user or group

IAM policies JSON document which grants permissions for a specific user, group, or role to access services. Policies are attached to IAM Identities.

A user cna belong to a group. Roles can be applied to groups to quickly remove and add permissions

A user can have a role directly attached, a policy can be directly attached to a user (called inline policy)

Roles can have many policies attached.
Variours AWS resources allow you to attach roles directly to them.

## Types of policies

### Managed policies
A policy which is managed by AWS which you cannot edit. Manages policies are labeled with an orange box

### Custom Managed Policies
A policy created by customer which is editable. Customer policies have no symbol besides them.

### Inline Policies
A policy which is directly attached to the user.

## Password policiy
In IAM you can set password policy to set the minimum requirements of a password and rotate passwords so users have to update their password after X days.

## Access Keys
Allows user to interact with AWS services programmatically via the AWS cli or sdk

## MFA
MFA can be turned on per user
The user has to turn on MFA admin cannot directly enforce users to have MFA
The admin could create policy requiring MFA to access certain resources.
