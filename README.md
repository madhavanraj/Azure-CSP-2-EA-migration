# Azure-CSP-2-EA-migration
Scenario 1 — Billing transfer (BEST case, no downtime)
CSP → EA within the SAME Microsoft Entra tenant
If the CSP subscription and EA enrollment are in the same tenant, Microsoft supports a subscription transfer



❌ Scenario 2 — CSP tenant → EA tenant (different tenants)
This is a TECHNICAL migration
If the EA is in a different tenant, Microsoft does NOT support a direct move of resources.


| Situation | Recommended approach |
|---|---|
| Same tenant | **Subscription billing transfer** |
| Different tenant, whole estate | **Subscription directory transfer** |
| Different tenant, selective workloads | **Rebuild + data migration** |
| VM‑only, minimal downtime | **Azure Site Recovery** |


Refer : https://docs.azure.cn/en-us/cost-management-billing/manage/subscription-transfer
