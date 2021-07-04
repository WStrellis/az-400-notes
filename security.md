# Azure AD

Azure AD can be used in conjuction with on-prem AD.
- *Password Hash Synchronization* - user's password is hashed 2x and shared between on-prem AD and Azure AD. Exposes user's password to cloud.
- *Pass-Through Authentication* - an Azure AD agent is installed on an on-prem server. When an Azure AD user tries to authenticate it is handled by the on-prem server.
- *Federated Authentication*  - Authentication is handled by on-prem AD Federation Service. Supports smart cards.

Produces two types of logs:
- *Sign-in* - information about sign-in activity
- *Audit* - a record of what users did

### Features
- *Azure AD B2B* - allows you to invite external users to your tenant, such as contractors
- *Azure AD Application Proxy* - add on-prem apps to Azure AD tenant
- *Azure AD B2C* - manage customer identities and access. Use with 3rd party auth systems ( google, facebook, apple).
- *Azure AD Domain Service* - add Azure VMs to a company domain without using domain controllers.
- *Azure AD Identity Protection* - automated risk detection and remediation. Admin first configures policies.

When a user account is deleted it remains in the AD Tenant in a suspended state for 30 days. During that window the account can be restored.


Ways to Assign Access Rights:
- Create a Role and assign the Role to a user
- Create a Group and add a user to the group
- Rule-Base : determine group membership by evaluating user or device properties

Group types
- *Security* - limit access to apps, resources, licenses, etc on azure
- *Microsoft 365* - limit access to shared files, folders, calendars, etc on MS 365 apps

### Azure AD B2B
- by default, both users and admins can invite users outside of the tenant to become guest users.
- when a guest user is invited to the network they use their own business credentials or personal email credentials to authenticate.

## Managed Identities
used to authenticate apps with other azure resources
- Only work with AZ resources
- free
- supports RBAC 
- automatically manages credentials and certificates

- *Client ID* - unique ID linked to AZ AD app and service principal
- *Object ID* - service principal of the managed identity
- *Azure Instance Metadata Service* - REST API that is enabled when ARM provisions a VM. Only accessible within VM.

Two types of Managed Identities:
- *System Assigned* - enabled directly on a single VM. Cannot be used on other VMs.
- *User Assigned* - User creates the managed identity. Can be assigned to multiple vms. Better when vms are duplicated.

A unique identy is created in the service principal. When the VM needs to authenticate to another resource it requests a token from AZ AD using the Instance Metdata Service. When it gets a token it sends the token to the resource it want to connect with. The other resource sends the token to AZ AD for verification. Then the two services can communicate.  

Create a managed identity exercise: [https://docs.microsoft.com/en-us/learn/modules/authenticate-apps-with-managed-identities/5-exercise-configure-managed-identity-for-vm](https://docs.microsoft.com/en-us/learn/modules/authenticate-apps-with-managed-identities/5-exercise-configure-managed-identity-for-vm)

## API Manager
A service which as a reverse proxy for custom apis.
- accepts api requests and sends to approriate backend server
- verifies api keys, JWT tokens, certs, and other credentials
- enforces usage quotas and limits
- can cache responses

*Subscription Keys*  
Limit access to an api.  
Three Scope Levels:
- *All* - allows access to all apis from the gateway
- *Single* - allows access to a specific endpoint on the gateway
- *Product* - a collection of APIs on the gateway

# Azure Security Center
- configure Just-in-time ssh/rdp access
- monitor security settings in cloud and on-prem
- automatically apply security settings to new resources
- identifies potential vulnerabilites
- detects and blocks malware from being installed on VMs

# Azure Sentinel
- collects data from cloud( only cloud)
- detects threats by analyzing data
- tools to investigate incidents
- tools to respond to incidents
- send alerts 
- utilizes Azure Monitor Workbooks to automate responses to threats

# Azure Blueprints
Templates which allow Cloud Managers to created reuseable templates for deploying policies across multiple subscriptions and resource groups. They combine ARM Templates, RBAC, and policies into a single template.
