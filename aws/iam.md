IAM users and IAM groups.  
You can access services using cli, sdk, web console.  
Users and groups are provisioned by admin with permision policies (IAM Policies) in form of JSON file. By default IAM users can't access anything.Users in group inherit group's permissions. Eg. you have 3 departments, then you create 3 IAM groups and then IAM user per user.  

By default you have only root. Recomended to create IAM user with administrative policies and not use root.  

IAM Role. Uses IAM policies for permissios. Does not have any long term defined credentials, passwords, access keys. Instead if user is assigned to a role access keys are created dynamicaly and provided to user temporalily. IAM roles can be used to delegate access to users, applications or services that don't normally have access to your aws resources. User who assumes role permissions gives up their permission and instead takes permissions of the role.  
Policy is created -> role is created, policy is attached to a role -> user is allowed to assume role -> when user isdone with activity, role is revoked and user has previous policies