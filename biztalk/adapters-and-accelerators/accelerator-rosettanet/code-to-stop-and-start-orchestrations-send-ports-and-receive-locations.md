---
title: 停止和啟動協調流程、 傳送埠和接收位置，以程式設計的方式 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- examples, orchestrations
- send ports, examples
- SDK samples, send ports
- examples, send ports
- SDK samples, orchestrations
- receive locations
- SDK samples, receive locations
- examples, receive locations
ms.assetid: 1c06e14d-44ec-4292-a2c2-ee2c8d07d948
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2736f76e3292c6e21a05c995afdd2808a9f60590
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995471"
---
# <a name="stopping-and-starting-orchestrations-send-ports-and-receive-locations-programmatically"></a>停止和啟動協調流程、 傳送埠和接收位置，以程式設計的方式
本主題提供以程式控制方式停止及啟動協調流程、傳送埠和接收位置的範例程式碼。 您可以將所有的協調流程、傳送埠和接收位置當做群組或個別地執行這些動作。 只要將這個程式碼包含在程式中，即可動態地執行這些動作。 在圖形化使用者介面中執行這些動作在設計階段於 Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]，或在 BizTalk 管理主控台中的執行階段。  
  
> [!NOTE]
>  對於用來啟動和停止協調流程的程式碼，您不必指定協調流程、傳送埠或接收位置。 範例程式碼上所有的協調流程執行動作、 傳送埠和接收位置，[!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)]安裝的。 對於在單一協調流程、傳送埠或接收位置執行動作的程式碼，則請新增指示程式碼執行所在之協調流程、傳送埠或接收位置的參數。  
  
## <a name="demonstrates"></a>示範  
 本主題中的範例程式碼包含不同的程式碼區段，可以執行下列動作：  
  
-   啟動協調流程：啟動所有傳送埠和接收位置，並登錄及啟動所有協調流程  
  
-   停止協調流程：取消登錄所有協調流程和傳送埠，並停用所有接收位置  
  
-   啟動單一傳送埠  
  
-   啟用單一接收位置  
  
-   取消登錄單一傳送埠  
  
-   停用單一接收位置  
  
-   啟動單一協調流程  
  
-   取消登錄單一協調流程  
  
## <a name="example"></a>範例  
 本主題中的範例程式碼包含不同的程式碼區段，可以執行＜展示＞一節所列的功能。  
  
```  
using System;  
using Microsoft.BizTalk.ExplorerOM;  
  
namespace Control  
{  
class Control  
{  
BtsCatalogExplorer bceExplorer;  
string[] sOrchestrations;  
string[] sReceiveLocations;  
string[] sSendPorts;  
  
[STAThread]  
static void Main(string[] args)  
{  
Control controlInstance = new Control();  
if(args.Length>0 && args[0].ToUpper()=="STOP")  
controlInstance.StopOrchestrations();  
else  
controlInstance.StartOrchestrations();  
}  
  
public Control()  
{  
bceExplorer = new BtsCatalogExplorer();  
//Edit the following connection string to point to the correct database and server  
bceExplorer.ConnectionString = "Integrated Security=SSPI;database=BizTalkMgmtDb;server=localhost";  
  
//Orchestrations  
sOrchestrations = new string[9];  
sOrchestrations[0]="Microsoft.Solutions.BTARN.CommonTypes.OdxTypes,Microsoft.Solutions.BTARN.CommonTypes, Version=3.3.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35";  
sOrchestrations[1]="Microsoft.Solutions.BTARN.CommonTypes.SendExceptionToLOB,Microsoft.Solutions.BTARN.CommonTypes, Version=3.3.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35";  
sOrchestrations[2]="Microsoft.Solutions.BTARN.CommonTypes.SendExceptionToPrivateProcess,Microsoft.Solutions.BTARN.CommonTypes, Version=3.3.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35";  
sOrchestrations[3]="Microsoft.Solutions.BTARN.PrivateInitiator.PrivateInitiatorProcess,Microsoft.Solutions.BTARN.PrivateInitiator, Version=3.3.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35";  
sOrchestrations[4]="Microsoft.Solutions.BTARN.PrivateResponder.PrivateResponderProcess,Microsoft.Solutions.BTARN.PrivateResponder, Version=3.3.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35";  
sOrchestrations[5]="Microsoft.Solutions.BTARN.PublicInitiator.PublicInitiatorV11,Microsoft.Solutions.BTARN.PublicInitiator, Version=3.3.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35";  
sOrchestrations[6]="Microsoft.Solutions.BTARN.PublicInitiator.PublicInitiatorProcess,Microsoft.Solutions.BTARN.PublicInitiator, Version=3.3.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35";  
sOrchestrations[7]="Microsoft.Solutions.BTARN.PublicResponder.PublicResponderV11,Microsoft.Solutions.BTARN.PublicResponder, Version=3.3.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35";  
sOrchestrations[8]="Microsoft.Solutions.BTARN.PublicResponder.PublicResponderProcess,Microsoft.Solutions.BTARN.PublicResponder, Version=3.3.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35";  
  
//Send Ports  
sSendPorts = new string[2];  
sSendPorts[0]="PrivateInitiator_To_LOB";  
sSendPorts[1]="PrivateResponder_To_LOB";  
  
//Receive Locations  
sReceiveLocations = new string[4];  
sReceiveLocations[0]="LOB_To_PrivateInitiator";  
sReceiveLocations[1]="LOB_To_PrivateResponder";  
sReceiveLocations[2]="RNIF_Async_Receive";  
sReceiveLocations[3]="RNIF_Sync_Receive";  
}  
  
public void StartOrchestrations()  
{     
bool bSuccess=true;  
  
//Start all the send ports  
for(int i=0;i<sSendPorts.Length;i++)  
{  
Console.WriteLine("Starting send port: " + sSendPorts[i]);  
bSuccess=StartSendPort(sSendPorts[i]);  
}  
  
//Start all the receive locations  
for(int i=0;i<sReceiveLocations.Length;i++)  
{  
Console.WriteLine("Enabling receive location: " + sReceiveLocations[i]);  
bSuccess=EnableReceiveLocation(sReceiveLocations[i]);  
}  
  
//Enlist and start all orchestrations  
for(int i=0;i<sOrchestrations.Length;i++)  
{  
Console.WriteLine("Starting orchestration: " + sOrchestrations[i].Split(',')[0]);  
bSuccess=StartOrchestration(sOrchestrations[i]);  
}  
  
if(bSuccess)  
Console.WriteLine("All artifacts successfully started");  
else  
Console.WriteLine("Not all artifacts were started");  
}  
  
public void StopOrchestrations()  
{     
bool bSuccess=true;  
  
//Unenlist all orchestrations  
for(int i=sOrchestrations.Length-1;i>=0;i--)  
{  
Console.WriteLine("Unelisting orchestration: " + sOrchestrations[i].Split(',')[0]);  
bSuccess=UnenlistOrchestration(sOrchestrations[i]);  
}  
  
//Unenlist all the send ports  
for(int i=sSendPorts.Length-1;i>=0;i--)  
{  
Console.WriteLine("Unenlisting send port: " + sSendPorts[i]);  
bSuccess=UnenlistSendPort(sSendPorts[i]);  
}  
  
//Disable all the receive locations  
for(int i=sReceiveLocations.Length-1;i>=0;i--)  
{  
Console.WriteLine("Disabling receive location: " + sReceiveLocations[i]);  
bSuccess=DisableReceiveLocation(sReceiveLocations[i]);  
}  
  
if(bSuccess)  
Console.WriteLine("All artifacts successfully stopped");  
else  
Console.WriteLine("Not all artifacts were stopped");  
}  
  
public bool StartSendPort(string sSendPortName)  
{  
try  
{  
SendPort sp = bceExplorer.SendPorts[sSendPortName];  
sp.Status = PortStatus.Started;  
bceExplorer.SaveChanges();  
return true;  
}  
catch(Exception e)  
{  
Console.WriteLine(e.Message);  
bceExplorer.DiscardChanges();  
return false;  
}  
}  
  
public bool EnableReceiveLocation(string sReceivePortName)  
{  
try  
{  
ReceivePort rp = bceExplorer.ReceivePorts[sReceivePortName];  
              foreach(ReceiveLocation rl in rp.ReceiveLocations)  
rl.Enable = true;  
  
bceExplorer.SaveChanges();  
return true;  
}  
catch(Exception e)  
{  
Console.WriteLine(e.Message);  
bceExplorer.DiscardChanges();  
return false;  
}  
}  
  
public bool UnenlistSendPort(string sSendPortName)  
{  
try  
{  
SendPort sp = bceExplorer.SendPorts[sSendPortName];  
sp.Status = PortStatus.Bound;  
  
bceExplorer.SaveChanges();  
return true;  
}  
catch(Exception e)  
{  
Console.WriteLine(e.Message);  
bceExplorer.DiscardChanges();  
return false;  
}  
}  
  
public bool DisableReceiveLocation(string sReceivePortName)  
{  
try  
{  
ReceivePort rp = bceExplorer.ReceivePorts[sReceivePortName];  
  
foreach(ReceiveLocation rl in rp.ReceiveLocations)  
rl.Enable = false;  
  
bceExplorer.SaveChanges();  
return true;  
}  
catch(Exception e)  
{  
Console.WriteLine(e.Message);  
bceExplorer.DiscardChanges();  
return false;  
}  
}  
  
private bool StartOrchestration(string sOrchestrationName)  
{  
  
BtsAssemblyCollection btsAssemblyCollection = bceExplorer.Assemblies;  
  
foreach (Microsoft.BizTalk.ExplorerOM.BtsAssembly btsAssembly in btsAssemblyCollection)  
{  
if(sOrchestrationName.Split(',')[1]==btsAssembly.DisplayName.Split(',')[0])  
{  
foreach (Microsoft.BizTalk.ExplorerOM.BtsOrchestration btsOrchestration in btsAssembly.Orchestrations)  
{  
if(sOrchestrationName==btsOrchestration.AssemblyQualifiedName)  
{  
btsOrchestration.Status=OrchestrationStatus.Started;  
try  
{  
bceExplorer.SaveChanges();  
return true;  
}  
catch(Exception e)  
{  
Console.WriteLine(e.Message);  
bceExplorer.DiscardChanges();  
return false;  
}  
}  
}  
}  
}  
return false;  
}  
  
private bool UnenlistOrchestration(string sOrchestrationName)  
{  
  
BtsAssemblyCollection btsAssemblyCollection = bceExplorer.Assemblies;  
  
foreach (Microsoft.BizTalk.ExplorerOM.BtsAssembly btsAssembly in btsAssemblyCollection)  
{  
if(sOrchestrationName.Split(',')[1]==btsAssembly.DisplayName.Split(',')[0])  
{  
foreach (Microsoft.BizTalk.ExplorerOM.BtsOrchestration btsOrchestration in btsAssembly.Orchestrations)  
{  
if(sOrchestrationName==btsOrchestration.AssemblyQualifiedName)  
{  
btsOrchestration.AutoTerminateInstances=true;  
btsOrchestration.Status=OrchestrationStatus.Unenlisted;  
try  
{  
bceExplorer.SaveChanges();  
return true;  
}  
catch(Exception e)  
{  
Console.WriteLine(e.Message);  
bceExplorer.DiscardChanges();  
return false;  
}  
}  
}  
}  
}  
return false;  
}  
  
}  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [範例](../../adapters-and-accelerators/accelerator-rosettanet/samples3.md)