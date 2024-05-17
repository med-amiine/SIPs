---
sip: 387
title: Deploy Synthetix V3 Omnibus & Synthetix Perps on Mode
network: Mode
status: Draft
type: Governance
author: 'Med Amine (@med-amiine), Deez'
Implementor: TBD
Release: TBD
Proposal: Open
created: 2024-05-17
---

<!--You can leave these HTML comments in your merged SIP and delete the visible duplicate text guides, they will not appear and may be helpful to refer to if you edit it again. -->

## Simple Summary

Deploy the SNX token on Mode via the Mode Bridge, enabling seamless transfer of SNX tokens between the Ethereum Mainnet and Mode.

## Abstract

<!--A short (~200 word) description of the proposed change, the abstract should clearly describe the proposed change. This is what *will* be done if the SIP is implemented, not *why* it should be done or *how* it will be done. If the SIP proposes deploying a new contract, write, "we propose to deploy a new contract that will do x".-->

The isolated deployment will launch Synthetix on Mode with a focus on progressive scaling. Initially, the system will enable LP deposits and stablecoin minting against LP collateral, then enable Synthetix Perps for trading on Mode. The deployment features include a Mode-native stablecoin, LPing functionalities, and a comprehensive Synthetix Perps launch. The Mode deployment will experiment with the usage of additional collateral types, including weETH.mode, sUSDe, USDe, mBTC, ezETH, and sDAI.

## Motivation

<!--This is the problem statement. This is the *why* of the SIP. It should clearly explain *why* the current state of the protocol is inadequate.  It is critical that you explain *why* the change is needed, if the SIP proposes changing how something is calculated, you must address *why* the current calculation is inaccurate or wrong. This is not the place to describe how the SIP will address the issue!-->

The expansion to Mode is motivated by the desire to launch on a chain with increased DeFi/Perps trading activity, at a time when Synthetix and its ecosystem are prepared to onboard traders across multiple chains. This deployment will complement Synthetix's cross-chain strategy encompassing Optimism, Base, Arbitrum and now Mode. Alongside this, Synthetix is eligible to be a recipient of the DevDrop program, to support the initial scaling up of the system on Mode. By beginning with targeted incentives and carefully staged functionality rollout, the protocol aims to solidify its presence and utility for users on Mode.

## Deployment Plan

This SIP concerns itself with the Pre-Launch and Beta Launch plans and timeline below. Collateral Onboarding and Enabling Synthetix Perps are provided for context only.

**Pre-Launch Preparation**
- Deploy to Mode testnet, begin risk assessment, analyze differences between Mode & existing deployments.

**Beta Launch Phase (By June 17th)**
- Deploy Synthetix V3 Omnibus on Mode, initially activating LP deposits and stablecoin minting.

**LP Rampup & Collateral Onboarding**
- Attract a critical mass of LP collateral which can be used to issue stablecoins.

**Enabling Synthetix Perps**
- Enable the Synthetix Perps market, allowing users to delegate their collateral and subsequent liquidity to Synthetix Perps.
- Gradually enable trading activities, starting with limited volumes to manage risk.

## Incentive Programs
The incentive programs listed below are contingent on the successful deployment of V3 on Mode and are provided here for context only.

**User Incentives:**
- Add Synthetix enabled dApps / Integrators on the Mode dashboard (100,000 views daily)
- Added to Mode incentive program

**LP Incentives:**
- Mode can bootstrap liquidity via Mode incentives to reach $10m in LP to encourage initial scale and liquidity for LPs and stablecoins.

**Trading Incentives:**
- Introduce $200k of growth incentives to stimulate trading activity, these incentives are targeted towards trading fee rebates, trading competitions, and other growth experiments.

## Specification

<!--The specification should describe the syntax and semantics of any new feature, there are five sections
1. Overview
2. Rationale
3. Technical Specification
4. Test Cases
5. Configurable Values
-->

### Overview

<!--This is a high level overview of *how* the SIP will solve the problem. The overview should clearly describe how the new feature will be implemented.-->

Synthetix will deploy the V3 omnibus package containing the V3 core system, Oracle Manager, Spot Market, and Synthetix Perps markets. The implementation of the core V3 system will allow Synthetix to establish the core contracts on Mode, allowing users to LP the following collateral types: weETH.mode, sUSDe, USDe, mBTC, ezETH, and sDAI while minting a Mode-native stablecoin against their collateral as outlined below.

The Synthetix Perps market will be paused upon initial deployment, with no tradable markets.

|  LP Collateral                           | max amount                                      | issuance                                        | liquidation               |   
|------------------------------------------|-------------------------------------------------|-------------------------------------------------|---------------------------|
| weETH.mode                               | 125K                                            | 200%                                            | 125%                      |
| sUSDe                                    | 500K                                            | 150%                                            | 120%                      |
| USDe                                     | 500k                                            | 150%                                            | 120%                      |                                  
| mBTC                                     | 300k                                            | 200%                                            | 125%                      |                            
| ezETH                                    | 125k                                            | 200%                                            | 125%                      |
| sDAI                                     | 500k                                            | 120%                                            | 105%                      |

**Spot Market Wrappers**
- sUSDe Wrapper - 250k cap
- sDAI Wrapper - 500k cap

These spot markets will allow users to wrap/unwrap sUSDe/ssUSDe and sDAI/ssDAI 1:1, but will exchange for the stablecoin at price provided from Pyth, with a staleness no older than 24 hours.
Test Cases Mode testnet Omnibus to be deployed and audited ASAP.

### Test Cases

<!--Test cases for an implementation are mandatory for SIPs but can be included with the implementation..-->
Mode testnet Omnibus to be deployed and audited ASAP.

### Configurable Values (Via SCCP)

<!--Please list all values configurable via SCCP under this implementation.-->

- Stablecoin name/symbol: "ModeDollar" / "USDd"
- Minimum Liquidity Ratio: 200%
- LP Collateral (max amount / issuance / liquidation)
- Perps toml file active/inactive

## Copyright

Copyright and related rights waived via [CC0](https://creativecommons.org/publicdomain/zero/1.0/).
