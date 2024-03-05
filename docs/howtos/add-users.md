(add-users)=
# Add Users

This is a quick guide on how to add users to organizations and how to manage
their privileges. This information can also be found in the CrateDB Cloud  
Console {ref}`Overview <console-overview>`, but is presented here separately 
for ease of use.

In CrateDB Cloud, you can add team members to your organizations. In order to 
add a user, they must first have signed up for CrateDB Cloud. Once they have 
an existing account, they can be added as a user. Users can be members or 
admins of more than one organization at a time, but every organization must 
have at least one organization admin (see also Restrictions below).

(add-users-to-org)=
## Add Users to an Organization

New users can be added to an organization by going to the Users tab in the 
left-hand menu. To add and manage users of the organization, you must be the 
organization admin.

````{note}
For more information on user roles and associated privileges, see the 
documentation on {ref}`user roles <user-roles>`.
````

![Cloud Console users overview](../_assets/img/users-overview.png)

On this page, you can see an overview of all users associated with the 
organization. It will show their username, email, user role, and their status.

To add a new user click the *Add user* button in the top right. Then you can 
add a new user either by their email or their user ID. You can also choose 
whether the user should have admin privileges.

![Cloud Console organization overview users tab](../_assets/img/add-user.png)

(add-users-edit)=
## Edit or Delete Users from an Organization

You can also edit user roles and delete users in the *Users* tab. 
To edit a user's role, navigate to its details page using the pen icon corresponding to 
that user in the user table. This will bring up a dropdown menu. 
To delete a user, use the bin icon.

(restrictions)=
## Restrictions

An organization needs to have at least one organization admin. It is therefore 
not possible to remove the organization admin if there is only one.
