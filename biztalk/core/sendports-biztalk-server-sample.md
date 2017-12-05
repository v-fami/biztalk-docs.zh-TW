---
title: "SendPorts （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b84f96a2-b749-4fe0-be15-e4dd13eff66f
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0bd7c03e4cfa586a0dddd2579931bd5f30d293fa
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="sendports-biztalk-server-sample"></a>SendPorts （BizTalk Server 範例）
傳送埠 」 範例示範如何列舉和管理傳送埠使用**Microsoft.BizTalk.ExplorerOM**系統管理類別。  
  
## <a name="prerequisites"></a>必要條件  
  
-   您必須擁有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在此範例中使用的系統管理物件的系統管理權限。  
  
-   Windows PowerShell 指令碼需要 Windows PowerShell 執行原則以允許執行指令碼。 如需詳細資訊，請參閱：[檢查執行原則](http://go.microsoft.com/fwlink/?LinkId=128930)。  
  
## <a name="what-this-sample-does"></a>此範例的用途  
 這個範例示範如何使用**BtsCatalogExplorer**和**SendPort**類別**Microsoft.BizTalk.ExplorerOM** 中的命名空間管理傳送埠[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。 此範例以 Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]。 本主題也包含 Windows PowerShell 範例指令碼。 此範例會示範下列作業：  
  
1.  使用連接到 「 BizTalk 管理 」 資料庫**BtsCatalogExplorer**類別。  
  
2.  建立兩個新的傳送埠命名為 myStaticOnewaySendPort1 和 myDynamicTwowaySendPort1。 myStaticOnewaySendPort1，正如其名，都是靜態單向傳送埠。  它會建立範例的目的 URL http://sample1 搭配使用 HTTP 傳輸。 myDynamicTwowaySendPort1 會建立為動態雙向傳送埠。  
  
3.  列舉中的傳送埠[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。 這個範例列舉型別應該包含兩個新的傳送埠。  
  
4.  刪除兩個新的傳送埠。  
  
5.  設定新傳送埠。 此範例所示範的設定會套用至名為 myStaticOnewaySendPort1 範例傳送埠。 下列範例所套用的設定：  
  
    -   啟用**連接埠處理前的要求訊息**追蹤訊息內文的選項。  
  
    -   啟用**連接埠處理後的要求訊息**追蹤訊息內文的選項。  
  
    -   指定用於外寄訊息的傳送埠加密憑證。  
  
    -   指定針對一組訊息的登記篩選條件。  
  
    -   新增對應來轉換訊息。  
  
6.  變更兩個新的傳送埠上的傳送埠狀態。  執行此範例會變更下列狀態 myStaticOnewaySendPort1 上：  
  
    -   將狀態變更為已啟動。  
  
    -   將狀態變更為已停止。  
  
    -   將狀態變更為繫結。 取消登錄與相同繫結的狀態。  
  
## <a name="where-to-find-this-sample"></a>此範例的位置  
 這個範例位於下列 SDK 位置：  
  
 \<*範例路徑*\>\Admin\ExplorerOM\SendPorts  
  
 下表顯示此範例中的檔案，並描述其用途。  
  
|檔案|Description|  
|---------------|-----------------|  
|SendPorts.cs|[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]這個範例中示範的作業的來源檔案。|  
|SendPorts.sln，SendPorts.csproj，SendPorts.suo|此範例的方案和專案檔。|  
  
## <a name="building-and-running-this-sample"></a>建置和執行此範例  
  
#### <a name="to-build-this-sample"></a>建置此範例  
  
1.  在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟方案檔 SendPorts.sln。  
  
2.  在主功能表中，按一下 **建置**，然後按一下 **建置方案**。  
  
#### <a name="to-run-this-sample"></a>執行此範例  
  
1.  開啟命令視窗並巡覽至下列資料夾：  
  
     \<*範例路徑*\>\Admin\ExplorerOM\SendPorts\bin\Debug  
  
2.  執行檔案 SendPorts.exe。  
  
## <a name="windows-powershell-script-example"></a>Windows PowerShell 指令碼範例  
 下列 Windows PowerShell 指令碼片段可以用來示範的相同功能**ExplorerOM**類別：  
  
```  
Function CreateSendPorts($Catalog)  
{  
    #=== Register a trap handler to discard changes on exceptions ===#  
  
    $ErrorActionPreference="silentlycontinue"  
    trap { "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes.`r`n";$Catalog.DiscardChanges();exit; }  
  
    #=== create a new static one-way send port using HTTP transport ===#  
  
    $myStaticOnewaySendPort = $Catalog.AddNewSendPort($false,$false)  
    $myStaticOnewaySendPort.Name = "myStaticOnewaySendPort1"  
    $myStaticOnewaySendPort.PrimaryTransport.TransportType = $catalog.ProtocolTypes["HTTP"]  
    $myStaticOnewaySendPort.PrimaryTransport.Address = "http://sample1"  
    $myStaticOnewaySendPort.SendPipeline = $Catalog.Pipelines["Microsoft.BizTalk.DefaultPipelines.XMLTransmit"]  
  
    #=== create a new dynamic two-way send port ===#  
  
    $myDynamicTwowaySendPort = $catalog.AddNewSendPort($true,$true)  
    $myDynamicTwowaySendPort.Name = "myDynamicTwowaySendPort1";  
    $myDynamicTwowaySendPort.SendPipeline = $Catalog.Pipelines["Microsoft.BizTalk.DefaultPipelines.XMLTransmit"];  
    $myDynamicTwowaySendPort.ReceivePipeline = $Catalog.Pipelines["Microsoft.BizTalk.DefaultPipelines.XMLReceive"];  
  
    #=== Persist new ports to BizTalk configuration database ===#  
  
    Write-Host Adding $myStaticOnewaySendPort.Name...  
    Write-Host Adding $myDynamicTwowaySendPort.Name...  
    $catalog.SaveChanges();  
    Write-Host "`r`nCreateSendPorts() completed."  
}  
  
Function DeleteSendPorts($Catalog)  
{  
    #=== Register a trap handler to discard changes on exceptions ===#  
  
    $ErrorActionPreference="silentlycontinue"  
    trap { "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes.`r`n";$Catalog.DiscardChanges();exit; }  
  
    #=== Delete this sample's new send ports by name ===#  
  
    $Catalog.RemoveSendPort($Catalog.SendPorts["myStaticOnewaySendPort1"])  
    $Catalog.RemoveSendPort($Catalog.SendPorts["myDynamicTwowaySendPort1"])  
  
    #=== Persist changes to BizTalk configuration database ===#  
  
    $catalog.SaveChanges();  
    Write-Host "DeleteSendPorts() completed."  
}  
  
Function EnumerateSendPorts($Catalog)  
{  
    #=== Display all send ports and their status info ===#  
  
    $catalog.SendPorts | format-table -Property Name, Status -autosize  
  
    Write-Host "EnumerateSendPorts`(`) completed."  
}  
  
Function ConfigureSendPort($Catalog)  
{  
    #=== Register a trap handler to discard changes on exceptions ===#  
  
    $ErrorActionPreference="silentlycontinue"  
    trap { "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes.`r`n";$Catalog.DiscardChanges();exit; }  
  
    $sendport = $catalog.SendPorts["myStaticOnewaySendPort1"];  
  
    #=== specify tracking settings for tracking ===#  
  
    Write-Host $sendport.Name: Enabling BeforeSendPipeline and AfterSendPipeline message body tracking.  
    $sendport.Tracking = ([Microsoft.BizTalk.ExplorerOM.TrackingTypes] "BeforeSendPipeline" -bor   
                         [Microsoft.BizTalk.ExplorerOM.TrackingTypes] "AfterSendPipeline")  
  
    #=== specify an encryption certificate for outgoing messages ===#  
  
    Write-Host $sendport.Name: Adding a encryption certificate  
    foreach ($certificate in $catalog.Certificates)  
    {  
        if ($certificate.UsageType -eq [Microsoft.BizTalk.ExplorerOM.CertUsageType] "Encryption")  
        {  
            $sendport.EncryptionCert = $certificate  
        }  
    }  
  
    #=== specify filters for content-based routing ===#  
    Write-Host $sendport.Name: Adding a filter  
    $sendport.Filter = "<Filter><Group>" +  
                       "<Statement Property='SMTP.Subject' Operator='0' Value='Purchase Order'/>" +  
                       "<Statement Property='SMTP.From' Operator='0' Value='Customer'/>" +  
                       "</Group></Filter>"  
  
    #=== specify transform maps for document normalization ===#  
  
    foreach ($transform in $catalog.Transforms)  
    {  
        if (($transform.SourceSchema.FullName -ieq "myPO") -and (transform.TargetSchema.FullName -ieq "partnerPO"))  
        {  
            Write-Host $sendport.Name: Adding a transform  
            $sendport.OutboundTransforms.Add($transform)  
        }  
    }  
  
    #=== Persist all changes to BizTalk configuration database ===#  
  
    Write-Host $sendport.Name: Saving changes  
    $catalog.SaveChanges();  
    Write-Host "`r`nConfigureSendPort() completed."  
}  
  
Function ChangeSendPortStatus($Catalog)  
{  
    #=== Register a trap handler to discard changes on exceptions ===#  
  
    $ErrorActionPreference="silentlycontinue"  
    trap { "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes.`r`n";$Catalog.DiscardChanges();exit; }  
  
    $sendport = $catalog.SendPorts["myStaticOnewaySendPort1"];  
  
    #=== start the send port to begin processing messages ===#  
  
    $sendport.Status = [Microsoft.BizTalk.ExplorerOM.PortStatus] "Started"  
    Write-Host Changing ($sendport.Name) status to ($sendport.Status)...  
    $catalog.SaveChanges();  
    Write-Host Complete.  
  
    #=== stop the send port to stop processing and suspend messages ===#  
  
    $sendport.Status = [Microsoft.BizTalk.ExplorerOM.PortStatus] "Stopped"  
    Write-Host Changing ($sendport.Name) status to ($sendport.Status)...  
    $catalog.SaveChanges();  
    Write-Host Complete.  
  
    #=== unenlist the send port to stop processing and discard messages ===#  
  
    $sendport.Status = [Microsoft.BizTalk.ExplorerOM.PortStatus] "Bound"  
    Write-Host Changing ($sendport.Name) status to ($sendport.Status)`(Unenlisted`)...  
    $catalog.SaveChanges();  
    Write-Host Complete.  
}  
  
#=== Main Script Body ===#  
  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect to the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
#=== Exercise the CreateSendPorts function to create the two new ports ===#  
  
Write-Host "`r`n========================="  
Write-Host "=== CreateSendPorts`(`) ==="  
Write-Host "=========================`r`n"  
CreateSendPorts $Catalog  
  
#=== Enumerate all send ports to view the two new ports ===#  
  
Write-Host "`r`n============================"  
Write-Host "=== EnumerateSendPorts`(`) ==="  
Write-Host "============================`r`n"  
EnumerateSendPorts $Catalog  
  
#=== Add some configuration to the static send port ===#  
  
Write-Host "`r`n==========================="  
Write-Host "=== ConfigureSendPort`(`) ==="  
Write-Host "===========================`r`n"  
ConfigureSendPort $Catalog  
  
#=== Cycle through some status changes on the static send port ===#  
  
Write-Host "`r`n=============================="  
Write-Host "=== ChangeSendPortStatus`(`) ==="  
Write-Host "==============================`r`n"  
ChangeSendPortStatus $Catalog  
  
#=== Delete the two new ports ===#  
  
Write-Host "`r`n========================="  
Write-Host "=== DeleteSendPorts`(`) ==="  
Write-Host "=========================`r`n"  
DeleteSendPorts $Catalog  
  
Write-Host  
```  
  
 以下是範例預期從執行 Windows PowerShell 指令碼範例的輸出。  
  
```  
PS C:\> & 'C:\SendPorts.ps1'  
  
=========================  
=== CreateSendPorts() ===  
=========================  
  
Adding myStaticOnewaySendPort1 ...  
Adding myDynamicTwowaySendPort1 ...  
  
CreateSendPorts() completed.  
  
============================  
=== EnumerateSendPorts() ===  
============================  
  
Name                      Status  
----                      ------  
ResendPort               Started  
HelloWorldSendPort       Started  
ToCustomerSendPort       Started  
CBRUSSendPort            Started  
CBRCANSendPort           Started  
SendportCANOrders          Bound  
myStaticOnewaySendPort1    Bound  
myDynamicTwowaySendPort1   Bound  
  
EnumerateSendPorts() completed.  
  
===========================  
=== ConfigureSendPort() ===  
===========================  
  
myStaticOnewaySendPort1 : Enabling BeforeSendPipeline and AfterSendPipeline message body tracking.  
myStaticOnewaySendPort1 : Adding a encryption certificate  
myStaticOnewaySendPort1 : Adding a filter  
myStaticOnewaySendPort1 : Saving changes  
  
ConfigureSendPort() completed.  
  
==============================  
=== ChangeSendPortStatus() ===  
==============================  
  
Changing myStaticOnewaySendPort1 status to Started ...  
Complete.  
Changing myStaticOnewaySendPort1 status to Stopped ...  
Complete.  
Changing myStaticOnewaySendPort1 status to Bound (Unenlisted)...  
Complete.  
  
=========================  
=== DeleteSendPorts() ===  
=========================  
  
DeleteSendPorts() completed.  
```  
  
## <a name="see-also"></a>請參閱  
 [Admin-ExplorerOM (BizTalk Server Samples 資料夾)](../core/admin-explorerom-biztalk-server-samples-folder.md)