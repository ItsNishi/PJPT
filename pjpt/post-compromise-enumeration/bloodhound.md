# BloodHound

Graph-based AD attack path visualization tool. Uses Neo4j to map relationships and find paths to Domain Admin.

## Components

- **SharpHound** -- Data collector (runs on target)
- **BloodHound** -- GUI for visualizing data (runs on attacker)
- **Neo4j** -- Graph database backend

## Setup

```bash
# Start Neo4j
sudo neo4j start

# Default creds: neo4j/neo4j (change on first login)
# Access at http://localhost:7474

# Start BloodHound
bloodhound
```

## Data Collection with SharpHound

```powershell
# On target machine
. .\SharpHound.ps1

# Collect all data
Invoke-BloodHound -CollectionMethod All -Domain DOMAIN.local -ZipFileName loot.zip

# Alternative: use the exe
.\SharpHound.exe -c All
```

Transfer the zip file back to your attacker machine.

## Using BloodHound

### Importing Data

1. Open BloodHound
2. Click upload icon (or drag and drop)
3. Select the SharpHound zip file

### Key Pre-Built Queries

- **Find all Domain Admins** -- Shows DA group members
- **Shortest Paths to Domain Admins** -- Most important query
- **Find Computers with Unsupported OS** -- Easy targets
- **Find Kerberoastable Users** -- Accounts with SPNs set
- **Shortest Paths to High Value Targets** -- Attack paths to sensitive groups

### Node Info

Click any node to see:
- Group memberships
- Admin rights
- Sessions
- Outbound/inbound object control

### Custom Queries

Right-click nodes to:
- Mark as owned (track progress)
- Mark as high value
- Find shortest path from owned principals

## Tips

- Run SharpHound during business hours for best session data
- Re-collect periodically as sessions change
- Mark compromised nodes as "owned" to find new paths
- Check "Derivative Local Admin" edges for indirect access
