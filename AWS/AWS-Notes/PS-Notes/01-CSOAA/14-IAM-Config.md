# Configuring IAM

- After creating your AWS account at first you will log in as the `root` user
- After login go to the IAM console from the AWS Services
- Now at your first login as root you'll see the some warning alerts in the `Security Status` area  and you need to fix those.
	- Delete your root access keys
	- Activate MFA on your root account
	- Create individual IAM users
	- Use groups to assign permissions
	- Apply an IAM password policy

> NOTE: Please do not use the root account. Create an IAM users and groups as per your or the company needs. The reason to delete the access keys of the root account is to avoid hacker attacks.

- Click on each of the security alerts and do it. On completing the task that alert will turn to green from warning
- Configure MFA for your root account
- On the left pane click on `Users`
	- Click on create user
	- Provide the user(s) name(s)
	- Check / Uncheck to create the access keys
	- Click on create
- If you want to apply permissions for individual users then click on `Users` in the left pane
	- Click on the username you want to apply permissions on
	- Click on `Attach Policy`
	- Select the required permission from the list of permissions/policies
	- Click on `Select`

	> NOTE: For an admin user please select `AdministratorAccess` policy
	
	> NOTE: Until you configure the password policy you can give either of the password which is not advisable. Please configure your password policy before changing the passwords of the users

- On the left pane click on `Groups`
	- Click on `Create New Group`
	- Give it a name
	- Click on `Next Step`
	- Select policy(s) for this group

	> NOTE: For an admin user please select `AdministratorAccess` policy

	- Click on `Next Step`
	- Review and create the group

---

# Roles

- This can be useful to deal with the applications. Some times we need to have some specific privillages on accessing some applications
- In such cases we can use the roles.
- Roles are just like the special users we create in our OS environments to manage through. For managing the applications we need to switch to that user.
- In the same way we can create a role in AWS IAM to which we need to switch and through that we can manage the applications
- Creating a `Role`
	- Click on `Create New Role`
	- Give it a name and click on `Next Step`. In my case `EC2Apps`
	- Select Role Type. I am selecting `Amazon EC2`
	- Attach policy. In my case `AdministratorAccess`
	- Review and create

---

# Policies

- Policy is a list of permissions
- Creating a policy
	- Go to policies in the left pane of the AWS IAM Console
	- Click on `Create Policy`
	- Select either of the way you need it
		- Copy an AWS Managed Policy
		- Policy Generator
		- Create Your Own Policy
	- Review and create
