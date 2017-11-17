---
title: "接收埠 （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c403005d-5e0e-4015-b138-6318e03192af
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cb14221ba11fe514ab076dd6bad8cc0aeb5b929e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="receiveports-biztalk-server-sample"></a><span data-ttu-id="13c7b-102">接收埠 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="13c7b-102">ReceivePorts (BizTalk Server Sample)</span></span>
<span data-ttu-id="13c7b-103">接收埠 」 範例示範如何建立新接收埠使用**ExplorerOM**系統管理類別。</span><span class="sxs-lookup"><span data-stu-id="13c7b-103">The ReceivePorts sample demonstrates how to create a new receive port by using the **ExplorerOM** administrative classes.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="13c7b-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="13c7b-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="13c7b-105">您必須擁有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在此範例中使用的系統管理物件的系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="13c7b-105">You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.</span></span>  
  
-   <span data-ttu-id="13c7b-106">Windows PowerShell 指令碼需要 Windows PowerShell 執行原則以允許執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="13c7b-106">The Windows PowerShell script requires the Windows PowerShell execution policy to allow script execution.</span></span> <span data-ttu-id="13c7b-107">如需詳細資訊，請參閱 [檢查執行原則](http://go.microsoft.com/fwlink/?LinkId=128930)。</span><span class="sxs-lookup"><span data-stu-id="13c7b-107">For more information see [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="13c7b-108">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="13c7b-108">What This Sample Does</span></span>  
 <span data-ttu-id="13c7b-109">這個範例示範如何使用**BtsCatalogExplorer**和**ReceivePort**類別**Microsoft.BizTalk.ExplorerOM**命名空間，將新接收埠[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="13c7b-109">This sample demonstrates using the **BtsCatalogExplorer** and **ReceivePort** classes from the **Microsoft.BizTalk.ExplorerOM** namespace to add a new receive port to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="13c7b-110">此範例以 Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="13c7b-110">The sample is written in Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)].</span></span> <span data-ttu-id="13c7b-111">本主題也包含 Windows PowerShell 範例指令碼。</span><span class="sxs-lookup"><span data-stu-id="13c7b-111">A Windows PowerShell example script is also included in this topic.</span></span> <span data-ttu-id="13c7b-112">此範例會示範下列作業：</span><span class="sxs-lookup"><span data-stu-id="13c7b-112">The sample demonstrates the following operations:</span></span>  
  
-   <span data-ttu-id="13c7b-113">使用連接到 「 BizTalk 管理 」 資料庫**BtsCatalogExplorer**類別。</span><span class="sxs-lookup"><span data-stu-id="13c7b-113">Connecting to the BizTalk Management database by using the **BtsCatalogExplorer** class.</span></span>  
  
-   <span data-ttu-id="13c7b-114">加入新接收埠使用**AddNewReceivePort**方法。</span><span class="sxs-lookup"><span data-stu-id="13c7b-114">Adding a new receive port by using the **AddNewReceivePort** method.</span></span>  
  
-   <span data-ttu-id="13c7b-115">列舉接收埠。</span><span class="sxs-lookup"><span data-stu-id="13c7b-115">Enumerating receive ports.</span></span>  
  
-   <span data-ttu-id="13c7b-116">刪除接收埠。</span><span class="sxs-lookup"><span data-stu-id="13c7b-116">Deleting receive ports.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="13c7b-117">此範例的位置</span><span class="sxs-lookup"><span data-stu-id="13c7b-117">Where To Find This Sample</span></span>  
 <span data-ttu-id="13c7b-118">這個範例位於下列 SDK 位置：</span><span class="sxs-lookup"><span data-stu-id="13c7b-118">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="13c7b-119">\<*範例路徑*> \Admin\ExplorerOM\ReceivePorts</span><span class="sxs-lookup"><span data-stu-id="13c7b-119">\<*Samples Path*>\Admin\ExplorerOM\ReceivePorts</span></span>  
  
 <span data-ttu-id="13c7b-120">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="13c7b-120">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="13c7b-121">檔案</span><span class="sxs-lookup"><span data-stu-id="13c7b-121">File(s)</span></span>|<span data-ttu-id="13c7b-122">Description</span><span class="sxs-lookup"><span data-stu-id="13c7b-122">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="13c7b-123">ReceivePorts.cs</span><span class="sxs-lookup"><span data-stu-id="13c7b-123">ReceivePorts.cs</span></span>|[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]<span data-ttu-id="13c7b-124">這個範例中示範的作業的來源檔案。</span><span class="sxs-lookup"><span data-stu-id="13c7b-124"> source file for operations demonstrated in this sample.</span></span>|  
|<span data-ttu-id="13c7b-125">ReceivePorts.sln 和 ReceivePorts.csproj</span><span class="sxs-lookup"><span data-stu-id="13c7b-125">ReceivePorts.sln and ReceivePorts.csproj</span></span>|<span data-ttu-id="13c7b-126">此範例的方案和專案檔案。</span><span class="sxs-lookup"><span data-stu-id="13c7b-126">Solution and project file for the sample.</span></span>|  
  
## <a name="building-and-running-this-sample"></a><span data-ttu-id="13c7b-127">建置和執行此範例</span><span class="sxs-lookup"><span data-stu-id="13c7b-127">Building and Running This Sample</span></span>  
  
#### <a name="to-build-this-sample"></a><span data-ttu-id="13c7b-128">建置此範例</span><span class="sxs-lookup"><span data-stu-id="13c7b-128">To build this sample</span></span>  
  
1.  <span data-ttu-id="13c7b-129">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟方案檔 ReceivePorts.sln。</span><span class="sxs-lookup"><span data-stu-id="13c7b-129">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file ReceivePorts.sln.</span></span>  
  
2.  <span data-ttu-id="13c7b-130">按一下 [ **建置** ] 功能表上的 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="13c7b-130">On the **Build** menu, click **Build Solution**.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="13c7b-131">執行此範例</span><span class="sxs-lookup"><span data-stu-id="13c7b-131">To run this sample</span></span>  
  
1.  <span data-ttu-id="13c7b-132">開啟命令視窗並巡覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="13c7b-132">Open a command window and navigate to the following folder:</span></span>  
  
     <span data-ttu-id="13c7b-133">\<*範例路徑*> \Admin\ExplorerOM\ReceivePorts\bin\Debug</span><span class="sxs-lookup"><span data-stu-id="13c7b-133">\<*Samples Path*>\Admin\ExplorerOM\ReceivePorts\bin\Debug</span></span>  
  
2.  <span data-ttu-id="13c7b-134">執行檔案 ReceivePorts.exe。</span><span class="sxs-lookup"><span data-stu-id="13c7b-134">Run the file ReceivePorts.exe.</span></span> <span data-ttu-id="13c7b-135">新的接收埠應該建立在程式碼中，連接埠列舉所示。</span><span class="sxs-lookup"><span data-stu-id="13c7b-135">The new receive port should be created and shown in the port enumeration.</span></span> <span data-ttu-id="13c7b-136">列舉型別之後會立即移除接收埠。</span><span class="sxs-lookup"><span data-stu-id="13c7b-136">After the enumeration the receive port is immediately removed.</span></span>  
  
## <a name="windows-powershell-script-example"></a><span data-ttu-id="13c7b-137">Windows PowerShell 指令碼範例</span><span class="sxs-lookup"><span data-stu-id="13c7b-137">Windows PowerShell Script Example</span></span>  
 <span data-ttu-id="13c7b-138">下列 Windows PowerShell 範例指令碼可以用於示範的相同功能**ExplorerOM**類別：</span><span class="sxs-lookup"><span data-stu-id="13c7b-138">The following Windows PowerShell example script can be used to demonstrate the same features of the **ExplorerOM** classes:</span></span>  
  
```  
#==================================================================#  
#===                                                            ===#  
#=== Create a new receive port named "My Receive Port".         ===#  
#===                                                            ===#  
#==================================================================#  
Function CreateReceivePort()  
{   
  #=== Passing false here creates a one-way receive port opposed to a two-way ===#  
  $myreceivePort = $catalog.AddNewReceivePort($false)  
  
  $myreceivePort.Name = "My Receive Port"  
  $myreceivePort.Tracking = [Microsoft.BizTalk.ExplorerOM.TrackingTypes] "AfterReceivePipeline"  
  
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
    $catalog.RemoveReceivePort($receivePort)    
  
    #=== Try to commit the changes made so far. If the commit fails, ===#  
    #=== roll back all changes in the trap handler.                  ===#  
    $catalog.SaveChanges()  
  }  
}  
  
#================================================================#  
#===                                                          ===#  
#=== Enumerate the receive ports.                             ===#  
#===                                                          ===#  
#================================================================#  
Function EnumerateReceivePorts  
{  
   #=== Enumerate the receive ports. ===#  
   foreach ($receivePort in $catalog.ReceivePorts)  
   {  
      Write-host "`r`n$($receivePort.Name)"  
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
  "Exception encountered:`r`n"; $_; "`r`nDiscarding changes and continuing execution so we can attempt to clean up the receive port...`r`n"  
  $Catalog.DiscardChanges()  
}  
  
#=== Create the new receive port ===#  
Write-Host "`r`nAttempting to create `"My Receive Port`"..."  
CreateReceivePort  
  
#=== Enumerate each receive port ===#  
Write-Host "`r`nEnumerating all receive ports...`r`n"  
EnumerateReceivePorts  
  
#=== Prompt before removing the new example receive port ===#  
Write-Host "`r`nPress <ENTER> to delete `"My Receive Port`"..."  
Read-Host  
DeleteReceivePort  
  
#=== Enumerate again to show the receive port was removed ===#  
Write-Host "`r`nEnumerating all receive ports to show `"My Receive Port`" was removed...`r`n"  
EnumerateReceivePorts  
  
```  
  
 <span data-ttu-id="13c7b-139">以下是範例會執行 Windows PowerShell 指令碼來建立新接收埠：</span><span class="sxs-lookup"><span data-stu-id="13c7b-139">Here is an example of running the Windows PowerShell script to create the new receive port:</span></span>  
  
```  
PS C:\> .\receiveports.ps1  
  
Attempting to create "My Receive Port"...  
  
Enumerating all receive ports...  
  
BatchControlMessageRecvPort  
  
ResendReceivePort  
  
HelloWorldReceivePort  
  
CBRReceivePort  
  
RP_ReceivePOFromInternal  
  
RP_ShipmentAgency1_OrderFiles  
  
RP_ShipmentAgency2_OrderFiles  
  
RP_ReceivePOFromBuyer  
  
RP_Receive_ShipmentAgency_Ack  
  
My Receive Port  
  
Press <ENTER> to delete "My Receive Port"...  
  
Enumerating all receive ports to show "My Receive Port" was removed...  
  
BatchControlMessageRecvPort  
  
ResendReceivePort  
  
HelloWorldReceivePort  
  
CBRReceivePort  
  
RP_ReceivePOFromInternal  
  
RP_ShipmentAgency1_OrderFiles  
  
RP_ShipmentAgency2_OrderFiles  
  
RP_ReceivePOFromBuyer  
  
RP_Receive_ShipmentAgency_Ack  
```  
  
## <a name="see-also"></a><span data-ttu-id="13c7b-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13c7b-140">See Also</span></span>  
 [<span data-ttu-id="13c7b-141">系統管理員 ExplorerOM （BizTalk Server 範例資料夾）</span><span class="sxs-lookup"><span data-stu-id="13c7b-141">Admin-ExplorerOM (BizTalk Server Samples Folder)</span></span>](../core/admin-explorerom-biztalk-server-samples-folder.md)