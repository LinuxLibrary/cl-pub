# IAM Users and Policies

- I need a user to access a bucket in S3
	- Check whether we have the user, if not create a user
	- Attach "AmazonS3FullAccess" policy for this user

> Now if we need some more users to have access to S3 we can do it the same way.
> By default no user will have access to any components in AWS
> Through attaching the IAM policies we can let them to access those
> In this way we can restrict or assign privillages to someone just to read or to have full access to S3
