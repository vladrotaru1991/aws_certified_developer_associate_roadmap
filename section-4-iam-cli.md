# Week 1: IAM & AWS CLI

Tasks and notes for IAM and CLI setup.

IAM = Identity and Access Management, GLOBAL service

Groups contain only users, not other groups

Users don't have to belong to a group, and they can also belong to multiple groups at the same time

Users or Groups can be assigned POLICIES (JSON documents with permissions)

In AWS, you should use the least privilege principle

Policies attached to a group are inherited by all users in the group.

Policies attached directly to a user are called inline policies.

IAM Policy structure:
* Version = policy language version. Is always "2012-10-17"
* Id = an identifier for the policy (optional)
* Statement = one or more individual statements (required)
  * Sid = an identifier for the statement (optional)
  * Effect = Whether the statement allows or denies access (Allow. Deny)
  * Principal = account/user/role to which this policy applies to
  * Action = list of actions this policy allows or denies
  * Resource = list of resources ti which the action applies to
  * Condition = conditions for when this policy is in effect (optional)

MFA = Multi Factor Authentication
MFA = password you know + security device you own

MFA device options:
* Virtual MFA device
  * Google Authenticator, Authy
* Universal 2nd Factor (U2F) Security Key
  * YubiKey by Yubico (can support multiple root/IAM users)
* Hardware Key Fob MFA Device

AWS access:
* AWS Management Console (protected by password + MFA)
* AWS Command Line Interface (CLI): protected by access keys
* AWS Software Developer Kit (SDK): for code: protected by access keys

Access keys are secret
Access Key ID ~= username
Secret Access Key ~= password

IAM Roles are just like users, but they are not intended to be used by people, but by AWS Services.

Roles do not have long-term credentials. They are assigned temporary credentials via STS.

IAM Credentials Report = Lists all your account's users and the status of their various credentials

IAM Access Adviser = Shows the service permissions granted to a user and when those services were last accessed. Can be used to revise policies (remove unused services access)





