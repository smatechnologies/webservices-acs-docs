---
sidebar_label: 'Release notes'
title: WebServices ACS release notes
description: "Version history and change details for the ACS WebServices and ACS AzureWebservices connectors, including new features and bug fixes."
tags:
  - Reference
  - Automation Engineer
  - System Administrator
  - Agents
---

# WebServices ACS release notes

## ACS AzureWebservices

### 25.0.4

2026

#### Bug fixes

- **Fixed Azure Storage token generation** Resolved issue where token generation for Azure Storage resulted in key errors by implementing OAuth2 V2.0 token generation using new GetOAuth2V2Token job.

## ACS Webservices

### 25.0.2

2025

#### Bug fixes

- **Fixed log file cleanup.** Resolved an issue where old log files were not deleted correctly.

### 25.0.0

Initial release.

---

## ACS AzureWebservices

### 25.0.3

2025

#### Bug fixes

- **Fixed log file cleanup.** Resolved an issue where old log files were not deleted correctly.

### 25.0.2

2025

#### New features

- **Added GetKeyVaultValue job type.** You can now retrieve secrets, keys, and certificates from Azure Key Vault directly within an OpCon schedule. A debug option is also included for troubleshooting.

### 25.0.1

2025

#### New features

- **Added RunDataFactoryPipeline job type.** You can now start and monitor a Microsoft Data Factory pipeline from an OpCon schedule.

### 25.0.0

Initial release.
