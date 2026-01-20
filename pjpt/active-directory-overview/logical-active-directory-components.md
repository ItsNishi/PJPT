# Logical Active Directory Components

## AD DS Schema

Defines every type of object that can be stored in the directory and enforces rules for object creation/configuration.

| Object Type | Function | Examples |
|-------------|----------|----------|
| Class Object | What objects can be created | User, Computer |
| Attribute Object | Info attached to objects | Display name |

## Domains

Used to group and manage objects in an organization.

- Administrative boundary for applying policies
- Replication boundary between domain controllers
- Authentication/authorization boundary for resource access

## Trees

A hierarchy of domains in AD DS.

All domains in a tree:
- Share a contiguous namespace with parent domain
- Can have additional child domains
- Create two-way transitive trust with other domains by default

## Forests

A collection of one or more domain trees.

Forests share:
- Common schema
- Common configuration partition
- Common global catalog for searching
- Trusts between all domains
- Enterprise Admins and Schema Admins groups

## Organizational Units (OUs)

Containers that can hold users, groups, computers, and other OUs.

Used to:
- Represent organization hierarchy
- Manage collections of objects consistently
- Delegate administrative permissions
- Apply Group Policy

## Trusts

| Type | Description |
|------|-------------|
| Directional | Trust flows from trusting domain to trusted domain |
| Transitive | Trust extends beyond two domains to include other trusted domains |

- All domains in a forest trust all other domains in that forest
- Trusts can extend outside the forest

## Objects

| Object | Description |
|--------|-------------|
| User | Enables network resource access for a user |
| InetOrgPerson | Similar to user, for compatibility with other directory services |
| Contacts | Email addresses for external users (no network access) |
| Groups | Simplify access control administration |
| Computers | Enable authentication and auditing of computer access |
| Printers | Simplify locating and connecting to printers |
| Shared Folders | Enable searching for shared folders by properties |
