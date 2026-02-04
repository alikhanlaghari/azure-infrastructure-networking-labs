# Azure AZ-104 – Application & Network Management Labs

This repository contains a structured, hands-on Azure lab series aligned with the **AZ-104 (Microsoft Azure Administrator)** certification and real-world **application management and infrastructure operations** scenarios.

The labs are designed to demonstrate **practical, explainable Azure skills** with a strong focus on security, reliability, and professional documentation practices.

Each phase builds progressively, following architectural patterns commonly used in **enterprise Azure environments**.

---

## What This Repository Demonstrates

- Azure infrastructure provisioning using best practices
- Secure network design and traffic control
- Application hosting and access management
- Hybrid connectivity patterns
- Operational validation and troubleshooting
- Clear technical documentation with evidence

This is not theoretical content — every phase is **built, validated, documented, and reviewed**.

---

## Completed Phases

### ✅ Phase 1 – Compute & Application Foundation
- Windows Server Virtual Machine deployment
- Secure administrative access configuration
- Automated IIS installation using Azure VM Extensions
- Application availability validation and troubleshooting
- Defense-in-depth awareness (NSGs + OS-level configuration)
- Full documentation with screenshots and explanations

---

### ✅ Phase 2 – Networking & Security
- Azure Virtual Networks with tier-based subnet segmentation
- Frontend (`web-subnet`) and backend (`app-subnet`) isolation
- Subnet-level Network Security Groups (NSGs)
- Least-privilege inbound traffic control
- Backend isolation from the public internet
- Private VNet-to-VNet peering over the Azure backbone
- Architecture diagrams and deployment screenshots

---

### ✅ Phase 3 – Hybrid Connectivity
- Azure Route-based VPN Gateway deployment
- Point-to-Site (P2S) VPN using certificate-based authentication
- Secure remote access without exposing virtual machines publicly
- Root and client certificate creation and validation
- Azure VPN Client configuration
- End-to-end connectivity verification using private IP access
- Cost-aware teardown of Azure resources after validation

This phase demonstrates a common **enterprise remote-access pattern** and forms the foundation for more advanced hybrid networking scenarios.

---

## Repository Structure

azure-az104-application-network-labs/
│
├── phase-1-compute/
│ └── README.md
│ └── screenshots/
│
├── phase-2-networking-security/
│ └── README.md
│ └── screenshots/
│
├── phase-3-hybrid-connectivity/
│ ├── README.md
│ └── screenshots/
│
└── README.md


Each phase contains:
- A dedicated README
- Deployment evidence (screenshots)
- Architecture explanations
- Validation steps
- Key learnings and outcomes

---

## Purpose of This Repository

The goal of this project is to:

- Build **practical Azure skills** that can be clearly explained
- Focus on **security-first and operationally sound designs**
- Provide **reviewable evidence** of hands-on work
- Prepare for roles involving:
  - Application management
  - Infrastructure operations
  - Network and hybrid connectivity
  - Cloud administration in enterprise environments

This repository is intended to reflect how Azure solutions are **designed, validated, documented, and discussed** in real professional settings.

---

## Technologies Used

- Microsoft Azure
- Azure Virtual Machines (Windows & Linux)
- Azure Virtual Networks & Subnets
- Network Security Groups (NSGs)
- VNet Peering
- Azure VPN Gateway (Point-to-Site)
- Certificate-based authentication
- Azure VM Extensions
- Azure VPN Client
- GitHub for version control and documentation
