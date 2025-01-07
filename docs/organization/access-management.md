# Access Management

CrateDB Cloud manages user access at two levels: through the Cloud Console and
directly within the database. Cloud Console access is handled via the CrateDB
Cloud user interface, where users are granted access to manage and monitor their
deployments. Database access is controlled using database-specific user accounts
and roles.

## Authentication Options

CrateDB Cloud offers multiple authentication methods. This guide outlines best
practices for configuring authentication securely. Always consult your security
team before choosing an authentication method.

### Email + Password
CrateDB Cloud supports authentication via email and password. To ensure the
security of your account, follow these best practices:

- Use a strong, unique password. Online resources can help you create memorable
  yet secure passwords.
- Alternatively, generate a random password using a password manager for
  enhanced security and easy storage.

### SSO with Google, Microsoft, or GitHub Social
CrateDB Cloud supports single sign-on (SSO) via Google, Microsoft, or GitHub.
Here's how to get started:
1. Sign up for CrateDB Cloud using your company Google, Microsoft or GitHub account.
2. Invite other users using their company email addressess.

For organizations using Google or Microsoft SSO, this setup ensures users
authenticate through the organization's login process — either via your identity
provider or directly through Google or Microsoft authentication — before accessing
CrateDB Cloud.

:::{note}
When signing in with an external authentication provider for the first time, a 
CrateDB Cloud user account will be automatically generated for you.
:::

:::{note}
When using Google, Microsoft, or GitHub for authentication in CrateDB Cloud,
admin permissions might be required to configure and allow access, depending
on your organization's settings. 

For **Microsoft**, admins may need to:  
- Grant tenant-wide consent for the permissions requested by CrateDB Cloud
  (`openid`, `profile`, `email`, and `offline_access`).  
- Allowlist the CrateDB Cloud application if app registrations or third-party
  integrations are restricted.

For **Google**, admins might need to:  
- Authorize the CrateDB Cloud application in the Google Admin Console under
  "Apps > App Management".
- Enable external applications if they are restricted within your organization.

For **GitHub**, admins may need to:  
- Approve the CrateDB Cloud application in the GitHub organization settings
  under "Third-party access".

Consult your admin team to ensure proper setup for CrateDB Cloud authentication.
:::

### Limitations
- Currently, each authentication method creates a separate CrateDB Cloud account.
  It is not possible to switch between authentication methods for the same
  account at this time.
- Authentication using Google, Microsoft, or GitHub relies is implemented via
  OpenID Connect (OIDC) but does not support full SAML-based integration.


---

## User Roles and Privileges

This section provides details on user roles and privileges in CrateDB Cloud,
covering both organization roles for Cloud users and database-specific roles.

### CrateDB Cloud Organization Roles

In CrateDB Cloud, users are assigned **organization roles** to manage access to
Cloud resources. 

- **Organization Admin**:
  - Can add, edit, or remove users within the organization.
  - Can perform all available operations on clusters and services.
  - Can manage billing and subscription details.
  - Must always exist; at least one admin is required per organization.

- **Organization Member**:  
  - Grants no permissions and only indicates membership in the organization.  
  - Cannot add, edit, or remove resources or perform administrative tasks.  
  - Primarily used to invite new users to the organization.


### Database Users and Roles

CrateDB Cloud automatically creates several system and administrative accounts
during cluster setup. These accounts serve specific purposes and should not be
modified or deleted to ensure proper cluster functionality.

- **`admin`**  
  - **Purpose**: Created when deploying a new cluster, this user is intended 
    for CrateDB Cloud users to manage the database.  
  - **Permissions**: Full privileges, allowing execution of all database
    operations.  
  - **Usage**:  
    - The password for the `admin` user is displayed after the initial cluster
      deployment.  
    - The password can be changed later through the **Cluster Management** page
      in the Cloud Console.  
    - The `admin` user is also the default account used by the **Cloud SQL
      Console**.

- **`system`**  
  - **Purpose**: Manages backend operations such as cluster upgrades, backups, and scaling.  
  - **Permissions**: Full admin privileges, allowing execution of all database operations.  

  :::{note}
  The `system` user is essential for CrateDB Cloud to operate correctly. Editing
  or deleting this user could result in system malfunctions and compromise
  cluster functionality.
  :::

- **`gc_admin`**  
  - **Purpose**: Handles automations, such as scheduled jobs and table policy
    management.  
  - **Permissions**: Full admin privileges, allowing execution of all database
    operations.  

  :::{note}
  The `gc_admin` user is crucial for maintaining cluster automation processes.
  Editing or deleting this user could disrupt scheduled jobs, table policies,
  and other automated workflows.
  :::

- **`crate`**  
  - **Purpose**: Acts as the default superuser for the cluster.  
  - **Permissions**: Full privileges, allowing execution of all database
    operations.  
  - **Restrictions**:  
    - Authentication is limited to `localhost` for security.  
    - Additional superusers cannot be created. 

---

For more details on CrateDB user management and privileges, refer to the
CrateDB documentation on {ref}`user management <crate-reference:administration_user_management>`
and {ref}`privileges. <crate-reference:administration-privileges>`

