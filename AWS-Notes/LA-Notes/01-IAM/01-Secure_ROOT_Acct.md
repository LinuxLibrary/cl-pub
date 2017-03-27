Most important and major concern in hosting a public cloud is we need to secure our ROOT account.
This account is similar to the root account in our Linux machines which has the high level privs.

Below are the steps to secure a root account.
From the IAM console you need to generate your unique login url.
After that you need to do the following steps:

1. Delete your root access keys
   (By default access keys are being deleted these days)
2. Activate MFA on your root account
3. Create individual IAM users
	- Create a user account without any access keys (we can create the access keys later on as needed)
	- Attach "AdministratorAccess" policy to this user
	- Set the password
4. Use groups to assign permissions
	- Create a group named admin
	- Attach "AdministratorAccess" policy to this group
5. Apply an IAM password policy
	- Choose the number of characters
	- Choose some other options you need
	- Choose password expiration details (if needed)
	- Choose password reuse policy (if needed)
