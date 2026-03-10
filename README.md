# Azure-CSP-2-EA-migration
Scenario 1 — Billing transfer (BEST case, no downtime)
CSP → EA within the SAME Microsoft Entra tenant
If the CSP subscription and EA enrollment are in the same tenant, Microsoft supports a subscription transfer:
✅ What happens

The subscription stays the same
Resources do not move
No downtime
Only billing ownership and agreement type change

✅ How it’s done

Use Azure subscription / product transfer (Microsoft Cost Management)
Coordinated between customer, CSP partner, and Microsoft

✅ Microsoft‑supported
Microsoft explicitly documents subscription transfers between CSP and EA as a billing ownership transfer, not a resource migration [learn.microsoft.com], [docs.azure.cn]
⚠️ Limitations

Billing & usage history does not move
Quotas may reset to EA defaults
Tenant must be the same

✅ This is the preferred approach whenever possible

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
