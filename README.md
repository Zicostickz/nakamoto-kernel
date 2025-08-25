# Nakamoto Kernel

A decentralized protocol for building secure, user-controlled data networks with fine-grained access management and community-driven participation.

## Overview

The Nakamoto Kernel provides a robust, modular infrastructure for creating decentralized data ecosystems with the following core capabilities:

- Secure user and device registration
- Granular, transparent access permissions
- Dynamic, opt-in community participation
- Privacy-preserving data sharing mechanisms
- Flexible, composable protocol design

Our protocol empowers users to maintain complete ownership and control of their digital assets while enabling innovative, community-driven applications.

## Architecture

The system is built around a central core protocol that orchestrates:

```mermaid
graph TD
    A[Users] --> B[Identity Management]
    A --> C[Access Control]
    A --> D[Community Interactions]
    A --> E[Data Initiatives]
    
    B --> F[Device Registration]
    C --> G[Consent Tracking]
    D --> H[Participation Mechanisms]
    E --> I[Contribution Frameworks]
    
    F --> J[Secure Metadata]
    G --> K[Permissioned Access]
    H --> L[Incentive Structures]
    I --> L
```

Core components:
- Decentralized identity management
- Secure metadata handling
- Granular access control
- Community participation frameworks
- Flexible incentive mechanisms

## Contract Documentation

### core-protocol.clar

The foundational protocol managing core network functionality.

#### Key Features:

1. **Identity Management**
   - Secure user registration
   - Device and access token management
   - Account lifecycle controls

2. **Access Governance**
   - Cryptographically-secured permissions
   - Transparent consent tracking
   - Revocable access rights

3. **Community Dynamics**
   - Modular participation frameworks
   - Dynamic challenge and initiative systems
   - Merit-based reward distributions

## Getting Started

### Prerequisites
- Clarinet
- Stacks wallet

### Installation

1. Clone the repository
2. Install dependencies:
```bash
clarinet install
```

3. Test the contract:
```bash
clarinet test
```

### Basic Usage

1. Register a user:
```clarity
(contract-call? .health-mesh register-user (some "John") (some "profile-url"))
```

2. Register a device:
```clarity
(contract-call? .health-mesh register-device "device-123" "smartwatch")
```

3. Grant data access:
```clarity
(contract-call? .health-mesh grant-data-permission 
  GRANTEE_PRINCIPAL 
  "heart-rate" 
  u86400 
  "research-study")
```

## Function Reference

### User Management

```clarity
(register-user (name (optional (string-utf8 50))) (profile-data-url (optional (string-utf8 256))))
(update-profile (name (optional (string-utf8 50))) (profile-data-url (optional (string-utf8 256))))
(deactivate-account)
```

### Device Management

```clarity
(register-device (device-id (string-utf8 64)) (device-type (string-utf8 50)))
(update-device-sync (device-id (string-utf8 64)))
(remove-device (device-id (string-utf8 64)))
```

### Data Access Control

```clarity
(grant-data-permission (grantee-id principal) (data-type (string-utf8 30)) (duration uint) (purpose (string-utf8 100)))
(revoke-data-permission (grantee-id principal) (data-type (string-utf8 30)))
(record-data-access (user-id principal) (data-type (string-utf8 30)))
```

### Community Features

```clarity
(create-health-challenge (name (string-utf8 100)) (description (string-utf8 256)) ...)
(join-challenge (challenge-id uint))
(submit-challenge-completion (challenge-id uint))
(claim-challenge-reward (challenge-id uint))
```

## Development

### Testing

Run the test suite:
```bash
clarinet test
```

### Local Development

1. Start Clarinet console:
```bash
clarinet console
```

2. Deploy contract:
```bash
clarinet deploy
```

## Security Considerations

1. **Data Privacy**
   - All actual health data is stored off-chain
   - Only encrypted storage references are maintained on-chain
   - Granular permission control with expiration

2. **Access Control**
   - Time-bound permissions
   - Revocable access rights
   - Transparent consent tracking

3. **Limitations**
   - Contract cannot guarantee off-chain data deletion
   - Users should review permissions regularly
   - Research contributions are one-way and cannot be withdrawn