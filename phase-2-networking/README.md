# Phase 2 – Networking & Security

This phase focuses on designing and implementing secure network communication in Azure using Virtual Networks, subnets, Network Security Groups (NSGs), and VNet peering.

The goal of this phase is to demonstrate **least-privilege networking**, **tier isolation**, and **private connectivity** without exposing internal resources to the public internet.

---

## Architecture Overview

- One application Virtual Network (`vnet-app`) with separated tiers:
  - `web-subnet` (frontend)
  - `app-subnet` (backend)
- One additional Virtual Network (`vnet-shared`) representing shared or external services
- Private, bidirectional VNet-to-VNet peering between the two networks

---

## Deployment Evidence

### Virtual Network Creation

A dedicated Virtual Network (`vnet-app`) was created with a `/16` address space to allow future growth without redesign.

- Address space: `10.10.0.0/16`
- Region: Norway East

![VNet Basics](screenshots/01-vnet-basics.png)

---

### Subnet Segmentation

The application network was divided into purpose-based subnets to enforce separation of concerns:

- **web-subnet** (`10.10.1.0/24`) – frontend tier
- **app-subnet** (`10.10.2.0/24`) – backend tier

This design limits lateral movement and enables granular security controls.

![Subnets Created](screenshots/02-subnets-created.png)

---

### Web Subnet Security (Frontend Tier)

A Network Security Group (`nsg-web`) was applied at the **subnet level** to control inbound traffic to the web tier.

Allowed inbound traffic:
- HTTP (TCP 80) from Internet
- HTTPS (TCP 443) from Internet

All other inbound traffic is denied by default.

![Web NSG Rules](screenshots/03-nsg-web-rules.png)

---

### NSG Association to Web Subnet

The `nsg-web` Network Security Group was explicitly associated with the `web-subnet` to ensure consistent enforcement of security rules across all frontend resources.

![Web NSG Associated](screenshots/04-nsg-web-associated.png)

---

### Application Subnet Security (Backend Tier)

A separate Network Security Group (`nsg-app`) was created to protect backend services.

Allowed inbound traffic:
- TCP port `8080` **only from the web-subnet (`10.10.1.0/24`)**

No direct inbound access from the Internet is permitted to the backend tier.

![App NSG Rules](screenshots/05-nsg-app-inbound-rules.png)

---

### NSG Association to Application Subnet

The `nsg-app` Network Security Group was associated with the `app-subnet`, enforcing backend isolation and preventing unauthorized access.

![App NSG Associated](screenshots/06-nsg-app-associated.png)

---

### Secondary Virtual Network Creation

A second Virtual Network (`vnet-shared`) was created to simulate shared or external network environments commonly found in enterprise architectures.

- Address space: `10.20.0.0/16`
- Subnet: `shared-subnet` (`10.20.1.0/24`)

![Shared VNet Created](screenshots/07-vnet-shared-created.png)

---

### VNet-to-VNet Peering

Private, bidirectional VNet peering was configured between `vnet-app` and `vnet-shared`.

This enables secure, low-latency communication over the Azure backbone without using public IPs or VPN gateways.

![VNet Peering Connected](screenshots/09-vnet-peering-connected.png)

---

## Network Security Model

The implemented security model enforces the following behavior:

- Internet → Web subnet (HTTP/HTTPS): **Allowed**
- Internet → App subnet: **Blocked**
- Web subnet → App subnet (TCP 8080): **Allowed**
- All other inbound traffic: **Denied by default**

This follows **least-privilege** and **defense-in-depth** principles.

---

## Key Learnings

- Subnet segmentation improves security and operational clarity
- NSGs are most effective when applied at subnet level
- Default deny rules significantly reduce attack surface
- Backend services should never be directly internet-accessible
- VNet peering enables private connectivity without VPN overhead
- Azure Portal may auto-synchronize peering, requiring verification rather than duplication

---

## Outcome

Phase 2 successfully established a **secure and scalable networking foundation** by:

- Isolating frontend and backend tiers
- Enforcing strict inbound traffic controls
- Preventing direct backend exposure
- Enabling private communication between Azure networks

This phase provides a solid baseline for introducing more advanced networking patterns in subsequent phases.

---

## Future Enhancements (Out of Scope for This Phase)

The following improvements are intentionally **not implemented in Phase 2**, but can be introduced later:

- Hub-and-spoke network architecture
- VPN connectivity (Point-to-Site / Site-to-Site)
- Centralized firewall or NVA
- Azure Bastion for secure administrative access
