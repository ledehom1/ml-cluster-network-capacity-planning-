# ml-cluster-network-capacity-planning-
# ML Cluster Network Capacity Planning Framework

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![GitHub stars](https://img.shields.io/github/stars/ledehom1/ml-cluster-network-capacity-planning.svg?style=social)](https://github.com/ledehom1/ml-cluster-network-capacity-planning)

> A comprehensive capacity planning and deployment framework for large-scale ML cluster networking infrastructure supporting 10,000 TPUs across 5 global data centers, implementing Google's CAPA architecture principles.

[📖 Read the Full Documentation](02-architecture/architecture-design-document.md) | [📊 View Capacity Model](03-capacity-model/) | [🔧 Deployment Runbook](05-deployment-runbook/)

---

## 🎯 Project Overview

This project demonstrates end-to-end Technical Program Management for deploying network infrastructure to support Google-scale ML training workloads. It includes capacity planning, architecture design, program management artifacts, and operational runbooks based on production-proven practices.

**Scenario:** Plan and deploy cluster networking capacity for 10,000 TPU chips distributed across 5 data centers to enable large-scale distributed machine learning training.

### Key Highlights

✅ **CAPA Architecture Integration** - Implements Google's Containment and Prevention Architecture for high-availability operations  
✅ **Comprehensive Capacity Model** - Interactive calculator with bandwidth analysis and growth projections  
✅ **Production-Ready Runbooks** - Detailed SOPs, troubleshooting guides, and configuration templates  
✅ **Risk Management** - 73% reduction in incident rate through systematic enforcement of best practices  
✅ **Real-World Scale** - Designed for ~20 Pbps aggregate bandwidth across 5 data centers  

---

## 📊 Key Metrics

| Metric | Value |
|--------|-------|
| **Total Capacity** | 10,000 TPUs across 5 DCs |
| **Network Bandwidth** | ~20 Pbps aggregate |
| **Hardware Components** | 160 spine switches, 585 leaf switches |
| **Project Timeline** | 18 months |
| **Capital Budget** | $338M |
| **Network SLA** | 99.99% availability, <10μs latency |
| **Expected Reliability** | 73% reduction in incident rate |

---

## 🏗️ Architecture Highlights

### Three-Layer CAPA Architecture┌─────────────────────────────────────────────┐
│     OPERATIONS WORKFLOW LAYER               │
│  - Capacity Forecasting                     │
│  - Hardware Procurement                     │
│  - Installation Orchestration               │
└─────────────────────────────────────────────┘
↓ (Behavioral Intents)
┌─────────────────────────────────────────────┐
│       REGULATION LAYER                      │
│  - Drain-Before-Operate Enforcement         │
│  - Rate Limiting (Fleet-Wide)               │
│  - Protected Cross-Section Bandwidth        │
│  - Automatic Rollback on Health Failure     │
└─────────────────────────────────────────────┘
↓ (Management Operations)
┌─────────────────────────────────────────────┐
│     PRODUCTION CRITICAL LAYER               │
│  - Spine-Leaf Fabric (BGP Routing)          │
│  - SDN Controllers                          │
│  - Fail-Static Routing                     │
│  - Low-Dependency Design                    │
└─────────────────────────────────────────────┘

### Technical Design

- **Topology:** Spine-leaf (Clos) with full-mesh connectivity
- **Scale:** 32 spines, 117 leaves per DC
- **Routing:** eBGP with ECMP across 32 paths
- **Redundancy:** 4 independent failure domains, 25% headroom enforced
- **Performance:** 1:1 oversubscription, <10μs latency, 99.99% availability

---

## 📂 Repository Structure

### [01-executive-summary/](01-executive-summary/)
High-level overview and executive presentation
- Business case and objectives
- Solution summary with key metrics
- Slide deck for stakeholder presentations

### [02-architecture/](02-architecture/)
Detailed network architecture and design
- Complete Architecture Design Document (60+ pages)
- CAPA integration details
- Network topology diagrams
- BGP routing design
- Failure scenarios and recovery

### [03-capacity-model/](03-capacity-model/)
Interactive capacity planning tools
- Excel/Python capacity calculator
- Bandwidth calculations and validations
- Cross-section capacity analysis
- 18-month growth projections
- Cost modeling and TCO analysis

### [04-program-management/](04-program-management/)
Program planning and execution artifacts
- 18-month deployment timeline (Gantt chart)
- RACI matrix
- Risk register with CAPA mitigations
- Rate limiting policies (YAML)
- Communication plan

### [05-deployment-runbook/](05-deployment-runbook/)
Operational procedures and documentation
- **SOPs:** Step-by-step installation procedures
- **Deployment Playbook:** Phased rollout strategy
- **Troubleshooting:** Decision trees and escalation procedures
- **Config Templates:** BGP, regulation layer APIs, validation scripts

### [06-capa-framework/](06-capa-framework/)
CAPA architecture implementation details
- Drain-before-operate enforcement
- Protected cross-section bandwidth
- Rate limiting policies
- Failure domain containment
- Fail-static routing design

### [07-documentation/](07-documentation/)
Supporting documentation
- Glossary of terms
- References and further reading
- Lessons learned
- FAQ

---

## 🛠️ Technical Highlights

### CAPA Architecture Principles

This framework implements Google's CAPA (Containment and Prevention Architecture) to systematically enforce production best practices:

1. **Drain-Before-Operate**: All operations must drain traffic first, protecting against unexpected side effects
2. **Protected Cross-Section Bandwidth**: Enforces 25% minimum headroom at all network cross-sections
3. **Fleet-Wide Rate Limiting**: Hierarchical concurrency control prevents correlated failures
4. **Failure Domain Containment**: Strict ACL enforcement ensures failures remain isolated
5. **Fail-Static Routing**: BGP fallback maintains WAN connectivity despite control plane failures
6. **Low-Dependency Design**: Production layer independent of external services for disaster recovery

### Network Design

**Spine-Leaf Topology:**
- 32 spine switches per DC (AS 65001-65032)
- 117 leaf switches per DC (AS 65101-65217)
- Full-mesh connectivity: Every leaf connects to every spine
- ECMP load balancing across all 32 spines

**Capacity:**
- Per DC: ~4 Pbps (3,994 Tbps actual)
- Aggregate: ~20 Pbps across 5 DCs
- Per TPU: 400 Gbps interconnect bandwidth
- Headroom: 25% enforced by CAPA

**Technologies:**
- 400G QSFP-DD transceivers (32,640 total)
- eBGP routing with BFD for fast convergence
- RoCE for RDMA over Ethernet (ML workloads)
- Fail-static routing for WAN resilience

---

## 🎓 Skills Demonstrated

### Technical Program Management
✅ Complex multi-phase program planning (18 months, $338M)  
✅ Cross-functional coordination (network, facilities, procurement, ML teams)  
✅ Risk identification and mitigation (15 risks mapped to CAPA mechanisms)  
✅ Budget planning and tracking (CapEx + OpEx modeling)  
✅ Stakeholder communication (multi-level communication plan)  

### Technical Depth
✅ Data center networking (spine-leaf, BGP, ECMP)  
✅ ML infrastructure requirements (TPU networking, all-reduce patterns)  
✅ Capacity planning at scale (~20 Pbps)  
✅ Network automation and configuration management  
✅ Operational excellence (SOPs, runbooks, troubleshooting frameworks)  
✅ Production reliability (CAPA architecture, 73% incident reduction)  

### Documentation & Communication
✅ Technical writing for multiple audiences (engineers, executives, operators)  
✅ Executive presentations (slide decks with clear metrics)  
✅ Detailed operational procedures (SOPs with time estimates)  
✅ Visual communication (network diagrams, decision trees, timelines)  

---

## 🚀 How to Use This Repository

### For Recruiters/Hiring Managers
1. Start with the [Executive Summary](01-executive-summary/README.md)
2. Review the [Architecture Design Document](02-architecture/architecture-design-document.md)
3. Check out the [Capacity Calculator](03-capacity-model/)
4. Browse the [Deployment Playbook](05-deployment-runbook/02-deployment-playbook/deployment-playbook.md)
