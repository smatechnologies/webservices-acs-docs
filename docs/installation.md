---
title: ACS installation and upgrade
description: "Install or upgrade the ACS Webservices or ACS AzureWebservices connector by downloading the package from the SMA FTP Site and deploying it to the correct plugins directory."
tags:
  - Procedural
  - System Administrator
  - Installation
  - Upgrade
---

# ACS installation and upgrade

**Theme:** Build
**Who is it for?** System Administrator

## What is it?

The ACS Webservices and ACS AzureWebservices connectors extend OpCon by enabling automated HTTP-based and Azure-based integrations. Installing the connector deploys the required plugin files to the OpCon environment, making the connector available for agent and job configuration in Solution Manager.

- Use this procedure when setting up the connector for the first time on a new OpCon environment
- Use the upgrade procedure when a new connector version is available and you need to replace the existing plugin files

## Installation

To install the ACS connector, complete the following steps:

1. Download the `ACSAzureWebservices.zip` or the `ACSWebservices.zip` file from the SMA FTP Site. The file is located at one of the following paths:
   - `/OpCon Releases/Integrations/Webservices/`
   - `/OpCon Releases/Integrations/AzureWebservices/`
2. Select the required version.
3. Unzip the `ACSAzureWebservices.zip` or the `ACSWebservices.zip` file.
4. Complete the steps for your deployment type:

   | Deployment type | Steps |
   |---|---|
   | On-prem | Copy the `ACSAzureWebservices\ACSWebservices` directory to the `\\SAM\\plugins` directory. Restart the **SMA OpCon Services Manager** and **SMA OpCon RestAPI** service. |
   | Cloud | Copy the `ACSAzureWebservices\ACSWebservices` directory to the `\\Relay\\plugins` directory. Restart the **SMA OpCon Relay** service. |

The connector is installed and available for configuration in Solution Manager.

## Upgrade

To upgrade the ACS connector, complete the following steps:

1. Download the `ACSAzureWebservices.zip` or the `ACSWebservices.zip` file from the SMA FTP Site. The file is located at one of the following paths:
   - `/OpCon Releases/Integrations/Webservices/`
   - `/OpCon Releases/Integrations/AzureWebservices/`
2. Unzip the `ACSAzureWebservices.zip` or the `ACSWebservices.zip` file.
3. Complete the steps for your deployment type:

   | Deployment type | Steps |
   |---|---|
   | On-prem | Stop the **SMA OpCon Services Manager** and **SMA OpCon RestAPI** service. Copy the `ACSAzureWebservices\ACSWebservices` directory to the `\\SAM\\plugins` directory. Restart the **SMA OpCon Services Manager** and **SMA OpCon RestAPI** service. |
   | Cloud | Copy the `ACSAzureWebservices\ACSWebservices` directory to the `\\Relay\\plugins` directory. Restart the **SMA OpCon Relay** service. |

The connector is upgraded to the new version.

## FAQs

**Where do I find the connector package?**
The package is available on the SMA FTP Site under `/OpCon Releases/Integrations/Webservices/` or `/OpCon Releases/Integrations/AzureWebservices/` depending on which connector you are installing.

**Which plugins directory do I copy files to?**
On-prem deployments use the `\\SAM\\plugins` directory. Cloud deployments use the `\\Relay\\plugins` directory.

**Do I need to stop services before upgrading?**
For on-prem deployments, stop the **SMA OpCon Services Manager** and **SMA OpCon RestAPI** service before copying files. For cloud deployments, you can copy the files and then restart the **SMA OpCon Relay** service without a prior stop step.

## Glossary

**ACS Webservices** — An OpCon connector that enables jobs to make HTTP requests (GET, POST, PUT, PATCH, DELETE) to remote REST APIs as part of automated schedules.

**ACS AzureWebservices** — An OpCon connector that enables jobs to interact with Azure services including DevOps pipelines, Data Factory pipelines, Key Vault, and Blob Storage.

**Plugin** — The deployed connector files placed in the `plugins` directory that OpCon loads at service startup to make a connector available.

**SMA OpCon Services Manager** — The Windows service that manages OpCon components on on-prem installations.

**SMA OpCon Relay** — The Windows service used in cloud-hosted OpCon deployments in place of the on-prem Services Manager.
