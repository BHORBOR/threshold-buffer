# Threshold Buffer

A flexible, secure buffer management system for dynamic blockchain applications with configurable threshold mechanisms.

## Overview

Threshold Buffer is a comprehensive smart contract suite built on Clarity, providing robust and adaptable buffer management with granular threshold controls. The system enables precise tracking, validation, and reward allocation across various application domains.

## Core Components

The system consists of four primary smart contracts:

### Threshold Registry (`threshold-registry`)
- Manages participant accounts and configurations
- Handles registration and authentication
- Controls access levels and permissions
- Stores dynamic threshold parameters

### Buffer Core (`buffer-core`)
- Tracks and manages dynamic buffer allocations
- Supports multiple buffer types and strategies
- Implements flexible threshold measurement
- Maintains historical buffer state and transitions

### Validator Core (`validator-core`)
- Validates buffer state changes and threshold crossings
- Supports multiple validation strategies:
  - Rule-based validation
  - Probabilistic assessment
  - Multi-signature verification
  - External oracle integration
- Assigns confidence and risk scores

### Reward Mechanism (`reward-mechanism`)
- Issues dynamic rewards for validated buffer events
- Manages reward calculations based on threshold complexity
- Implements tiered achievement system
- Provides flexible reward distribution options

## Smart Contract Details

### User Registry

The user registry contract manages user accounts and profile information, serving as the foundation for identity in the ecosystem.

#### Key Functions:
```clarity
(define-public (register-user (username (string-utf8 50)) (region (string-utf8 30)) 
               (sustainability-goal (string-utf8 200)) (privacy-setting uint)))
(define-public (update-profile (username (string-utf8 50)) (region (string-utf8 30))
               (sustainability-goal (string-utf8 200))))
(define-public (update-privacy-setting (privacy-setting uint)))
```

### Carbon Tracker

This contract enables users to track their carbon footprint through various activities and calculates environmental impact.

#### Activity Types:
- Transport: Car, Bus, Train, Plane, Bike, Walk
- Energy: Electricity, Gas, Heating Oil, Renewable
- Diet: Meat (Beef/Other), Fish, Vegetarian, Vegan
- Consumption: Clothes, Electronics, Household, Recycled

#### Key Functions:
```clarity
(define-public (log-activity (activity-type uint) (activity-subtype uint) (amount uint)))
(define-read-only (get-user-carbon-total (user principal)))
(define-read-only (calculate-goal-progress (user principal)))
```

### Verification System

The verification system ensures the integrity of reported sustainable actions through multiple validation methods.

#### Verification Types:
- Self-attestation
- Photo/video evidence
- Community validation
- IoT device integration
- Third-party verification

#### Key Functions:
```clarity
(define-public (submit-activity (activity-type uint) (description (string-utf8 500))
               (verification-type uint) (evidence-hash (optional (buff 32)))))
(define-public (validate-activity (activity-id uint) (approved bool)
               (notes (optional (string-utf8 200)))))
```

### Eco Rewards

This contract manages the reward system, issuing tokens for verified sustainable actions and implementing engagement mechanisms.

#### Features:
- Token rewards based on action type and verification level
- Achievement badges (Bronze, Silver, Gold, Platinum)
- Community challenges
- Token redemption options

#### Key Functions:
```clarity
(define-public (record-action (action-id (string-ascii 36)) (action-type uint)
               (verification-level uint)))
(define-public (create-challenge (name (string-ascii 50)) (description (string-ascii 200))
               (action-type uint) (required-count uint) (reward-amount uint) (duration uint)))
(define-public (redeem-tokens (option-id uint)))
```

## Getting Started

To interact with the EcoForge platform:

1. Register a user account using the `user-registry` contract
2. Start tracking carbon footprint by logging activities in the `carbon-tracker`
3. Submit activities for verification through the `verification-system`
4. Earn and manage rewards using the `eco-rewards` contract

## Future Enhancements

The platform is designed to support future expansions including:
- Community challenges and competitions
- Carbon offset marketplace integration
- External verification service partnerships
- Enhanced data analytics and reporting
- Mobile app integration

This project is actively developed and welcomes community contributions.