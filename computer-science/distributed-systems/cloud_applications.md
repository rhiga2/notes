Cloud Applications
==================
# Introduction
## Why cloud?
* Scalablity and elasticity: meets demand
* Locality: able to service customers in regions using data centers in close proximity
* Reliability: multi-zone data centers prevent outages in many cases
* Ease: do not need to physically manage servers
## Different abstractions of cloud computing:
* Infra as a Service (IAAS): rent virtual compute and storage resources.
  * You have to manage OS and middleware   
* Platform as a Service (PAAS): managed envs provided by many providers
  * You only have to manage application and data, but you have less control over env.   
* Software as a Service (SAAS): IAAS and PAAS are solutions for application developers. SAAS pertrains to end users.
   * Software that does not need to be installed or updated on local computer. Works in browser   
## Common Cloud Service Offerings
* Access Management
* Compute
* Storage
* Networking
* Databases
* Monitoring

# Access Management
## Terminology
* Shared Responsibility Model: 
* Principal:
* Principle of Least Privilege: Give minimal access to principal to do their job and nothing more. 
* Authentication: Who are you?
  * Ways to authenticate:
    * Log in with username and password
    * API access keys
    * Federation: identity is verfied by a third-party
* Authorization: What can you do?

## Identity and Access Management
* Organization
* Account
* Identities
  * Users: person or app with long-term credendtials. Not recommended for apps or code to have long-tern creds
  * User groups: multiple users that share a set of permissions. Users can belong to multiple user groups
  * Roles:
* Policies: Permissions given to a user or resource
  * Identity-based: permissions (allowed and denied actions) attacked to users, user groups, or roles.
  * Resource-based: permissions attached to resources (i.e. make S3 bucket publicly accessible)
  * 

# Networking
## IP Addresses and CIDR
## Virtual Private Clouds and Subnets
