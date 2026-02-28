---
sidebar_label: 'Installation'
---

# ACS Installation

Download the ACSAzureWebservices.zip or the ACSWebservices.zip file from the SMA FTP Site.
Location will be in
**/OpCon Releases/Integrations/Webservices/** 
**/OpCon Releases/Integrations/AzureWebservices/** 

Select the required version.

- Unzip the ACSAzureWebservices.zip or the ACSWebservices.zip files.
- On-prem customers 
  Copy the ACSAzureWebservices\ACSWebservices directory to the \\SAM\\plugins directory
  Restart the **SMA OpCon Services Manager** and **SMA OpCon RestAPI** service.
- Cloud customers
  Copy the ACSAzureWebservices\ACSWebservices directory to the \\Relay\\plugins directory
  Restart the **SMA OpCon Relay** service.

# ACS Upgrade

Download the ACSAzureWebservices.zip or the ACSWebservices.zip file from the SMA FTP Site.
Location will be in
**/OpCon Releases/Integrations/Webservices/** 
**/OpCon Releases/Integrations/AzureWebservices/** 

- Unzip the ACSAzureWebservices.zip or the ACSWebservices.zip files.
- On-prem customers 
  Stop the **SMA OpCon Services Manager** and **SMA OpCon RestAPI** service.
  Copy the ACSAzureWebservices\ACSWebservices directory to the \\SAM\\plugins directory
  Restart the **SMA OpCon Services Manager** and **SMA OpCon RestAPI** service.
- Cloud customers
  Copy the ACSAzureWebservices\ACSWebservices directory to the \\Relay\\plugins directory
  Restart the **SMA OpCon Relay** service.