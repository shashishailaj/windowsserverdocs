---
title: A Replica server must be configured to accept replication requests
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: 
  - hyper-v
  - techgroup-compute
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9f5ddb52-bfb2-4d57-90e5-3e1bf595941c
author: KBDAzure
---
# A Replica server must be configured to accept replication requests
\[This information is preliminary and subject to change.\]  
  
For more information about best practices and scans, see [Run Best Practices Analyzer Scans and Manage Scan Results](http://go.microsoft.com/fwlink/p/?LinkID=223177).  
  
|||  
|-|-|  
|**Operating System**|[!INCLUDE[winthreshold_server_2](includes/winthreshold_server_2_md.md)]|  
|**Product\/Feature**|Hyper\-V|  
|**Severity**|Error|  
|**Category**|Configuration|  
  
In the following sections, italics indicates UI text that appears in the Best Practices Analyzer tool for this issue.  
  
## Issue  
*This computer is designated as a Hyper\-V Replica server but is not configured to accept incoming replication data from primary servers.*  
  
## Impact  
*This server cannot accept replication traffic from primary servers.*  
  
## Resolution  
*Use Hyper\-V Manager to specify which primary servers this Replica server should accept replication data from.*  
  
#### Create authorization entries using Hyper\-V Manager  
  
1.  Open Hyper\-V Manager. \(From Server Manager, click **Tools** > **Hyper\-V Manager**.\)  
  
2.  From the list of hosts, right\-click the one you want, then click **Hyper\-V Settings**.  
  
3.  In the navigation pane, click **Replication Configuration**.  
  
4.  Under **Authorization and storage**, click **Allow replication from the specified servers**.  
  
5.  Below the list of servers, click **Add**.  
  
6.  Under **Add Authorization Entry**:  
  
    -   Type the fully qualified name of the first server.  
  
    -   Specify a dedicated location to store only that server's files.  
  
7.  Click **OK**.  
  
8.  Repeat for each primary server.  
  
9. Click **OK** again to finish and close the window.  
  
### Create authorization entries using Windows PowerShell  
  
1.  Open Windows PowerShell. \(From the desktop, click Start and start typing **[!INCLUDE[wps_2](includes/wps_2_md.md)]**.\)  
  
2.  Right\-click **[!INCLUDE[wps_2](includes/wps_2_md.md)]** and click **Run as administrator**.  
  
3.  Run a command similar to the following, replacing:  
  
    -   The primary server name of server01.domain01.contoso.com with the fully qualified domain name of your server.  
  
    -   The location of D:\\ReplicaVMStorage with your location.  
  
    -   The trust group named DEFAULT with name of your group, if you've created one. If not, use DEFAULT.  
  
```  
New-VMReplicationAuthorizationEntry server01.domain01.contoso.com D:\ReplicaVMStorage DEFAULT  
```  
  
