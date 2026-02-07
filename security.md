# Security

[Risk Assesment](#risk-assessment) | [Security Controls](#security-controls) | [Plan](./plan.md) | [Network Design](./network.md) | [Cloud Services](./cloud.md) | [Ethics](./ethics.md) | [Reflection](./reflection.md) | [Return to index](./README.md)

## Risk Assessment

[View risk assessment spreadsheet](./risk-assessment.xlsx)

### TVA Matrix
![TVA 1](./threat-vulnerability-asset-1.png)  
![TVA 1](./threat-vulnerability-asset-2.png)  
![TVA 1](./threat-vulnerability-asset-3.png)

---

## Security Controls

As long as customer data is involved, the highest risk data asset will be **customer booking database**, as it will store all the private information, including PII and transactional data.

| Security Control (NIST) | How Implemented in Truelec Network | How It Reduces Risk | Network Location / Changes Required | User Disadvantages |
|---|---|---|---|---|
| **Multi-Factor Authentication (IA-2)** | The primary control required by Truelec is to deploy multi-factor authentication for all users accessing Truelec systems to ensure that only authorized users can access the data. | When MFA is enabled on all login gateways, only users with the MFA code generated via an authentication application can successfully verify their identity. | MFA must be enabled on VPN gateways, Active Directory servers, and cloud login portals such as IAM users or administrator accounts. | Additional login step for users |
| **Database Encryption (SC-28)** | Encryption must be applied to data at rest on the database, and TLS encryption must be implemented for communications between servers and branches. This can be managed via the Key Management Service offered by Azure. | All information stored in the database remains encrypted, ensuring that even if the database is compromised, attackers cannot read the stored data. | All cloud and local network database servers must implement AES encryption for data at rest and TLS for encryption in transit. | Additional service required for managing encryption keys |
| **Network Segmentation & Firewall Rules (SC-7)** | Proper network segmentation must be applied within the internal LAN, where each LAN segment has separate firewall rules. The booking application database server must be placed inside a secure VLAN with its own ACL rules. | Network segmentation prevents attacker lateral movement by enforcing different access control rules across isolated segments, protecting user workstations and network devices. | Implementation can be done on network switches by configuring VLANs, each with its own ACL rules. | Network configuration complexity increases due to VLANs |