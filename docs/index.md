---
slug: '/'
sidebar_label: 'WebServices ACS'
---

# WebServices ACS Documentation

Latest version is 25.0.0

WebServices ACS provides direct Rest-API access to applications without the need for the installation of additional components.
It is part of the ACS (Agentless Connector System) suite of products. 

ACS is a new OpCon Agent type that provides a framework for agent development. It is an internal component provided by the SMANetCom module. 
All integrations are generated DLL's and placed in a standard folder that is monitored by the ACS services.

These modules are loaded into the OpCon environment during startup. New modules can be copied to the monitored folder and will be available for 
configuration after the SMA OpCOn Service Manager and SMA OpCon RestAPI services are restarted.

All code and task / agent screen definitions are contained in the generated DLL that is placed in the monitored folder. To display the task and 
agent definitions, the form layouts are retrieved from the DLL and passed to Solution Manager to render the screen layout. Agent / task definitions are 
stored as JSON values in the OpCon database tables.

Agent / task definitions for the ACS environment can only be created / updated using Solution Manager.
JORS support for the ACS environment is only provided through Solution Manager.

WebService ACS comprises of two separate environments ACSWebservices and ACSAzureWebservices.

Provides jobtypes that can be used to create task definitions. Each jobtype is a separate OpCon task and information is passed between tasks using the
capabilities of the ACS framework (information passed between tasks are saved as Schedule Instance properties).  

## ACSAzureWebservices
Provides defined integrations with the MicroSoft Azure environment. Includes authentication tasks and tasks to start DevOps pipelines and Upload and Download files to/from Azure storage.
The following job-types are currently available.

JobType              | Description
---------------------|------------
GetOAuth2Token       | Get an OAuth2 token 
GetPatToken          | Create a Azure DevOps authentication token using a PAT (Personal Access Token)
RunDevOpsPipeline    | Starts an Azure DevOps pipeline and monitors for completion
DownloadBlobStorage  | Download a file from Azure Blob Storage
UploadBlobStorage    | Upload a file to Azure Blob Storage

## ACSWebservices
Provides generic implementations for authentication and standard GET, POST, PUT, PATCH and DELETE functions.

JobType              | Description
---------------------|------------
BASICTOKEN           | Creates a basic token that can be used on subsequent tasks
OPCONTOKEN           | Gets an OpCon token that can be used on subsequent tasks
OAUTH2TOKEN          | Gets an OAuth2 token that can be used on subsequent tasks
GET                  | Used to define a RestAPI GET function
POST                 | Used to define a RestAPI POST function
PUT                  | Used to define a RestAPI PUT function
PATCH                | Used to define a RestAPI PATCH function
DELETE               | Used to define a RestAPI DELETE function
