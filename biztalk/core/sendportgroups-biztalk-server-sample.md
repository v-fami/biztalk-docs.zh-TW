---
title: SendPortGroups （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4510aa31-16c3-475a-98aa-b590e13ae189
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 035cd5d0f6b3c37861574d3ace81b15e1dfbc06d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990039"
---
# <a name="sendportgroups-biztalk-server-sample"></a>SendPortGroups （BizTalk Server 範例）
SendPortGroups 範例示範如何列舉使用和管理傳送埠群組**Microsoft.BizTalk.ExplorerOM**管理類別。  

## <a name="prerequisites"></a>必要條件  

- 您必須擁有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理權限才能在此範例中使用的系統管理物件。  

- Windows PowerShell 指令碼需要 Windows PowerShell 執行原則，以允許執行指令碼。 如需詳細資訊，請參閱 [檢查執行原則](http://go.microsoft.com/fwlink/?LinkId=128930)。  

## <a name="what-this-sample-does"></a>此範例的用途  
 此範例示範如何使用**BtsCatalogExplorer**並**SendPortGroup**類別**Microsoft.BizTalk.ExplorerOM**命名空間來管理傳送埠群組在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。 此範例以 Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]。 本主題也包含 Windows PowerShell 範例指令碼。 此範例會示範下列作業：  

- 使用連接到 「 BizTalk 管理 」 資料庫**BtsCatalogExplorer**類別。  

- 建立新的傳送埠群組，名為 「 我將傳送埠群組 」。  

- 列舉的傳送埠群組，以顯示新建立傳送埠群組。  

- 正在刪除新的傳送埠群組。  

  其他函式會出現在此範例中，但不是會在執行[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]版本。  PowerShell 範例指令碼將示範一些額外的函式。 其他函式會示範下列功能：  

- 加入新建立的傳送埠群組 （PowerShell 範例涵蓋） 中的傳送埠。  

- 刪除傳送埠的傳送埠群組 （如 PowerShell 範例所述）。  

- 啟動傳送埠群組。  

- 停止傳送埠群組。  

## <a name="where-to-find-this-sample"></a>此範例的位置  
 這個範例位於下列 SDK 位置：  

 \<*範例路徑*\>\Admin\ExplorerOM\SendPortGroups  

 下表顯示此範例中的檔案，並描述其用途。  


|                            檔案                            |                                                 描述                                                  |
|---------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
|                       SendPortGroups.cs                       | [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] 此範例中示範的作業的原始程式檔。 |
| SendPortGroups.sln，SendPortGroups.csproj，SendPortGroups.suo |                                  此範例的方案和專案檔。                                  |

## <a name="building-and-running-this-sample"></a>建置和執行此範例  

#### <a name="to-build-this-sample"></a>建置此範例  

1. 在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟方案檔 SendPortGroups.sln。  

2. 在 [方案總管] 中，按兩下**SendPortGroups.cs**開啟範例程式碼。  

3. 尋找`root.ConnectionString`在`CreateSendPortGroup`函式。  您必須變更以正確指向裝載 BizTalk 管理資料庫的 SQL server 的伺服器規格。  您也可以使用句號 （.） 來連接到本機的 SQL server。  例如：  

   ```  
   root.ConnectionString = "Integrated Security=SSPI;database=BizTalkMgmtDb;server=.";  
   ```  

4. 重複步驟 3 來執行下列功能：  

   -   **EnumerateSendPortGroups**  

   -   **DeleteSendPortGroup**  

5. 儲存**SendPortGroups.cs**。  

6. 在主功能表中，按一下 **建置**，然後按一下**建置方案**。  

#### <a name="to-run-this-sample"></a>執行此範例  

1.  開啟命令視窗並巡覽至下列資料夾：  

     \<*範例路徑*\>\Admin\ExplorerOM\SendPortGroups\bin\Debug  

2.  執行檔案 SendPortGroups.exe。  

## <a name="windows-powershell-script-example"></a>Windows PowerShell 指令碼範例  
 下列 Windows PowerShell 指令碼片段，可以用來示範相同的功能**ExplorerOM**類別：  

```  
Function CreateSendPortGroup($Catalog, $strName)  
{  
   #=== Register a trap handler to discard changes on exceptions ===#  

   $ErrorActionPreference="silentlycontinue"  
   trap { "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes.`r`n";$Catalog.DiscardChanges();exit; }  

   #=== Create a new send port group and set its name ===#  

   $NewSendPortGroup = $Catalog.AddNewSendPortGroup()  
   $NewSendPortGroup.Name = $strName  

   #=== Persist new ports to the BizTalk Management database ===#  

   Write-Host Adding "`"$($NewSendPortGroup.Name)`"..."  
   $catalog.SaveChanges();  
   Write-Host "`r`nCreateSendPortGroup() completed."  
}  

Function DeleteSendPortGroup($Catalog,$strName)  
{  
   #=== Register a trap handler to discard changes on exceptions ===#  

   $ErrorActionPreference="silentlycontinue"  
   trap { "Exception encountered DeleteSendPortGroup:`r`n"; $_; "`r`nDiscarding Changes.`r`n";$Catalog.DiscardChanges();}  

   #=== Delete this sample's new send ports by name ===#  

   $NewSendPortGroup = $Catalog.SendPortGroups[$strName]  
   $Catalog.RemoveSendPortGroup($NewSendPortGroup)  

   #=== Persist changes to the BizTalk Management database ===#  

   Write-Host "Deleting `"$strName`"..."  
   $catalog.SaveChanges();  
   Write-Host "DeleteSendPortGroup() completed."  
}  

Function EnumerateSendPortGroups($Catalog)  
{  
   #=== Register a trap handler to discard changes on exceptions ===#  

   $ErrorActionPreference="silentlycontinue"  
   trap { "Exception encountered During Enumeration:`r`n"; $_; "`r`n"}  

   #=== Display all send port groups by name ===#  

   $count = 1  
   foreach ($group in $catalog.SendPortGroups)  
   {  
     Write-Host "$count. $($group.Name)"  
     $count++  
   }  

   Write-Host "`r`nEnumerateSendPortGroups() completed."  
}  

Function PromptForSendPort($Catalog)  
{  
   #=== Provide a list of the send ports for the user to make a selection ===#  

   Write-Host "Here is a list of send ports:`r`n"  
   $count = 1  
   foreach($sendport in $Catalog.SendPorts)  
   {  
      Write-Host ($Count). ($Sendport.Name)  
      $count++  
   }     

   Write-Host "`r`nChoose a port to add to the group by ordinal (ex. 1,2, etc): " -nonewline  
   $selection = read-host  
   $selection = $Catalog.SendPorts[([int]$selection)-1]  
   Write-Host $Selection.Name selected.  

   return $Selection.Name     
}  

Function AddSendPortToSendPortGroup($Catalog,$strPortName,$strGroupName)  
{  

   #=== Add the user's selected send port to the group ===#  

   #========================================================#  
   #=== Presently, we have to use WMI from PowerShell    ===#  
   #=== This is because the methods on the collections   ===#  
   #=== are marked internal. So unfortunately the        ===#  
   #=== following very straightforward code won't work.  ===#  
   #========================================================#  

   # $sendportgroup = $Catalog.SendPortGroups[$strName]  
   # $sendportgroup.SendPorts.Add($Catalog.SendPorts[$strPortName])  
   # $catalog.SaveChanges();  

   #============================================================================#  
   #=== Get the WMI send port group representation to look up DB and server. ===#     
   #=== Expecting only one to match the query in this example.               ===#  
   #============================================================================#  

   $WQL = "select * from MSBTS_SendPortGroup where Name='" + $strGroupName + "'"  
   $groupset = gwmi -query ($WQL) -namespace "root\MicrosoftBizTalkServer"  

   #=== Create a new MSBTS_SendPortGroup2SendPort instance to map the port to the group ===#     

   $group2port = [WMICLASS]"root\MicrosoftBizTalkServer:MSBTS_SendPortGroup2SendPort"  
   $newPortEntry = [WMI] $group2port.psbase.CreateInstance()  
   $newPortEntry.MgmtDbServerOverride = $groupset.MgmtDbServerOverride   
   $newPortEntry.MgmtDbNameOverride = $groupset.MgmtDbNameOverride  
   $newPortEntry.SendPortGroupName = $groupset.Name  
   $newPortEntry.SendPortName = $strPortName  
   Write-Host "Adding $strPortName to $($groupset.Name)"  

   #=== Persist changes to the BizTalk Management database ===#  

   #=== POWERSHELL V1 BUG WORKAROUND =============================#  
   #=== First method call on a non-cimv2 WMI object can fail.  ===#  
   #=== The workaround in PowerShell V1 is to call GetType()   ===#  
   #=== as the first method.                                   ===#   
   $ErrorActionPreference="silentlycontinue"                     
   trap {}  
   $newPortEntry.GetType()  
   #=== POWERSHELL V1 BUG WORKAROUND =============================#  

   $ErrorActionPreference="continue"                     
   [void] $newPortEntry.Put()  

   #=== Since we used WMI to update the BizTalk Management database, ===#  
   #=== refresh our BtsExplorerCatalog to have an updated DB view.   ===#  

   $Catalog.Refresh()  
   Write-Host "AddSendPortToSendPortGroup() completed."  
}  

Function DeleteSendPortFromSendPortGroup($Catalog, $strPortName, $strGroupName)  
{  
   #========================================================#  
   #=== Presently, we have to use WMI from PowerShell    ===#  
   #=== This is because the methods on the collections   ===#  
   #=== are marked internal. So unfortunately the        ===#  
   #=== following very straightforward code won't work.  ===#  
   #========================================================#  

   # $sendportgroup = $Catalog.SendPortGroups[$strGroupName]  
   # $sendportgroup.SendPorts.Remove($Catalog.SendPorts[$strPortName])  
   # $catalog.SaveChanges();  

   #============================================================================#  
   #=== Get the WMI send port to group instance and delete it.               ===#     
   #=== Expecting only one to match the query in this example.               ===#  
   #============================================================================#  

   $WQL = "select * from MSBTS_SendPortGroup2SendPort where " +   
          "SendPortName='" + $strPortName + "' and " +   
          "SendPortGroupName='" + $strGroupName + "'"  

   $groupset = gwmi -query ($WQL) -namespace "root\MicrosoftBizTalkServer"  

   write-host "Removing $strPortName from $strGroupName..."  
   $groupset.Delete();  

   #=== Since we used WMI to update the BizTalk Management database, ===#  
   #=== refresh our BtsExplorerCatalog to have an updated DB view.   ===#  

   $Catalog.Refresh()  
   Write-Host "DeleteSendPortFromSendPortGroup() completed."  
}  

#========================#  
#=== Main Script Body ===#  
#========================#  

#=== Make sure the ExplorerOM assembly is loaded ===#  

[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  

#=== Connect to the BizTalk Management database ===#  

$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "DATABASE=BizTalkMgmtDb;Integrated Security=SSPI;SERVER=."  

#=== Exercise the CreateSendPortGroup function to create a new send port group ===#  

$SendPortGroupName = "PowerShell Sample Send Port Group"  

Write-Host "`r`n============================="  
Write-Host "=== CreateSendPortGroup() ==="  
Write-Host "=============================`r`n"  
CreateSendPortGroup $Catalog $SendPortGroupName  

#=== Enumerate all send port groups to view the new one ===#  

Write-Host "`r`n================================="  
Write-Host "=== EnumerateSendPortGroups() ==="  
Write-Host "=================================`r`n"  
EnumerateSendPortGroups $Catalog  

#=== Add a send port to the group ===#  

Write-Host "`r`n===================================="  
Write-Host "=== AddSendPortToSendPortGroup() ==="  
Write-Host "====================================`r`n"  
$SendPortName = PromptForSendPort($Catalog)  
AddSendPortToSendPortGroup $Catalog $SendPortName $SendPortGroupName  

#=== Remove the send port from the group ===#  

Write-Host "`r`n========================================="  
Write-Host "=== DeleteSendPortFromSendPortGroup() ==="  
Write-Host "=========================================`r`n"  
DeleteSendPortFromSendPortGroup $Catalog $SendPortName $SendPortGroupName  

#=== Delete the group ===#  

Write-Host "`r`n============================="  
Write-Host "=== DeleteSendPortGroup() ==="  
Write-Host "=============================`r`n"  
DeleteSendPortGroup $Catalog $SendPortGroupName  

Write-Host  
```  

 以下是從執行 Windows PowerShell 指令碼範例的範例預期輸出。  

```  
PS C:\> .\sendportgroups.ps1  

=============================  
=== CreateSendPortGroup() ===  
=============================  

Adding "PowerShell Sample Send Port Group"...  

CreateSendPortGroup() completed.  

=================================  
=== EnumerateSendPortGroups() ===  
=================================  

1. PowerShell Sample Send Port Group  

EnumerateSendPortGroups() completed.  

====================================  
=== AddSendPortToSendPortGroup() ===  
====================================  

Here is a list of send ports:  

1 . ResendPort  
2 . HelloWorldSendPort  
3 . ToCustomerSendPort  
4 . CBRUSSendPort  
5 . CBRCANSendPort  
6 . SendportCANOrders  

Choose a port to add to the group by ordinal (ex. 1,2, etc): 2  
HelloWorldSendPort selected.  
Adding HelloWorldSendPort to PowerShell Sample Send Port Group  
AddSendPortToSendPortGroup() completed.  

=========================================  
=== DeleteSendPortFromSendPortGroup() ===  
=========================================  

Removing HelloWorldSendPort from PowerShell Sample Send Port Group...  
DeleteSendPortFromSendPortGroup() completed.  

=============================  
=== DeleteSendPortGroup() ===  
=============================  

Deleting "PowerShell Sample Send Port Group"...  
DeleteSendPortGroup() completed.  
```  

## <a name="see-also"></a>另請參閱  
 [Admin-ExplorerOM (BizTalk Server Samples 資料夾)](../core/admin-explorerom-biztalk-server-samples-folder.md)