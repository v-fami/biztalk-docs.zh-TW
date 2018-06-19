---
title: DeleteParty （BizTalk Server 範例） |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- examples, parties
- parties, examples
- deleting, parties
- examples, administering
- parties, deleting
- administering, examples
ms.assetid: 8161af7d-76ef-4df5-81c8-f0f5c81df9a8
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 68016285a53a2655c56810028925a91c1f8d66b0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25969220"
---
# <a name="deleteparty-biztalk-server-sample"></a><span data-ttu-id="cbf4f-102">DeleteParty （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="cbf4f-102">DeleteParty (BizTalk Server Sample)</span></span>
<span data-ttu-id="cbf4f-103">DeleteParty 範例示範如何刪除指定的合作對象。</span><span class="sxs-lookup"><span data-stu-id="cbf4f-103">The DeleteParty sample demonstrates how to delete a specified party.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="cbf4f-104">如果在部署後不需要部署指令碼，就應該將其移除。</span><span class="sxs-lookup"><span data-stu-id="cbf4f-104">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="cbf4f-105">必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。</span><span class="sxs-lookup"><span data-stu-id="cbf4f-105">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cbf4f-106">您必須先建立合作對象，才可以將它刪除。</span><span class="sxs-lookup"><span data-stu-id="cbf4f-106">Before you can delete a party, you must first create one.</span></span> <span data-ttu-id="cbf4f-107">這是執行其中一種方式執行[PartyResolution （BizTalk Server 範例）](../core/partyresolution-biztalk-server-sample.md)範例。</span><span class="sxs-lookup"><span data-stu-id="cbf4f-107">One way to do this is to run the [PartyResolution (BizTalk Server Sample)](../core/partyresolution-biztalk-server-sample.md) sample.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cbf4f-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="cbf4f-108">Prerequisites</span></span>  
  
-   <span data-ttu-id="cbf4f-109">您必須擁有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在此範例中使用的系統管理物件的系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="cbf4f-109">You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.</span></span>  
  
-   <span data-ttu-id="cbf4f-110">Windows PowerShell 指令碼需要 Windows PowerShell 執行原則以允許執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="cbf4f-110">The Windows PowerShell script requires the Windows PowerShell execution policy to allow script execution.</span></span> <span data-ttu-id="cbf4f-111">如需詳細資訊，請參閱：[檢查執行原則](http://go.microsoft.com/fwlink/?LinkId=128930)。</span><span class="sxs-lookup"><span data-stu-id="cbf4f-111">For more information see: [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="cbf4f-112">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="cbf4f-112">What This Sample Does</span></span>  
 <span data-ttu-id="cbf4f-113">此範例中，撰寫 Microsoft Visual C# 中，使用 BizTalk 總管物件模型 (ExplorerOM)，物件會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="cbf4f-113">This sample, written in Microsoft Visual C#, using objects from the BizTalk Explorer object model (ExplorerOM), performs the following operations:</span></span>  
  
-   <span data-ttu-id="cbf4f-114">查詢指定的合作對象。</span><span class="sxs-lookup"><span data-stu-id="cbf4f-114">Query for a specified party.</span></span>  
  
-   <span data-ttu-id="cbf4f-115">刪除該合作對象。</span><span class="sxs-lookup"><span data-stu-id="cbf4f-115">Delete that party.</span></span>  
  
-   <span data-ttu-id="cbf4f-116">處理任何錯誤，讓有意義的資訊能傳回給使用者。</span><span class="sxs-lookup"><span data-stu-id="cbf4f-116">Handle any errors such that meaningful information is returned to the user.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="cbf4f-117">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="cbf4f-117">Where to Find This Sample</span></span>  
 <span data-ttu-id="cbf4f-118">這個範例位於下列 SDK 位置：</span><span class="sxs-lookup"><span data-stu-id="cbf4f-118">This sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="cbf4f-119">\<*範例路徑*\>\Admin\ExplorerOM\DeleteParty\\</span><span class="sxs-lookup"><span data-stu-id="cbf4f-119">\<*Samples Path*\>\Admin\ExplorerOM\DeleteParty\\</span></span>  
  
 <span data-ttu-id="cbf4f-120">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="cbf4f-120">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="cbf4f-121">檔案</span><span class="sxs-lookup"><span data-stu-id="cbf4f-121">File(s)</span></span>|<span data-ttu-id="cbf4f-122">Description</span><span class="sxs-lookup"><span data-stu-id="cbf4f-122">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cbf4f-123">App.ico、AssemblyInfo.cs、DeleteParty.csproj、DeleteParty.sln、DeleteParty.cs</span><span class="sxs-lookup"><span data-stu-id="cbf4f-123">App.ico, AssemblyInfo.cs, DeleteParty.csproj, DeleteParty.sln, DeleteParty.cs</span></span>|<span data-ttu-id="cbf4f-124">專案、方案和原始程式檔，用於建置 Visual C# 命令列應用程式，以移除指定的合作對象。</span><span class="sxs-lookup"><span data-stu-id="cbf4f-124">Project, solution, and source files for building a Visual C# command-line application that removes a specified party.</span></span>|  
  
### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="cbf4f-125">若要建置並初始化這個範例</span><span class="sxs-lookup"><span data-stu-id="cbf4f-125">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="cbf4f-126">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，開啟方案檔 DeleteParty.sln。</span><span class="sxs-lookup"><span data-stu-id="cbf4f-126">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file DeleteParty.sln.</span></span>  
  
2.  <span data-ttu-id="cbf4f-127">按一下 [ **建置** ] 功能表上的 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="cbf4f-127">On the **Build** menu, click **Build Solution**.</span></span>  
  
### <a name="to-run-this-sample"></a><span data-ttu-id="cbf4f-128">執行此範例</span><span class="sxs-lookup"><span data-stu-id="cbf4f-128">To run this sample</span></span>  
  
1.  <span data-ttu-id="cbf4f-129">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="cbf4f-129">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="cbf4f-130">\<*範例路徑*\>\Admin\ExplorerOM\DeleteParty\bin\Debug\\</span><span class="sxs-lookup"><span data-stu-id="cbf4f-130">\<*Samples Path*\>\Admin\ExplorerOM\DeleteParty\bin\Debug\\</span></span>  
  
2.  <span data-ttu-id="cbf4f-131">執行 DeleteParty.exe 檔案，它會傳遞下列兩個命令列引數：</span><span class="sxs-lookup"><span data-stu-id="cbf4f-131">Run the file DeleteParty.exe, passing one of the two following command-line arguments:</span></span>  
  
    -   <span data-ttu-id="cbf4f-132">**\<** ***PartyName* \>。**</span><span class="sxs-lookup"><span data-stu-id="cbf4f-132">**\<** ***PartyName* \>.**</span></span> <span data-ttu-id="cbf4f-133">要刪除的合作對象的名稱。</span><span class="sxs-lookup"><span data-stu-id="cbf4f-133">The name of a party to be deleted.</span></span> <span data-ttu-id="cbf4f-134">如果合作對象名稱包含空格，請用引號括住該名稱。</span><span class="sxs-lookup"><span data-stu-id="cbf4f-134">If the party name contains spaces, enclose the name in quotes.</span></span>  
  
    -   <span data-ttu-id="cbf4f-135">**/?.**</span><span class="sxs-lookup"><span data-stu-id="cbf4f-135">**/?.**</span></span> <span data-ttu-id="cbf4f-136">顯示說明。</span><span class="sxs-lookup"><span data-stu-id="cbf4f-136">Displays help.</span></span>  
  
     <span data-ttu-id="cbf4f-137">例如：</span><span class="sxs-lookup"><span data-stu-id="cbf4f-137">For example:</span></span>  
  
    ```  
    DeleteParty "My Party #3"  
    ```  
  
     <span data-ttu-id="cbf4f-138">-或-</span><span class="sxs-lookup"><span data-stu-id="cbf4f-138">-OR-</span></span>  
  
    ```  
    DeleteParty /?  
    ```  
  
## <a name="windows-powershell-script-example"></a><span data-ttu-id="cbf4f-139">Windows Powershell 指令碼範例</span><span class="sxs-lookup"><span data-stu-id="cbf4f-139">Windows Powershell Script example</span></span>  
 <span data-ttu-id="cbf4f-140">下列 Windows PowerShell 指令碼片段可以用來示範的相同功能**ExplorerOM**類別：</span><span class="sxs-lookup"><span data-stu-id="cbf4f-140">The following Windows PowerShell script fragment can be used to demonstrate the same features of the **ExplorerOM** classes:</span></span>  
  
```  
  
#===================#  
#=== Main Script ===#  
#===================#  
  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect to the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
#=======================================#  
#=== If no party name is specified   ===#  
#=== just list the parties.          ===#  
#=======================================#  
  
if ($args[0] -eq $null)  
{  
  Write-Host `r`nNo party name provided for delete operation.`r`n`r`nListing Parties on local Biztalk Server:  
  
  $Catalog.Parties | Format-List Name  
}  
  
#==========================================#  
#=== Delete the specified party by name ===#  
#==========================================#  
  
else  
{  
  $party = $Catalog.Parties[$args[0]]  
  Write-Host `r`nRemoving Party named `"($args[0])`"`r`n  
  $catalog.RemoveParty($party)  
  $catalog.SaveChanges()  
}  
```  
  
 <span data-ttu-id="cbf4f-141">指令碼範例需要單一合作對象名稱做為命令列引數傳遞。</span><span class="sxs-lookup"><span data-stu-id="cbf4f-141">The script example expects a single party name to be passed as a command line argument.</span></span>  <span data-ttu-id="cbf4f-142">它會依名稱尋找該合作對象，並嘗試將它刪除。</span><span class="sxs-lookup"><span data-stu-id="cbf4f-142">It looks for that party by name and attempts to delete it.</span></span>  <span data-ttu-id="cbf4f-143">如果沒有命令列引數傳遞給它，指令碼會列出本機 Biztalk 伺服器上的所有合作對象。</span><span class="sxs-lookup"><span data-stu-id="cbf4f-143">The script will list all parties on the local Biztalk server if no commandline argument is passed to it.</span></span> <span data-ttu-id="cbf4f-144">以下是從指令碼的範例輸出：</span><span class="sxs-lookup"><span data-stu-id="cbf4f-144">Here is example output from the script:</span></span>  
  
```  
PS C:\> .\DeletePart.ps1  
  
No party name provided for delete operation.  
  
Listing Parties on local Biztalk Server:  
  
Name : Party1  
  
Name : Party3  
  
Name : Party2  
  
PS C:\> .\DeletePart.ps1 Party3  
  
Removing Party named " Party3 "  
  
PS C:\> .\DeletePart.ps1  
  
No party name provided for delete operation.  
  
Listing Parties on local Biztalk Server:  
  
Name : Party1  
  
Name : Party2  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="cbf4f-145">請參閱</span><span class="sxs-lookup"><span data-stu-id="cbf4f-145">See Also</span></span>  
 [<span data-ttu-id="cbf4f-146">Admin-ExplorerOM (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="cbf4f-146">Admin-ExplorerOM (BizTalk Server Samples Folder)</span></span>](../core/admin-explorerom-biztalk-server-samples-folder.md)