---
title: OrchestrationBinding （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ea14c0db-ea83-4bf9-b417-f877b3cb1bf9
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b361968ddb28d629244515281cc02147af533cd0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25973796"
---
# <a name="orchestrationbinding-biztalk-server-sample"></a><span data-ttu-id="96707-102">OrchestrationBinding (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="96707-102">OrchestrationBinding (BizTalk Server Sample)</span></span>
<span data-ttu-id="96707-103">協調流程繫結範例會示範使用 [Microsoft.BizTalk.ExplorerOM](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.aspx) 系統管理物件來設定及管理協調流程。</span><span class="sxs-lookup"><span data-stu-id="96707-103">The Orchestration Binding sample demonstrates using the [Microsoft.BizTalk.ExplorerOM](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.aspx) administrative objects to configure and manage orchestrations.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="96707-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="96707-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="96707-105">這個範例需要部署 HelloWorld 範例時，會藉由執行中的 setup.bat \<*範例路徑*\>\Orchestrations\HelloWorld 目錄。</span><span class="sxs-lookup"><span data-stu-id="96707-105">This sample requires that the HelloWorld sample be deployed by running setup.bat located in the \<*Samples Path*\>\Orchestrations\HelloWorld directory.</span></span>  
  
-   <span data-ttu-id="96707-106">您必須擁有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在此範例中使用的系統管理物件的系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="96707-106">You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.</span></span>  
  
-   <span data-ttu-id="96707-107">Windows PowerShell 指令碼範例需要 Windows PowerShell 執行原則來允許指令碼執行。</span><span class="sxs-lookup"><span data-stu-id="96707-107">The Windows PowerShell script example requires the Windows PowerShell execution policy to allow script execution.</span></span> <span data-ttu-id="96707-108">如需詳細資訊，請參閱 [檢查執行原則](http://go.microsoft.com/fwlink/?LinkId=128930)。</span><span class="sxs-lookup"><span data-stu-id="96707-108">For more information see [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="96707-109">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="96707-109">What This Sample Does</span></span>  
 <span data-ttu-id="96707-110">本範例示範如何使用 **Microsoft.BizTalk.ExplorerOM** 命名空間中的系統管理物件來管理協調流程。</span><span class="sxs-lookup"><span data-stu-id="96707-110">This sample demonstrates using the administrative objects in the **Microsoft.BizTalk.ExplorerOM** namespace to manage orchestrations.</span></span> <span data-ttu-id="96707-111">此範例會使用 **ExplorerOM** 物件示範下列作業：</span><span class="sxs-lookup"><span data-stu-id="96707-111">The sample demonstrates the following operations using the **ExplorerOM** objects:</span></span>  
  
-   <span data-ttu-id="96707-112">使用[Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.btscatalogexplorer.aspx) 類別連接到 BizTalk 管理資料庫。</span><span class="sxs-lookup"><span data-stu-id="96707-112">Connecting to the BizTalk Management database by using the[Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.btscatalogexplorer.aspx) class.</span></span>  
  
-   <span data-ttu-id="96707-113">變更 **Microsoft.BizTalk.ExplorerOM.BtsOrchestration** 類別的 [狀態](http://msdn.microsoft.com/library/Microsoft.BizTalk.ExplorerOM.BtsOrchestration.aspx) 屬性以停止和啟動協調流程。</span><span class="sxs-lookup"><span data-stu-id="96707-113">Stopping and starting orchestrations by changing the **Status** property of the [Microsoft.BizTalk.ExplorerOM.BtsOrchestration](http://msdn.microsoft.com/library/Microsoft.BizTalk.ExplorerOM.BtsOrchestration.aspx) class.</span></span>  
  
-   <span data-ttu-id="96707-114">變更 **Microsoft.BizTalk.ExplorerOM.BtsOrchestration** 類別的 [狀態](http://msdn.microsoft.com/library/Microsoft.BizTalk.ExplorerOM.BtsOrchestration.aspx) 屬性，登錄及取消登錄協調流程。</span><span class="sxs-lookup"><span data-stu-id="96707-114">Enlisting and unenlisting orchestrations by changing the **Status** property of the [Microsoft.BizTalk.ExplorerOM.BtsOrchestration](http://msdn.microsoft.com/library/Microsoft.BizTalk.ExplorerOM.BtsOrchestration.aspx) class.</span></span>  
  
-   <span data-ttu-id="96707-115">使用 **Microsoft.BizTalk.ExplorerOM.BtsOrchestration** 類別上的 [連接埠](http://msdn.microsoft.com/library/Microsoft.BizTalk.ExplorerOM.BtsOrchestration.aspx) 集合，繫結及解除繫結協調流程。</span><span class="sxs-lookup"><span data-stu-id="96707-115">Binding and unbinding orchestrations by using the **Ports** collection on the [Microsoft.BizTalk.ExplorerOM.BtsOrchestration](http://msdn.microsoft.com/library/Microsoft.BizTalk.ExplorerOM.BtsOrchestration.aspx) class.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="96707-116">此範例的位置</span><span class="sxs-lookup"><span data-stu-id="96707-116">Where To Find This Sample</span></span>  
 <span data-ttu-id="96707-117">這個範例位於下列 SDK 位置：</span><span class="sxs-lookup"><span data-stu-id="96707-117">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="96707-118">\<*範例路徑*\>\Admin\ExplorerOM\OrchestrationBinding</span><span class="sxs-lookup"><span data-stu-id="96707-118">\<*Samples Path*\>\Admin\ExplorerOM\OrchestrationBinding</span></span>  
  
 <span data-ttu-id="96707-119">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="96707-119">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="96707-120">檔案</span><span class="sxs-lookup"><span data-stu-id="96707-120">File(s)</span></span>|<span data-ttu-id="96707-121">描述</span><span class="sxs-lookup"><span data-stu-id="96707-121">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="96707-122">OrchestrationBinding.cs</span><span class="sxs-lookup"><span data-stu-id="96707-122">OrchestrationBinding.cs</span></span>|[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]<span data-ttu-id="96707-123">這個範例中示範的作業的來源檔案。</span><span class="sxs-lookup"><span data-stu-id="96707-123"> source file for operations demonstrated in this sample.</span></span>|  
|<span data-ttu-id="96707-124">OrchestrationBinding.sln、OrchestrationBinding.csproj、OrchestrationBinding.suo</span><span class="sxs-lookup"><span data-stu-id="96707-124">OrchestrationBinding.sln, OrchestrationBinding.csproj, OrchestrationBinding.suo</span></span>|<span data-ttu-id="96707-125">此範例的方案和專案檔。</span><span class="sxs-lookup"><span data-stu-id="96707-125">Solution and project files for the sample.</span></span>|  
  
## <a name="building-and-running-this-sample"></a><span data-ttu-id="96707-126">建置和執行此範例</span><span class="sxs-lookup"><span data-stu-id="96707-126">Building and Running This Sample</span></span>  
  
#### <a name="to-build-this-sample"></a><span data-ttu-id="96707-127">建置此範例</span><span class="sxs-lookup"><span data-stu-id="96707-127">To build this sample</span></span>  
  
1.  <span data-ttu-id="96707-128">請確定您已完成建置和初始化 HelloWorld 範例的步驟。</span><span class="sxs-lookup"><span data-stu-id="96707-128">Make sure you have completed the steps for building and initializing the HelloWorld sample.</span></span> <span data-ttu-id="96707-129">這些步驟中提供[HelloWorld （BizTalk Server 範例）](../core/helloworld-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="96707-129">Those steps are provided in [HelloWorld (BizTalk Server Sample)](../core/helloworld-biztalk-server-sample.md).</span></span>  
  
2.  <span data-ttu-id="96707-130">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟方案檔 OrchestrationBinding.sln。</span><span class="sxs-lookup"><span data-stu-id="96707-130">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file OrchestrationBinding.sln.</span></span>  
  
3.  <span data-ttu-id="96707-131">按一下 [ **建置** ] 功能表上的 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="96707-131">On the **Build** menu, click **Build Solution**.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="96707-132">執行此範例</span><span class="sxs-lookup"><span data-stu-id="96707-132">To run this sample</span></span>  
  
1.  <span data-ttu-id="96707-133">開啟命令視窗並巡覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="96707-133">Open a command window and navigate to the following folder:</span></span>  
  
     <span data-ttu-id="96707-134">\<*範例路徑*\>\Admin\ExplorerOM\OrchestrationBinding\bin\Debug</span><span class="sxs-lookup"><span data-stu-id="96707-134">\<*Samples Path*\>\Admin\ExplorerOM\OrchestrationBinding\bin\Debug</span></span>  
  
2.  <span data-ttu-id="96707-135">執行 OrchestrationBinding.exe 檔案並遵循範例所提供的指示。</span><span class="sxs-lookup"><span data-stu-id="96707-135">Run the file OrchestrationBinding.exe and follow the directions provided by the sample.</span></span>  
  
## <a name="windows-powershell-script-example"></a><span data-ttu-id="96707-136">Windows PowerShell 指令碼範例</span><span class="sxs-lookup"><span data-stu-id="96707-136">Windows PowerShell Script Example</span></span>  
 <span data-ttu-id="96707-137">下列 Windows PowerShell 指令碼可以用來示範 **ExplorerOM** 類別的相同功能。</span><span class="sxs-lookup"><span data-stu-id="96707-137">The following Windows PowerShell script can be used to demonstrate the same features of the **ExplorerOM** classes.</span></span>  
  
```  
  
Function RefreshPrompt($oldstatus,$newstatus)  
{  
  Write-Host Orchestration Status should now be `"$oldstatus`"  
  Write-Host Press F5 in the Orchestrations view of BizTalk Server Administration Console to refresh and verify   
  
  if ($newstatus)  
  {  
    Write-Host Pressing `<Enter`> now will $newstatus the orchestration using ExplorerOM`.`.`.  
    Read-Host  
    Write-Host "=== Please wait, attempting to $newstatus the orchestration... ===`r`n"  
  }  
  else  
  {  
    write-host `r`n  
  }  
}  
  
#===================#  
#=== Main Script ===#  
#===================#  
  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect to the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
#=== This sample expects the HelloWorld sample orchestration to be using the ===#  
#=== default name "Biztalk Application 1"                                    ===#  
  
$HelloWorldApp = $Catalog.Applications["Biztalk Application 1"]  
$orch = $HelloWorldApp.orchestrations["Microsoft.Samples.BizTalk.HelloWorld.HelloSchedule"]  
  
#==================================================================#  
#=== Register a trap handler to discard changes on exceptions   ===#  
#=== Execution will continue in the event we need to re-enlist, ===#  
#=== re-bind, or restart the orchestration.                     ===#  
#==================================================================#  
  
$ErrorActionPreference="silentlycontinue"  
trap { "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes and continuing execution...`r`n";$Catalog.DiscardChanges();}  
  
write-host `r`nMake sure the "HelloWorld" sample application is deployed and running.  
write-host By default it will be listed in the BizTalk Server Administration Console  
write-host with the application name: `"BizTalk.Application.1`"`r`n  
  
#==========================================================#  
#=== Change orchestration state from Started to stopped ===#  
#==========================================================#  
  
RefreshPrompt Started stop  
$orch.Status = [Microsoft.BizTalk.ExplorerOM.OrchestrationStatus] "Enlisted"  
$Catalog.SaveChanges()  
  
#=============================================================#  
#=== Change orchestration state from stopped to unenlisted ===#  
#=============================================================#  
  
RefreshPrompt Stopped unenlist  
$orch.Status = [Microsoft.BizTalk.ExplorerOM.OrchestrationStatus] "Unenlisted"  
$Catalog.SaveChanges()  
  
#=============================================================#  
#=== Change orchestration state from unenlisted to unbound ===#  
#=============================================================#  
  
RefreshPrompt Unenlisted unbind  
$orch.Ports["SendInvoicePort"].SendPort = $null  
$orch.Ports["ReceivePOPort"].ReceivePort = $null;  
$orch.Host = $null  
$Catalog.SaveChanges()  
  
#==================================================================#  
#=== Change orchestration state from unbound back to unenlisted ===#  
#==================================================================#  
  
RefreshPrompt Unenlisted`(Unbound`) re-bind  
$orch.Ports["SendInvoicePort"].SendPort = $Catalog.SendPorts["HelloWorldSendPort"]  
$orch.Ports["ReceivePOPort"].ReceivePort = $Catalog.ReceivePorts["HelloWorldReceivePort"]  
$orch.Host = $Catalog.Hosts["BizTalkServerApplication"]  
$Catalog.SaveChanges()  
  
#==================================================================#  
#=== Change orchestration state from unenlisted back to stopped ===#  
#==================================================================#  
  
RefreshPrompt Unenlisted enlist  
$orch.Status = [Microsoft.BizTalk.ExplorerOM.OrchestrationStatus] "Enlisted"  
$Catalog.SaveChanges()  
  
#===============================================================#  
#=== Change orchestration state from stopped back to started ===#  
#===============================================================#  
  
RefreshPrompt Stopped restart  
$orch.Status = [Microsoft.BizTalk.ExplorerOM.OrchestrationStatus] "Started"  
$Catalog.SaveChanges()  
  
RefreshPrompt Started  
  
```  
  
 <span data-ttu-id="96707-138">以下是執行 Windows PowerShell 指令碼的輸出範例。</span><span class="sxs-lookup"><span data-stu-id="96707-138">Here is an example output from running the Windows PowerShell script.</span></span>  
  
```  
PS C:\> .\OrchestrationBind.ps1  
  
Make sure the HelloWorld sample application is deployed and running.  
By default it will be listed in the BizTalk Server Administration Console  
with the application name: "BizTalk.Application.1"  
  
Orchestration Status should now be "Started"  
Press F5 in the Orchestrations view of BizTalk Server Administration Console to refresh and verify  
Pressing <Enter> now will stop the orchestration using ExplorerOM...  
  
=== Please wait, attempting to stop the orchestration... ===  
  
Orchestration Status should now be "Stopped"  
Press F5 in the Orchestrations view of BizTalk Server Administration Console to refresh and verify  
Pressing <Enter> now will unenlist the orchestration using ExplorerOM...  
  
=== Please wait, attempting to unenlist the orchestration... ===  
  
Orchestration Status should now be "Unenlisted"  
Press F5 in the Orchestrations view of BizTalk Server Administration Console to refresh and verify  
Pressing <Enter> now will unbind the orchestration using ExplorerOM...  
  
=== Please wait, attempting to unbind the orchestration... ===  
  
Orchestration Status should now be "Unenlisted(Unbound)"  
Press F5 in the Orchestrations view of BizTalk Server Administration Console to refresh and verify  
Pressing <Enter> now will re-bind the orchestration using ExplorerOM...  
  
=== Please wait, attempting to re-bind the orchestration... ===  
  
Orchestration Status should now be "Unenlisted"  
Press F5 in the Orchestrations view of BizTalk Server Administration Console to refresh and verify  
Pressing <Enter> now will enlist the orchestration using ExplorerOM...  
  
=== Please wait, attempting to enlist the orchestration... ===  
  
Orchestration Status should now be "Stopped"  
Press F5 in the Orchestrations view of BizTalk Server Administration Console to refresh and verify  
Pressing <Enter> now will restart the orchestration using ExplorerOM...  
  
=== Please wait, attempting to restart the orchestration... ===  
  
Orchestration Status should now be "Started"  
Press F5 in the Orchestrations view of BizTalk Server Administration Console to refresh and verify  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="96707-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="96707-139">See Also</span></span>  
 <span data-ttu-id="96707-140">[系統管理員 ExplorerOM （BizTalk Server 範例資料夾）](../core/admin-explorerom-biztalk-server-samples-folder.md) </span><span class="sxs-lookup"><span data-stu-id="96707-140">[Admin-ExplorerOM (BizTalk Server Samples Folder)](../core/admin-explorerom-biztalk-server-samples-folder.md) </span></span>  
 [<span data-ttu-id="96707-141">HelloWorld (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="96707-141">HelloWorld (BizTalk Server Sample)</span></span>](../core/helloworld-biztalk-server-sample.md)