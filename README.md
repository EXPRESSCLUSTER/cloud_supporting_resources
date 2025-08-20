# IP Address & Hostname Failover Matrix (EXPRESSCLUSTER × Azure / AWS)

| Item                             | Azure                                      | AWS                                        |
|----------------------------------|--------------------------------------------|--------------------------------------------|
| **Virtual IP (VIP) failover**     | ❌ Not supported (VIP not available)        | ✅ Supported (via ENI reattachment)         |
| **Elastic IP reassignment**       | ❌ Not applicable (no EIP concept in Azure) | ✅ Supported (reassign EIP to new instance) |
| **Secondary IP failover**         | ❌ Not recommended (NIC manipulation limited) | ✅ Supported (multiple IPs on ENI)         |
| **DNS hostname switching**        | ✅ Supported (Azure DNS + script automation) | ✅ Supported (Route 53 + script automation) |
| **Virtual Computer Name (vcom)**  | ⚠️ Limited (NetBIOS constraints)            | ⚠️ Limited (not recommended in cloud)       |
| **Dynamic DNS resource (ddns)**   | ✅ Recommended (cloud-friendly)             | ✅ Recommended (cloud-friendly)             |

## Notes

- **Azure** does not support Layer 3 VIP failover, so DNS-based switching is the mainstream approach.
- **AWS** offers more flexibility with ENI and EIP, enabling direct IP failover.
- **vcom (Virtual Computer Name)** is designed for on-premises use; DNS-based alternatives are preferred in cloud environments.
- **Script resources** can be used to automate DNS or IP updates during failover events.
