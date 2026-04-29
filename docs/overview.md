---
title: WebServices ACS overview
sidebar_label: 'Overview'
description: "Overview of the ACS WebServices and ACS AzureWebservices connectors, including architecture, job types, and how data is passed between jobs."
tags:
  - Conceptual
  - Automation Engineer
  - Agents
---

# WebServices ACS overview

ACS WebServices provides direct REST API access to applications without requiring additional component installation. It is part of the ACS (Agentless Connector System) suite of products.

## What is it?

ACS WebServices and ACS AzureWebservices are OpCon connectors that allow you to automate REST API interactions and Azure cloud operations directly from OpCon schedules — without installing an agent on the target system.

- Use ACS WebServices when you need to call generic REST API endpoints for authentication, data retrieval, or submission using GET, POST, PUT, PATCH, or DELETE operations
- Use ACS AzureWebservices when you need to integrate with Microsoft Azure services such as Azure DevOps, Azure Data Factory, Azure Blob Storage, or Azure Key Vault
- Use either connector when your target system exposes a REST API but does not support a traditional OpCon agent installation

## Architecture

ACS is an OpCon agent type that provides a framework for connector development. It is an internal component provided by the SMANetCom module. All integrations are compiled DLL files placed in a standard folder monitored by the ACS services.

These modules load into the OpCon environment during startup. New modules can be copied to the monitored folder and become available for configuration after the **SMA OpCon Service Manager** and **SMA OpCon RestAPI** services are restarted.

All code and job and agent screen definitions are contained in the DLL. Screen layouts are retrieved from the DLL and passed to Solution Manager for rendering. Agent and job definitions are stored as JSON values in the OpCon database tables.

Agent and job definitions for the ACS environment can only be created or updated using Solution Manager. JORS support for the ACS environment is only provided through Solution Manager.

## Passing data between jobs

The ACS WebServices implementation does not include steps as in the previous WebServices Connector. Each function runs as a separate job. Information is passed between jobs using ACS scoped properties, which are saved as schedule instance properties of the associated schedule instance in the daily tables.

To save data, use the **Response Variables** section to define the variable name and its associated value. The variable name can then be used in the URLs and message bodies of subsequent jobs.

**Examples**

1. Pass the ID returned from a POST request to a subsequent job:
   - On the POST job, define a response variable `taskId=$.task.id`, where `taskId` is the variable name and `$.task.id` is the JPath expression to extract the ID from the returned JSON
   - In the subsequent GET job URL, reference the variable: `GET https://server:port/api/status/taskId`

2. Pass the ID from a POST request in the message body of a subsequent POST job:
   - On the POST job, define a response variable `taskId=$.task.id`
   - In the subsequent POST job message body, reference the variable: `{"previous-task":"taskId"}`

## ACS AzureWebservices job types

ACS AzureWebservices provides defined integrations with the Microsoft Azure environment, including authentication jobs and jobs to start DevOps pipelines and upload or download files to Azure storage.

| Job type | Description |
|---|---|
| GetOAuth2Token | Retrieves an OAuth2 token for authenticating subsequent Azure jobs |
| GetPatToken | Creates an Azure DevOps authentication token using a Personal Access Token (PAT) |
| GetKeyVaultValue | Retrieves secrets, keys, or certificates from Azure Key Vault |
| RunDevOpsPipeline | Starts an Azure DevOps pipeline and monitors it for completion |
| RunDataFactoryPipeline | Starts a Microsoft Data Factory pipeline and monitors it for completion |
| DownloadBlobStorage | Downloads a file from Azure Blob Storage |
| UploadBlobStorage | Uploads a file to Azure Blob Storage |

## ACS Webservices job types

ACS Webservices provides generic implementations for authentication and standard HTTP methods.

| Job type | Description |
|---|---|
| BASICTOKEN | Creates a basic token for use by subsequent jobs |
| OPCONTOKEN | Retrieves an OpCon token for use by subsequent jobs |
| OAUTH2TOKEN | Retrieves an OAuth2 token for use by subsequent jobs |
| GET | Performs a REST API GET request |
| POST | Performs a REST API POST request |
| PUT | Performs a REST API PUT request |
| PATCH | Performs a REST API PATCH request |
| DELETE | Performs a REST API DELETE request |

## Latest versions

| Connector | Latest version |
|---|---|
| ACS WebServices | 25.0.2 |
| ACS AzureWebServices | 25.0.3 |

## FAQs

**Do I need to install an agent on the target system?**
No. ACS WebServices and ACS AzureWebservices communicate directly with REST API endpoints. No agent installation is required on the target system.

**Where are the connector files installed?**
On-premises: copy the connector directory to the `\SAM\plugins` directory. Cloud: copy it to the `\Relay\plugins` directory.

**Can I use both ACS WebServices and ACS AzureWebservices in the same schedule?**
Yes. Each connector is configured as a separate agent definition in Solution Manager. You can include jobs from both connectors in the same schedule and define dependencies between them.

**How do I pass a token from an authentication job to a subsequent job?**
Define a **Response Variable** on the authentication job to store the token as a schedule instance property. Reference that property name in the **Header Attributes** field of subsequent jobs.

**Can I mix ACS WebServices jobs with standard OpCon jobs in the same schedule?**
Yes. ACS jobs run alongside standard OpCon jobs in a schedule. You can define job dependencies between ACS jobs and standard jobs using the standard OpCon dependency configuration.

## Glossary

**ACS (Agentless Connector System)** — An OpCon agent framework that allows connectors to run without a dedicated agent installation on the target system. All connector logic is contained in DLL files loaded by the ACS service.

**Scoped property** — A schedule instance property created and managed within the ACS framework. Scoped properties pass data between jobs in the same schedule instance.

**Response Variable** — A field in an ACS job definition that maps a JPath expression to a schedule instance property name. When the job runs, the extracted value is stored as the named property for use by subsequent jobs.

**JPath** — A query language for navigating JSON structures, similar to XPath for XML. Used in ACS Response Variable definitions to extract specific values from JSON responses (for example, `$.task.id` extracts the `id` field from a `task` object).

**Related topics:**

- [Installation](./installation.md)
- [ACS Webservices operation](./ACSWebservicesOperation.md)
- [ACS AzureWebservices operation](./ACSAzureWebservicesOperation.md)
- [Release notes](./release-notes.md)
