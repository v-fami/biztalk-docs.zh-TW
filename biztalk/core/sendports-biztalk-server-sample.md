---
title: SendPorts （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b84f96a2-b749-4fe0-be15-e4dd13eff66f
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac6ef809104e1ce11385cb88d94547d0de496af1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009903"
---
# <a name="sendports-biztalk-server-sample"></a><span data-ttu-id="91775-102">SendPorts （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="91775-102">SendPorts (BizTalk Server Sample)</span></span>
<span data-ttu-id="91775-103">SendPorts 範例示範如何列舉使用和管理傳送埠**Microsoft.BizTalk.ExplorerOM**管理類別。</span><span class="sxs-lookup"><span data-stu-id="91775-103">The SendPorts sample demonstrates how to enumerate and manage send ports by using the **Microsoft.BizTalk.ExplorerOM** administration classes.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="91775-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="91775-104">Prerequisites</span></span>  

- <span data-ttu-id="91775-105">您必須擁有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理權限才能在此範例中使用的系統管理物件。</span><span class="sxs-lookup"><span data-stu-id="91775-105">You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.</span></span>  

- <span data-ttu-id="91775-106">Windows PowerShell 指令碼需要 Windows PowerShell 執行原則，以允許執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="91775-106">The Windows PowerShell script requires the Windows PowerShell execution policy to allow script execution.</span></span> <span data-ttu-id="91775-107">如需詳細資訊，請參閱：[檢查執行原則](http://go.microsoft.com/fwlink/?LinkId=128930)。</span><span class="sxs-lookup"><span data-stu-id="91775-107">For more information see: [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).</span></span>  

## <a name="what-this-sample-does"></a><span data-ttu-id="91775-108">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="91775-108">What This Sample Does</span></span>  
 <span data-ttu-id="91775-109">此範例示範如何使用**BtsCatalogExplorer**並**SendPort**類別**Microsoft.BizTalk.ExplorerOM** 中的命名空間來管理傳送埠[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="91775-109">This sample demonstrates using the **BtsCatalogExplorer** and **SendPort** classes from the **Microsoft.BizTalk.ExplorerOM** namespace to manage send ports in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span> <span data-ttu-id="91775-110">此範例以 Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="91775-110">The sample is written in Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)].</span></span> <span data-ttu-id="91775-111">本主題也包含 Windows PowerShell 範例指令碼。</span><span class="sxs-lookup"><span data-stu-id="91775-111">A Windows PowerShell example script is also included in this topic.</span></span> <span data-ttu-id="91775-112">此範例會示範下列作業：</span><span class="sxs-lookup"><span data-stu-id="91775-112">The sample demonstrates the following operations:</span></span>  

1. <span data-ttu-id="91775-113">使用連接到 「 BizTalk 管理 」 資料庫**BtsCatalogExplorer**類別。</span><span class="sxs-lookup"><span data-stu-id="91775-113">Connecting to the BizTalk Management database by using the **BtsCatalogExplorer** class.</span></span>  

2. <span data-ttu-id="91775-114">建立兩個新的傳送埠，名為 myStaticOnewaySendPort1 和 myDynamicTwowaySendPort1。</span><span class="sxs-lookup"><span data-stu-id="91775-114">Creating two new send ports named myStaticOnewaySendPort1 and myDynamicTwowaySendPort1.</span></span> <span data-ttu-id="91775-115">myStaticOnewaySendPort1，正如其名，都是靜態的單向傳送埠。</span><span class="sxs-lookup"><span data-stu-id="91775-115">myStaticOnewaySendPort1, as its name implies, is a static one-way send port.</span></span>  <span data-ttu-id="91775-116">它會建立以範例目的地 url 使用 HTTP 傳輸 http://sample1 。</span><span class="sxs-lookup"><span data-stu-id="91775-116">It is created to use the HTTP transport with an example destination URL http://sample1.</span></span> <span data-ttu-id="91775-117">myDynamicTwowaySendPort1 會建立為動態的雙向傳送埠。</span><span class="sxs-lookup"><span data-stu-id="91775-117">myDynamicTwowaySendPort1 is created as a dynamic two-way send port.</span></span>  

3. <span data-ttu-id="91775-118">列舉中的傳送埠[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="91775-118">Enumerating send ports in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span> <span data-ttu-id="91775-119">這個範例列舉型別應該包含兩個新的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="91775-119">This example enumeration should include the two new send ports.</span></span>  

4. <span data-ttu-id="91775-120">正在刪除兩個新的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="91775-120">Deleting the two new send ports.</span></span>  

5. <span data-ttu-id="91775-121">設定新的傳送埠。</span><span class="sxs-lookup"><span data-stu-id="91775-121">Configuring the new send ports.</span></span> <span data-ttu-id="91775-122">此範例所示範的設定會套用至名為 myStaticOnewaySendPort1 範例傳送埠。</span><span class="sxs-lookup"><span data-stu-id="91775-122">The configurations demonstrated by the sample are applied to the example send port named myStaticOnewaySendPort1.</span></span> <span data-ttu-id="91775-123">下列範例所套用的設定：</span><span class="sxs-lookup"><span data-stu-id="91775-123">The configurations applied by the sample include the following:</span></span>  

   -   <span data-ttu-id="91775-124">啟用**連接埠處理前的要求訊息**追蹤訊息內文的選項。</span><span class="sxs-lookup"><span data-stu-id="91775-124">Enabling the **Request message before port processing** option for tracking message bodies.</span></span>  

   -   <span data-ttu-id="91775-125">啟用**連接埠處理後的要求訊息**追蹤訊息內文的選項。</span><span class="sxs-lookup"><span data-stu-id="91775-125">Enabling the **Request message after port processing** option for tracking message bodies.</span></span>  

   -   <span data-ttu-id="91775-126">指定用於外寄訊息的傳送埠加密憑證。</span><span class="sxs-lookup"><span data-stu-id="91775-126">Specifying an encryption certificate for the send port to use on outgoing messages.</span></span>  

   -   <span data-ttu-id="91775-127">指定針對一組訊息的登記的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="91775-127">Specifying a filter for enlistment against a set of messages.</span></span>  

   -   <span data-ttu-id="91775-128">新增對應來轉換訊息。</span><span class="sxs-lookup"><span data-stu-id="91775-128">Adding a map to transform the messages.</span></span>  

6. <span data-ttu-id="91775-129">變更兩個新的傳送埠上的傳送埠狀態。</span><span class="sxs-lookup"><span data-stu-id="91775-129">Changing send port status on the two new send ports.</span></span>  <span data-ttu-id="91775-130">執行此範例會對 myStaticOnewaySendPort1 下列的狀態變更：</span><span class="sxs-lookup"><span data-stu-id="91775-130">The execution of the sample will make the following status changes on the myStaticOnewaySendPort1:</span></span>  

   -   <span data-ttu-id="91775-131">將狀態變更為已啟動。</span><span class="sxs-lookup"><span data-stu-id="91775-131">Change the status to started.</span></span>  

   -   <span data-ttu-id="91775-132">將狀態變更為已停止。</span><span class="sxs-lookup"><span data-stu-id="91775-132">Change the status to stopped.</span></span>  

   -   <span data-ttu-id="91775-133">將狀態變更為繫結。</span><span class="sxs-lookup"><span data-stu-id="91775-133">Change the status to bound.</span></span> <span data-ttu-id="91775-134">繫結的狀態相當於取消登錄。</span><span class="sxs-lookup"><span data-stu-id="91775-134">The bound status is the same as unenlisted.</span></span>  

## <a name="where-to-find-this-sample"></a><span data-ttu-id="91775-135">此範例的位置</span><span class="sxs-lookup"><span data-stu-id="91775-135">Where To Find This Sample</span></span>  
 <span data-ttu-id="91775-136">這個範例位於下列 SDK 位置：</span><span class="sxs-lookup"><span data-stu-id="91775-136">The sample is located in the following SDK location:</span></span>  

 <span data-ttu-id="91775-137">\<*範例路徑*\>\Admin\ExplorerOM\SendPorts</span><span class="sxs-lookup"><span data-stu-id="91775-137">\<*Samples Path*\>\Admin\ExplorerOM\SendPorts</span></span>  

 <span data-ttu-id="91775-138">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="91775-138">The following table shows the files in this sample and describes their purpose.</span></span>  


|                    <span data-ttu-id="91775-139">檔案</span><span class="sxs-lookup"><span data-stu-id="91775-139">File(s)</span></span>                     |                                                 <span data-ttu-id="91775-140">描述</span><span class="sxs-lookup"><span data-stu-id="91775-140">Description</span></span>                                                  |
|------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
|                  <span data-ttu-id="91775-141">SendPorts.cs</span><span class="sxs-lookup"><span data-stu-id="91775-141">SendPorts.cs</span></span>                  | [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]<span data-ttu-id="91775-142"> 此範例中示範的作業的原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="91775-142"> source file for operations demonstrated in this sample.</span></span> |
| <span data-ttu-id="91775-143">SendPorts.sln，SendPorts.csproj，SendPorts.suo</span><span class="sxs-lookup"><span data-stu-id="91775-143">SendPorts.sln, SendPorts.csproj, SendPorts.suo</span></span> |                                  <span data-ttu-id="91775-144">此範例的方案和專案檔。</span><span class="sxs-lookup"><span data-stu-id="91775-144">Solution and project files for the sample.</span></span>                                  |

## <a name="building-and-running-this-sample"></a><span data-ttu-id="91775-145">建置和執行此範例</span><span class="sxs-lookup"><span data-stu-id="91775-145">Building and Running This Sample</span></span>  

#### <a name="to-build-this-sample"></a><span data-ttu-id="91775-146">建置此範例</span><span class="sxs-lookup"><span data-stu-id="91775-146">To build this sample</span></span>  

1. <span data-ttu-id="91775-147">在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟方案檔 SendPorts.sln。</span><span class="sxs-lookup"><span data-stu-id="91775-147">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file SendPorts.sln.</span></span>  

2. <span data-ttu-id="91775-148">在主功能表中，按一下 **建置**，然後按一下**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="91775-148">On the main menu, click **Build**, and then click **Build Solution**.</span></span>  

#### <a name="to-run-this-sample"></a><span data-ttu-id="91775-149">執行此範例</span><span class="sxs-lookup"><span data-stu-id="91775-149">To run this sample</span></span>  

1.  <span data-ttu-id="91775-150">開啟命令視窗並巡覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="91775-150">Open a command window and navigate to the following folder:</span></span>  

     <span data-ttu-id="91775-151">\<*範例路徑*\>\Admin\ExplorerOM\SendPorts\bin\Debug</span><span class="sxs-lookup"><span data-stu-id="91775-151">\<*Samples Path*\>\Admin\ExplorerOM\SendPorts\bin\Debug</span></span>  

2.  <span data-ttu-id="91775-152">執行檔案 SendPorts.exe。</span><span class="sxs-lookup"><span data-stu-id="91775-152">Run the file SendPorts.exe.</span></span>  

## <a name="windows-powershell-script-example"></a><span data-ttu-id="91775-153">Windows PowerShell 指令碼範例</span><span class="sxs-lookup"><span data-stu-id="91775-153">Windows PowerShell Script Example</span></span>  
 <span data-ttu-id="91775-154">下列 Windows PowerShell 指令碼片段，可以用來示範相同的功能**ExplorerOM**類別：</span><span class="sxs-lookup"><span data-stu-id="91775-154">The following Windows PowerShell script fragment can be used to demonstrate the same features of the **ExplorerOM** classes:</span></span>  

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

 <span data-ttu-id="91775-155">以下是從執行 Windows PowerShell 指令碼範例的範例預期輸出。</span><span class="sxs-lookup"><span data-stu-id="91775-155">Here is example expected output from running the Windows PowerShell script sample.</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="91775-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="91775-156">See Also</span></span>  
 [<span data-ttu-id="91775-157">Admin-ExplorerOM (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="91775-157">Admin-ExplorerOM (BizTalk Server Samples Folder)</span></span>](../core/admin-explorerom-biztalk-server-samples-folder.md)