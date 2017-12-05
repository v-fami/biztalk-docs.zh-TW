---
title: "ReceiveLocations （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87d75941-3973-4166-91b0-f1192b25a804
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b5b1a6d6b651ea07430f67667a17029dfe162d4d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="receivelocations-biztalk-server-sample"></a><span data-ttu-id="3e6c9-102">ReceiveLocations （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="3e6c9-102">ReceiveLocations (BizTalk Server Sample)</span></span>
<span data-ttu-id="3e6c9-103">ReceiveLocations 範例示範如何建立接收位置中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境使用**ExplorerOM**管理物件。</span><span class="sxs-lookup"><span data-stu-id="3e6c9-103">The ReceiveLocations sample demonstrates how to create receive locations in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment by using the **ExplorerOM** administration objects.</span></span> <span data-ttu-id="3e6c9-104">如需有關一般接收位置，請參閱[接收位置](../core/receive-locations.md)。</span><span class="sxs-lookup"><span data-stu-id="3e6c9-104">For more information about receive locations in general, see [Receive Locations](../core/receive-locations.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="3e6c9-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="3e6c9-105">Prerequisites</span></span>  
  
-   <span data-ttu-id="3e6c9-106">您必須擁有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在此範例中使用的系統管理物件的系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="3e6c9-106">You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.</span></span>  
  
-   <span data-ttu-id="3e6c9-107">Windows PowerShell 指令碼需要 Windows PowerShell 執行原則以允許執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="3e6c9-107">The Windows PowerShell script requires the Windows PowerShell execution policy to allow script execution.</span></span> <span data-ttu-id="3e6c9-108">如需詳細資訊，請參閱 [檢查執行原則](http://go.microsoft.com/fwlink/?LinkId=128930)。</span><span class="sxs-lookup"><span data-stu-id="3e6c9-108">For more information see [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="3e6c9-109">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="3e6c9-109">What This Sample Does</span></span>  
 <span data-ttu-id="3e6c9-110">這個範例示範如何使用**ExplorerOM**系統管理類別來建立及設定接收埠和接收位置。</span><span class="sxs-lookup"><span data-stu-id="3e6c9-110">This sample demonstrates using the **ExplorerOM** administrative classes to create and configure receive ports and receive locations.</span></span> <span data-ttu-id="3e6c9-111">本主題也包含 Windows PowerShell 範例指令碼。</span><span class="sxs-lookup"><span data-stu-id="3e6c9-111">A Windows PowerShell example script is also included in this topic.</span></span> <span data-ttu-id="3e6c9-112">此範例會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="3e6c9-112">The sample performs the following operations:</span></span>  
  
-   <span data-ttu-id="3e6c9-113">建立新接收埠命名為 「 我的接收埠 」。</span><span class="sxs-lookup"><span data-stu-id="3e6c9-113">Create a new receive port named “My Receive Port”.</span></span>  
  
-   <span data-ttu-id="3e6c9-114">建立新接收位置與新的連接埠相關聯，而且設定為使用 HTTP 傳輸通訊協定。</span><span class="sxs-lookup"><span data-stu-id="3e6c9-114">Create a new receive location associated with the new port and configured to use the HTTP transport protocol.</span></span>  
  
-   <span data-ttu-id="3e6c9-115">此範例也包含範例程序來刪除，並列舉接收埠和位置。</span><span class="sxs-lookup"><span data-stu-id="3e6c9-115">This sample also contains example procedures to delete and enumerate receive ports and locations.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="3e6c9-116">此範例的位置</span><span class="sxs-lookup"><span data-stu-id="3e6c9-116">Where To Find This Sample</span></span>  
 <span data-ttu-id="3e6c9-117">這個範例位於下列 SDK 位置：</span><span class="sxs-lookup"><span data-stu-id="3e6c9-117">This sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="3e6c9-118">\<*範例路徑*\> \Admin\ExplorerOM\ReceiveLocations</span><span class="sxs-lookup"><span data-stu-id="3e6c9-118">\<*Samples Path*\> \Admin\ExplorerOM\ReceiveLocations</span></span>  
  
 <span data-ttu-id="3e6c9-119">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="3e6c9-119">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="3e6c9-120">檔案</span><span class="sxs-lookup"><span data-stu-id="3e6c9-120">File(s)</span></span>|<span data-ttu-id="3e6c9-121">Description</span><span class="sxs-lookup"><span data-stu-id="3e6c9-121">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3e6c9-122">ReceiveLocations.cs</span><span class="sxs-lookup"><span data-stu-id="3e6c9-122">ReceiveLocations.cs</span></span>|[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]<span data-ttu-id="3e6c9-123">這個範例中示範的作業的來源檔案。</span><span class="sxs-lookup"><span data-stu-id="3e6c9-123"> source file for the operations demonstrated in this sample.</span></span>|  
|<span data-ttu-id="3e6c9-124">ReceiveLocations.sln 和 ReceiveLocations.csproj</span><span class="sxs-lookup"><span data-stu-id="3e6c9-124">ReceiveLocations.sln and ReceiveLocations.csproj</span></span>|<span data-ttu-id="3e6c9-125">此範例的方案和專案檔。</span><span class="sxs-lookup"><span data-stu-id="3e6c9-125">Solution and project files for this sample.</span></span>|  
  
## <a name="building-and-running-this-sample"></a><span data-ttu-id="3e6c9-126">建置和執行此範例</span><span class="sxs-lookup"><span data-stu-id="3e6c9-126">Building and Running This Sample</span></span>  
  
#### <a name="to-build-this-sample"></a><span data-ttu-id="3e6c9-127">建置此範例</span><span class="sxs-lookup"><span data-stu-id="3e6c9-127">To build this sample</span></span>  
  
1.  <span data-ttu-id="3e6c9-128">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟方案檔 ReceiveLocations.sln。</span><span class="sxs-lookup"><span data-stu-id="3e6c9-128">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file ReceiveLocations.sln.</span></span>  
  
2.  <span data-ttu-id="3e6c9-129">按一下 [ **建置** ] 功能表上的 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="3e6c9-129">On the **Build** menu, click **Build Solution**.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="3e6c9-130">執行此範例</span><span class="sxs-lookup"><span data-stu-id="3e6c9-130">To run this sample</span></span>  
  
1.  <span data-ttu-id="3e6c9-131">開啟命令提示字元，使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="3e6c9-131">Open a command prompt with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges.</span></span>  
  
2.  <span data-ttu-id="3e6c9-132">若要變更\<*範例*\>\Admin\ExplorerOM\ReceiveLocations\bin\debug 目錄。</span><span class="sxs-lookup"><span data-stu-id="3e6c9-132">Change to the \<*Samples*\>\Admin\ExplorerOM\ReceiveLocations\bin\debug directory.</span></span>  
  
3.  <span data-ttu-id="3e6c9-133">執行 ReceiveLocations.exe。</span><span class="sxs-lookup"><span data-stu-id="3e6c9-133">Run ReceiveLocations.exe.</span></span>  
  
4.  <span data-ttu-id="3e6c9-134">檢視新的接收埠和接收位置與[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="3e6c9-134">View the new receive port and receive location with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
## <a name="windows-powershell-script-example"></a><span data-ttu-id="3e6c9-135">Windows PowerShell 指令碼範例</span><span class="sxs-lookup"><span data-stu-id="3e6c9-135">Windows PowerShell Script Example</span></span>  
 <span data-ttu-id="3e6c9-136">下列 PowerShell 範例指令碼示範如何為相同的作業[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]版本。</span><span class="sxs-lookup"><span data-stu-id="3e6c9-136">The following PowerShell example script demonstrates the same operations as the [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] version.</span></span> <span data-ttu-id="3e6c9-137">請確定指令碼執行原則已正確設定本主題中的需求 > 一節中所述。</span><span class="sxs-lookup"><span data-stu-id="3e6c9-137">Make sure the script execution policy has been properly configured as mentioned in the requirements section of this topic.</span></span>  
  
```  
#==================================================================#  
#===                                                            ===#  
#=== Create a new receive port named "My Receive Port" as an    ===#  
#=== example.                                                   ===#  
#===                                                            ===#  
#=== A new receive location will also be created and associated ===#  
#=== with the receive port.                                     ===#  
#===                                                            ===#  
#==================================================================#  
Function CreateAndConfigureReceiveLocation()  
{  
   $myreceivePort = $catalog.AddNewReceivePort($false)  
  
   #=== Note that if you don’t set the name property for the receieve port, ===#  
   #=== it will create a new receive location and add it to the receive     ===#     
   #=== port.                                                               ===#  
  
   $myreceivePort.Name = "My Receive Port"  
  
   #=== Create a new receive location and add it to the receive port ===#  
   $myreceiveLocation = $myreceivePort.AddNewReceiveLocation()  
  
   foreach ($handler in $catalog.ReceiveHandlers)  
   {  
      if ($handler.TransportType.Name -eq "HTTP")  
      {  
         $myreceiveLocation.ReceiveHandler = $handler  
         break  
      }  
   }  
  
   #=== Associate a transport protocol and URI with the receive location. ===#   
   $myreceiveLocation.TransportType = $catalog.ProtocolTypes["HTTP"]  
   $myreceiveLocation.Address = "/home"  
  
   #=== Assign the first receive pipeline found to process the message. ===#  
   foreach ($pipeline in $catalog.Pipelines)  
   {  
      if ($pipeline.Type -eq [Microsoft.Biztalk.ExplorerOM.PipelineType] "Receive")  
      {  
         $myreceiveLocation.ReceivePipeline = $pipeline  
         break  
      }  
  
      #=== Enable the receive location. ===#  
      $myreceiveLocation.Enable = $true  
  
      #=== Optional Properties ===#  
      $myreceiveLocation.FragmentMessages = [Microsoft.BizTalk.ExplorerOM.Fragmentation] "Yes"  
      $myreceiveLocation.ServiceWindowEnabled = $false    
   }  
  
    #=== Try to commit the changes made so far. If the commit fails, ===#  
    #=== roll back all changes.                                      ===#  
    $catalog.SaveChanges()  
}  
  
#===============================================================#  
#===                                                         ===#  
#=== Delete the receive port named "My Receive Port"         ===#  
#===                                                         ===#  
#===============================================================#  
Function DeleteReceivePort  
{  
  $receivePort = $catalog.ReceivePorts["My Receive Port"]  
  
  if ($receivePort -ne $null)  
  {  
  
    #=== Enumerate the receive locations. ===#  
    foreach ($location in $receivePort.ReceiveLocations)  
    {  
        if (($location.Name -eq "Receive Location1") -and ($location.IsPrimary -eq $false))  
        {  
          $receivePort.RemoveReceiveLocation($location)  
        }  
    }  
  
    $catalog.RemoveReceivePort($receivePort)    
  
    #=== Try to commit the changes made so far. If the commit fails, ===#  
    #=== roll back all changes in the trap handler.                  ===#  
    $catalog.SaveChanges()  
  }  
}  
  
#================================================================#  
#===                                                          ===#  
#=== Enumerate the receive ports and their receive locations. ===#  
#===                                                          ===#  
#================================================================#  
Function EnumerateReceiveLocations  
{  
   #=== Enumerate the receive locations in each of the receive ports. ===#  
   foreach ($receivePort in $catalog.ReceivePorts)  
   {  
      Write-host "`r`n$($receivePort.Name)"  
  
      #=== Enumerate the receive locations. ===#  
      foreach ($location in $receivePort.ReceiveLocations)  
      {  
         Write-Host "`t$($location.Name)"  
      }  
   }  
  
   Write-host ""  
}  
  
#===================#  
#=== Main Script ===#  
#===================#  
  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect to the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
#==================================================================#  
#=== Register a trap handler to discard changes on exceptions   ===#  
#=== Execution will continue in the event we want to delete the ===#  
#=== receive port.                                              ===#  
#==================================================================#  
  
$Script:NoExceptionOccurred = $true  
$ErrorActionPreference="silentlycontinue"  
trap   
{   
  $Script:NoExceptionOccurred = $false  
  "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes and continuing execution so we can attempt to clean up the receive port...`r`n"  
  $Catalog.DiscardChanges()  
}  
  
#=== Create the new receive port with its new receive location ===#  
CreateAndConfigureReceiveLocation  
Write-Host "`r`n`"My Receive Port`" created."  
  
#=== Enumerate each receive port along with its receive locations ===#  
Write-Host "`r`nEnumerating all receive ports...`r`n"  
EnumerateReceiveLocations  
  
#=== Prompt before removing the new example receive port and location ===#  
Write-Host "`r`nPress <ENTER> to delete `"My Receive Port`"..."  
Read-Host  
DeleteReceivePort  
  
#=== Enumerate again to show the receive port and location was removed ===#  
Write-Host "`r`nEnumerating all receive ports to show `"My Receive Port`" was removed...`r`n"  
EnumerateReceiveLocations  
  
```  
  
 <span data-ttu-id="3e6c9-138">以下是範例輸出顯示接收埠和位置正在建立並刪除 PowerShell 指令碼執行：</span><span class="sxs-lookup"><span data-stu-id="3e6c9-138">Here is example output from the PowerShell script execution showing the receive port and location being created and deleted:</span></span>  
  
```  
PS C:\> .\ReceiveLocations.ps1  
  
"My Receive Port" created.  
  
Enumerating all receive ports...  
  
BatchControlMessageRecvPort  
        BatchControlMessageRecvLoc  
  
ResendReceivePort  
        ResendReceiveLocation  
  
HelloWorldReceivePort  
        HelloWorldReceiveLocation  
  
CBRReceivePort  
        CBRReceiveLocation  
  
RP_ReceivePOFromInternal  
        RL_ReceivePOFromInternal  
  
RP_ShipmentAgency1_OrderFiles  
        RL_ShipmentAgency1_OrderFiles  
  
RP_ShipmentAgency2_OrderFiles  
        RL_ShipmentAgency2_OrderFiles  
  
RP_ReceivePOFromBuyer  
        RL_ReceivePOFromBuyer  
  
RP_Receive_ShipmentAgency_Ack  
        RL_Receive_ShipmentAgency_Ack  
  
My Receive Port  
        Receive Location1  
  
Press <ENTER> to delete "My Receive Port"...  
  
Enumerating all receive ports to show "My Receive Port" was removed...  
  
BatchControlMessageRecvPort  
        BatchControlMessageRecvLoc  
  
ResendReceivePort  
        ResendReceiveLocation  
  
HelloWorldReceivePort  
        HelloWorldReceiveLocation  
  
CBRReceivePort  
        CBRReceiveLocation  
  
RP_ReceivePOFromInternal  
        RL_ReceivePOFromInternal  
  
RP_ShipmentAgency1_OrderFiles  
        RL_ShipmentAgency1_OrderFiles  
  
RP_ShipmentAgency2_OrderFiles  
        RL_ShipmentAgency2_OrderFiles  
  
RP_ReceivePOFromBuyer  
        RL_ReceivePOFromBuyer  
  
RP_Receive_ShipmentAgency_Ack  
        RL_Receive_ShipmentAgency_Ack  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e6c9-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="3e6c9-139">See Also</span></span>  
 <span data-ttu-id="3e6c9-140">[接收位置](../core/receive-locations.md) </span><span class="sxs-lookup"><span data-stu-id="3e6c9-140">[Receive Locations](../core/receive-locations.md) </span></span>  
 [<span data-ttu-id="3e6c9-141">Admin-ExplorerOM (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="3e6c9-141">Admin-ExplorerOM (BizTalk Server Samples Folder)</span></span>](../core/admin-explorerom-biztalk-server-samples-folder.md)