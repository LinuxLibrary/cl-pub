# Amazon Security Token Service (STS)

- The AWS Security Token Service (STS) is a web service that enables you to request temporary, limited-privilege credentials for AWS Identity and Access Management (IAM) users or for users that you authenticate (federated users).
- You can use the AWS Security Token Service (AWS STS) to create and provide trusted users with temporary security credentials that can control access to your AWS resources. 
- Temporary security credentials work almost identically to the long-term access key credentials that your IAM users can use, with the following differences:
	- Temporary security credentials are short-term, as the name implies.
	- They can be configured to last for anywhere from a few minutes to several hours.
	- After the credentials expire, AWS no longer recognizes them or allows any kind of access from API requests made with them.
	- Temporary security credentials are not stored with the user but are generated dynamically and provided to the user when requested.
	- When (or even before) the temporary security credentials expire, the user can request new credentials, as long as the user requesting them still has permissions to do so.
- Advantages of temporary credentials and STS:
	- You do not have to distribute or embed long-term AWS security credentials with an application.
	- You can provide access to your AWS resources to users without having to define an AWS identity for them.
	- Temporary credentials are the basis for roles and identity federation.
	- The temporary security credentials have a limited lifetime, so you do not have to rotate them or explicitly revoke them when they're no longer needed.
	- After temporary security credentials expire, they cannot be reused.
	- You can specify how long the credentials are valid, up to a maximum limit.

---

- Temporary credentials are useful in scenarios that involve identity federation, delegation, cross-account access, and IAM roles.

- ***Identity Federation:***

- You can manage your user identities in an external system outside of AWS and grant users who sign in from those systems access to perform AWS tasks and access your AWS resources.
- IAM supports two types of identity federation.
- In both cases, the identities are stored outside of AWS.
- The distinction is where the external system resides—in your data center or an external third party on the web.
	- ***Enterprise identity federation*** – You can authenticate users in your organization's network, and then provide those users access to AWS without creating new AWS identities for them and requiring them to sign in with a separate user name and password. This is known as the single sign-on (SSO) approach to temporary access. AWS STS supports open standards like Security Assertion Markup Language (SAML) 2.0, with which you can use Microsoft AD FS to leverage your Microsoft Active Directory. You can also use SAML 2.0 to manage your own solution for federating user identities.
		- ***Custom federation broker*** – You can use your organization's authentication system to grant access to AWS resources.
		- ***Federation using SAML 2.0*** – You can use your organization's authentication system and SAML to grant access to AWS resources.
	- ***Web identity federation*** – You can let users sign in using a well-known third party identity provider such as Login with Amazon, Facebook, Google, or any OpenID Connect (OIDC) 2.0 compatible provider. You can exchange the credentials from that provider for temporary permissions to use resources in your AWS account.
