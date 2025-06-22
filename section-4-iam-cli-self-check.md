# ✅ Week 1: IAM & AWS CLI – Self-Check & Practice

Use this checklist to test your recall and understanding of IAM and the AWS CLI after completing Section 4.

---

## 🧠 Concepts – Can You Explain...?

- [x] What is the difference between an IAM user and an IAM role?
  - An IAM user, as the name suggests, will be used be a real person to log into AWS Console while an IAM role is used by services to access other functionalities (to which the role gives them access).
  - IAM roles have temporary credentials assigned via STS while an IAM user uses an username and password 
- [x] What are the differences between inline and managed policies?
  - Inline policies are created by another user (with access) and added directly to another user/group, while managed policies are policies created by AWS and they can also be added directly to user/groups
- [x] What is the IAM policy evaluation logic? (Allow/Deny precedence)
  - Any Deny policy will overwrite an Allow policy. If there is no policy, it is denied by default
- [x] What is the principle of least privilege?
  - Giving a user/role as little access as needed to perform their actions.
- [x] What is a trust policy in IAM roles?
  - It can be attached to an IAM role and it specifies the entities that are allowed to assume said role. By entities I mean IAM users, IAM roles or AWS services
  - They do not define permissions
- [x] Why are roles preferred over access keys for AWS services?
  - With roles you can delegate access to AWS services and resources to other users, applications, or services without the need to share long-term access keys. Also roles allow for more fine-grained access rights
  - Access keys are long-term and harder to rotate/manage securely, whereas roles provide temporary, automatically rotated credentials.
- [x] What are resource-based policies vs identity-based policies?
  - Resource-based: Attached to a resource like an S3 bucket or Lambda function. They specify who (principal) can access the resource and what actions they can take.
  - Identity-based: Attached to users, groups, or roles. They specify what actions the identity can take on which resources.
- [x] What is the purpose of the IAM Credentials Report and Access Advisor?
  - Credentials Report: CSV report that shows each user's credentials (password status, access keys, last used, MFA, etc.)
  - Access Advisor: Shows which services a user or role has access to and when they last used them

---

## 🛠 CLI Skills – Can You Run These From Memory?

- [x] Configure the AWS CLI with a named profile
  ```bash
  aws configure --profile dev
  ```
- [x] List IAM users
  ```bash
  aws iam list-users
  ```
- [x] Attach a managed policy to a user
  ```bash
  aws iam attach-user-policy ...
  ```
- [x] View current identity using STS
  ```bash
  aws sts get-caller-identity
  ```

---

## 🔍 Practice Scenarios

- [x] Create a new user via CLI and assign a policy
- [x] Set up two CLI profiles and switch between them
- [x] Try using the CLI with incorrect credentials and observe the error
- [x] Find and download the IAM credentials report

---

## 📘 Bonus Questions

- [x] What does this IAM policy do?
```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Deny",
      "Action": "s3:*",
      "Resource": "*",
      "Condition": {
        "Bool": {
          "aws:MultiFactorAuthPresent": "false"
        }
      }
    }
  ]
}
```
- [x] How do you securely manage CLI credentials on a shared machine?

---

## 📈 Self-Scoring

| Skill | Rating (1–5) | Notes |
|-------|--------------|-------|
| IAM Users & Policies |              |       |
| IAM Roles & Trust     |              |       |
| MFA + Secure Access   |              |       |
| CLI Commands          |              |       |
| Troubleshooting IAM   |              |       |

---
