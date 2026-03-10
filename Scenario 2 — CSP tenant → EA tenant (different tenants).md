❌ Scenario 2 — CSP tenant → EA tenant (different tenants)
This is a TECHNICAL migration
If the EA is in a different tenant, Microsoft does NOT support a direct move of resources.
There is:

❌ No Azure Resource Mover
❌ No Azure Migrate
❌ No direct ARM move


✅ Supported options when tenants are different

✅ Option A — Transfer the entire CSP subscription to the EA tenant
(If CSP subscription type allows directory change)

Use “Change directory / Transfer subscription to another Entra tenant”
Moves the whole subscription into the EA tenant
Resources stay intact

📌 This is the only supported “lift‑and‑shift” across tenants
 [docs.azure.cn], [azuredoctor.com]
Trade‑offs

RBAC assignments removed
Managed identities must be recreated
Some services don’t survive the transfer

✅ Option B — Rebuild + migrate (most common in CSP → EA)
When subscription transfer isn’t allowed (very common for CSP):
How it works

Create new EA subscriptions in target tenant
Re‑deploy infrastructure using:

ARM / Bicep / Terraform


Migrate data using:

AzCopy
Backup & Restore
Replication


Re‑establish:

Identity
RBAC
Networking


✅ Fully supported
❌ Not lift‑and‑shift
📌 Microsoft explicitly states that unsupported CSP transfers require resource‑level migration [learn.microsoft.com]

✅ Option C — Azure Site Recovery (VM‑only)

Used for Azure VM replication
Helps reduce downtime
Does not migrate PaaS

Supported but narrow scope
 [azuredoctor.com]

🚫 What CANNOT be used


| Tool | CSP → EA (different tenants) |
|---|---|
| Azure Resource Mover | ❌ No |
| Azure Migrate | ❌ No |
| ARM move | ❌ No |


| ToolCSP → EA (different tenants)Azure Resource Mover❌ NoAzure Migrate❌ NoARM move❌ No