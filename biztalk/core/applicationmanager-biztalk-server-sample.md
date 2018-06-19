---
title: ApplicationManager （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 51ebe7a8-a0ca-4d2a-bf40-ec6421ba5a95
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 374fc67f0a4b750aa1f797d57778f68347383736
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25965580"
---
# <a name="applicationmanager-biztalk-server-sample"></a><span data-ttu-id="98f7d-102">ApplicationManager （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="98f7d-102">ApplicationManager (BizTalk Server Sample)</span></span>
<span data-ttu-id="98f7d-103">ApplicationManager 範例示範如何啟動或停止 BizTalk 應用程式使用系統管理物件。</span><span class="sxs-lookup"><span data-stu-id="98f7d-103">The ApplicationManager sample demonstrates how to start or stop a  BizTalk application by using the administration objects.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="98f7d-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="98f7d-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="98f7d-105">您必須擁有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在此範例中使用的系統管理物件的系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="98f7d-105">You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.</span></span>  
  
-   <span data-ttu-id="98f7d-106">Windows PowerShell 指令碼需要 Windows PowerShell 執行原則以允許執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="98f7d-106">The Windows PowerShell script requires the Windows PowerShell execution policy to allow script execution.</span></span> <span data-ttu-id="98f7d-107">如需詳細資訊，請參閱：[檢查執行原則](http://go.microsoft.com/fwlink/?LinkId=128930)。</span><span class="sxs-lookup"><span data-stu-id="98f7d-107">For more information see: [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="98f7d-108">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="98f7d-108">What This Sample Does</span></span>  
 <span data-ttu-id="98f7d-109">這個範例示範如何使用**BtsCatalogExplorer**和**應用程式**類別**Microsoft.BizTalk.ExplorerOM**啟動和停止的已部署的命名空間 BizTalk 應用程式。</span><span class="sxs-lookup"><span data-stu-id="98f7d-109">This sample demonstrates using the **BtsCatalogExplorer** and **Application** classes from the **Microsoft.BizTalk.ExplorerOM** namespace to start and stop a deployed  BizTalk application.</span></span> <span data-ttu-id="98f7d-110">此範例以 Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="98f7d-110">The sample is written in Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)].</span></span> <span data-ttu-id="98f7d-111">本主題也包含 Windows PowerShell 範例指令碼。</span><span class="sxs-lookup"><span data-stu-id="98f7d-111">A Windows PowerShell example script is also included in this topic.</span></span> <span data-ttu-id="98f7d-112">此範例會示範下列作業：</span><span class="sxs-lookup"><span data-stu-id="98f7d-112">The sample demonstrates the following operations:</span></span>  
  
-   <span data-ttu-id="98f7d-113">使用連接到 「 BizTalk 管理 」 資料庫**BtsCatalogExplorer**類別。</span><span class="sxs-lookup"><span data-stu-id="98f7d-113">Connecting to the BizTalk Management database by using the **BtsCatalogExplorer** class.</span></span>  
  
-   <span data-ttu-id="98f7d-114">尋找應用程式執行個體從**BtsCatalogExplorer**根據應用程式名稱。</span><span class="sxs-lookup"><span data-stu-id="98f7d-114">Finding an application instance from  **BtsCatalogExplorer** based on application name.</span></span>  
  
-   <span data-ttu-id="98f7d-115">正在提交應用程式啟動或停止命令。</span><span class="sxs-lookup"><span data-stu-id="98f7d-115">Submitting a start or stop command for the application.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="98f7d-116">此範例的位置</span><span class="sxs-lookup"><span data-stu-id="98f7d-116">Where To Find This Sample</span></span>  
 <span data-ttu-id="98f7d-117">這個範例位於下列 SDK 位置：</span><span class="sxs-lookup"><span data-stu-id="98f7d-117">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="98f7d-118">\<*範例路徑*\>\Admin\ExplorerOM\ApplicationManager</span><span class="sxs-lookup"><span data-stu-id="98f7d-118">\<*Samples Path*\>\Admin\ExplorerOM\ApplicationManager</span></span>  
  
 <span data-ttu-id="98f7d-119">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="98f7d-119">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="98f7d-120">檔案</span><span class="sxs-lookup"><span data-stu-id="98f7d-120">File(s)</span></span>|<span data-ttu-id="98f7d-121">Description</span><span class="sxs-lookup"><span data-stu-id="98f7d-121">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="98f7d-122">Program.cs</span><span class="sxs-lookup"><span data-stu-id="98f7d-122">Program.cs</span></span>|[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]<span data-ttu-id="98f7d-123">這個範例中示範的作業的來源檔案。</span><span class="sxs-lookup"><span data-stu-id="98f7d-123"> source file for operations demonstrated in this sample.</span></span>|  
|<span data-ttu-id="98f7d-124">ApplicationManager.sln,ApplicationManager.csproj,ApplicationManager.suo</span><span class="sxs-lookup"><span data-stu-id="98f7d-124">ApplicationManager.sln,ApplicationManager.csproj,ApplicationManager.suo</span></span>|<span data-ttu-id="98f7d-125">此範例的方案和專案檔。</span><span class="sxs-lookup"><span data-stu-id="98f7d-125">Solution and project files for the sample.</span></span>|  
  
## <a name="building-and-running-this-sample"></a><span data-ttu-id="98f7d-126">建置和執行此範例</span><span class="sxs-lookup"><span data-stu-id="98f7d-126">Building and Running This Sample</span></span>  
  
#### <a name="to-build-this-sample"></a><span data-ttu-id="98f7d-127">建置此範例</span><span class="sxs-lookup"><span data-stu-id="98f7d-127">To build this sample</span></span>  
  
1.  <span data-ttu-id="98f7d-128">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟方案檔 ApplicationManager.sln。</span><span class="sxs-lookup"><span data-stu-id="98f7d-128">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file ApplicationManager.sln.</span></span>  
  
2.  <span data-ttu-id="98f7d-129">按一下 [ **建置** ] 功能表上的 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="98f7d-129">On the **Build** menu, click **Build Solution**.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="98f7d-130">執行此範例</span><span class="sxs-lookup"><span data-stu-id="98f7d-130">To run this sample</span></span>  
  
1.  <span data-ttu-id="98f7d-131">開啟命令視窗並巡覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="98f7d-131">Open a command window and navigate to the following folder:</span></span>  
  
     <span data-ttu-id="98f7d-132">\<*範例路徑*\>\Admin\ExplorerOM\ApplicationManager\bin\Debug</span><span class="sxs-lookup"><span data-stu-id="98f7d-132">\<*Samples Path*\>\Admin\ExplorerOM\ApplicationManager\bin\Debug</span></span>  
  
2.  <span data-ttu-id="98f7d-133">執行檔案 ApplicationManager.exe 提供下列兩個已排序命令列引數：</span><span class="sxs-lookup"><span data-stu-id="98f7d-133">Run the file ApplicationManager.exe providing the following two ordered command-line arguments:</span></span>  
  
    -   <span data-ttu-id="98f7d-134">**\<開始 &#124; 將 stop\>** 第一個引數是要部署的應用程式上執行的作業。</span><span class="sxs-lookup"><span data-stu-id="98f7d-134">**\<start&#124;stop\>** First argument is the operation to be performed on the deployed application.</span></span>  
  
    -   <span data-ttu-id="98f7d-135">**\<ApplicationName\>** 第二個引數是已部署的應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="98f7d-135">**\<ApplicationName\>** Second argument is the name of the deployed application.</span></span>  
  
     <span data-ttu-id="98f7d-136">例如：</span><span class="sxs-lookup"><span data-stu-id="98f7d-136">For example:</span></span>  
  
    ```  
    ApplicationManager.exe stop MyBizTalkApp  
    ```  
  
     <span data-ttu-id="98f7d-137">命令列參數不足以執行範例時，會顯示使用語法。</span><span class="sxs-lookup"><span data-stu-id="98f7d-137">Running the sample with insufficient command-line parameters displays the usage syntax.</span></span> <span data-ttu-id="98f7d-138">例如：</span><span class="sxs-lookup"><span data-stu-id="98f7d-138">For example:</span></span>  
  
    ```  
    Usage:  
  
    ApplicationManager <start|stop> <Application Name>  
  
     Where:  
      <Application Name> = The name of the application that needs to be changed  
  
    Example: ApplicationManager start Application1  
    ```  
  
## <a name="windows-powershell-script-example"></a><span data-ttu-id="98f7d-139">Windows PowerShell 指令碼範例</span><span class="sxs-lookup"><span data-stu-id="98f7d-139">Windows PowerShell Script Example</span></span>  
 <span data-ttu-id="98f7d-140">下列 Windows PowerShell 指令碼片段可以用來示範的相同功能**ExplorerOM**類別：</span><span class="sxs-lookup"><span data-stu-id="98f7d-140">The following Windows PowerShell script fragment can be used to demonstrate the same features of the **ExplorerOM** classes:</span></span>  
  
```  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
#=== Loop through applications in the catalog trying to find a name match ===#  
  
foreach($app in $Catalog.Applications)  
{  
    if ($($app.Name) -ieq $args[1])  
    {  
  
        #=== The first command-line argument should be "start" or "stop" ===#  
  
        if ($args[0] -ieq "start")  
        {  
            Write-Host `r`nIssuing start command to $app.Name...`r`n  
            $app.Start([Microsoft.BizTalk.ExplorerOM.ApplicationStartOption] "StartAll")  
            $Catalog.SaveChanges()  
        }  
  
        if ($args[0] -ieq "stop")  
        {  
            Write-Host `r`nIssuing stop command to $app.Name...`r`n  
            $app.Stop([Microsoft.BizTalk.ExplorerOM.ApplicationStopOption] "StopAll")  
            $Catalog.SaveChanges()  
        }  
  
    }  
}  
```  
  
 <span data-ttu-id="98f7d-141">指令碼必須要有相同的命令列引數為[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="98f7d-141">The script expects the same command-line arguments as the [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] sample.</span></span> <span data-ttu-id="98f7d-142">執行 Windows PowerShell 指令碼來啟動已部署的 BizTalk 應用程式中的範例如下：</span><span class="sxs-lookup"><span data-stu-id="98f7d-142">Here is an example of running the Windows PowerShell script to start a deployed BizTalk application:</span></span>  
  
```  
PS C:\> .\ApplicationManager.ps1 start MyBizTalkApp  
  
Issuing start command to MyBizTalkApp ...  
```  
  
## <a name="see-also"></a><span data-ttu-id="98f7d-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="98f7d-143">See Also</span></span>  
 [<span data-ttu-id="98f7d-144">Admin-ExplorerOM (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="98f7d-144">Admin-ExplorerOM (BizTalk Server Samples Folder)</span></span>](../core/admin-explorerom-biztalk-server-samples-folder.md)