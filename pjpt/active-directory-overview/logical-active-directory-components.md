# Logical Active Directory Components

The AD DS Schema:

Defines every type of object that can be stored in the directory

Enforces rules regarding object creation and configuration





<table><thead><tr><th>Object Types</th><th width="247">Function</th><th>Examples</th></tr></thead><tbody><tr><td>Class Object</td><td>What objects can be created in the directory</td><td><ul><li>User</li><li>Computer</li></ul></td></tr><tr><td>Attribute Object</td><td>Information that can be attached to an object</td><td><ul><li>Display name</li></ul></td></tr></tbody></table>



Domains: Domains are used to group and manage objects in an organization

An administrative boundary for applying policies to groups of objects

A replication boundary for replicating data between domain controllers

An authentication and authorization boundary that provides a way to limit the scope of access to resources



Tree: A domain tree is a hierarchy of a domain in AD DS



All domains in the tree:

share a contiguous namespace with the parent domain

can have additional child domains

by default create a two-way transitive trust with other domains



forests: a forest is a collection of one or domain trees

forests:

shares a common schema

share a common configuration partition

shares a common global catalog to enable searching

enable trusts between all domains in the forest

share the enterprise admins and schema admins group



Organizational Units (OUs): are active directory containers that can contain users, groups, computers, and other OUs

OUs are used to:&#x20;

Represent your organization hierarchically and logically

Manage a collection of objects in a consistent way

delegate permissions to administer groups of objects

apply policies



Trusts



| Types of Trusts | Description                                                                                   | Diagram                                                                     |
| --------------- | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| Directional     | The trust direction flows from trusting domain to the trusted domain                          | <img src="../../.gitbook/assets/image (3).png" alt="" data-size="original"> |
| Transitive      | The trust relationship is extended beyond a two-domain trust to include other trusted domains | <img src="../../.gitbook/assets/image (4).png" alt="" data-size="original"> |

All domains in a forest trust all other domains in the forest

trusts can extend outside the forests





Objects





| Object         | Description                                                                                         |
| -------------- | --------------------------------------------------------------------------------------------------- |
| User           | Enables network resources for a user                                                                |
| InetOrgPerson  | <p>similar to a user account<br>used for compatibility with other directory services</p>            |
| Contacts       | <p>Use primarily to assign e-mail addresses to external users<br>Does not enable network access</p> |
| Groups         | Used to simplify the administration of access control                                               |
| Computers      | Enables authentication an auditing of computer access to resources                                  |
| Printers       | Used to simplify the process of locating and connecting to printers                                 |
| Shared Folders | Enables users to search for shared folders based on properties                                      |

