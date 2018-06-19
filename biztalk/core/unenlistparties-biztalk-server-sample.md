---
title: UnenlistParties （BizTalk Server 範例） |Microsoft 文件
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
- parties, unenlisting
- examples, administering
- administering, examples
ms.assetid: a751a0fc-ca94-4610-a8aa-db3a24159334
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 34cbb94dff7211a157fc492c1157fa379236641e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25973468"
---
# <a name="unenlistparties-biztalk-server-sample"></a><span data-ttu-id="10a04-102">UnenlistParties （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="10a04-102">UnenlistParties (BizTalk Server Sample)</span></span>
<span data-ttu-id="10a04-103">UnenlistParties 範例示範如何取消登錄與已部署之 BizTalk Server 組件關聯的所有合作對象。</span><span class="sxs-lookup"><span data-stu-id="10a04-103">The UnenlistParties sample demonstrates how to unenlist all of the parties associated with a deployed BizTalk Server assembly.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="10a04-104">如果在部署後不需要部署指令碼，就應該將其移除。</span><span class="sxs-lookup"><span data-stu-id="10a04-104">Deployment scripts should be removed after deployment if not needed.</span></span> <span data-ttu-id="10a04-105">必須保留的系統管理指令碼和其他指令碼都應該由 ACL 保護，而且予以密切監控。</span><span class="sxs-lookup"><span data-stu-id="10a04-105">Administration scripts and other scripts that must remain should be secured by ACL’s and closely monitored.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="10a04-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="10a04-106">Prerequisites</span></span>  
  
-   <span data-ttu-id="10a04-107">您必須擁有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在此範例中使用的系統管理物件的系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="10a04-107">You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.</span></span>  
  
-   <span data-ttu-id="10a04-108">Windows PowerShell 指令碼需要 Windows PowerShell 執行原則以允許執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="10a04-108">The Windows PowerShell script requires the Windows PowerShell execution policy to allow script execution.</span></span> <span data-ttu-id="10a04-109">如需詳細資訊，請參閱：[檢查執行原則](http://go.microsoft.com/fwlink/?LinkId=128930)。</span><span class="sxs-lookup"><span data-stu-id="10a04-109">For more information see: [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="10a04-110">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="10a04-110">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="10a04-111">此範例是以 Visual C# 撰寫而成，並使用 [BizTalk 總管] 物件模型中的物件，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="10a04-111">This sample, written in Visual C# using objects from the BizTalk Explorer object model, performs the following operations:</span></span>  
  
-   <span data-ttu-id="10a04-112">查詢特定組件。</span><span class="sxs-lookup"><span data-stu-id="10a04-112">Query for a particular assembly.</span></span>  
  
-   <span data-ttu-id="10a04-113">擷取與該組件相關聯的所有角色。</span><span class="sxs-lookup"><span data-stu-id="10a04-113">Retrieve all of the roles associated with that assembly.</span></span>  
  
-   <span data-ttu-id="10a04-114">取消登錄與每個這類角色相關聯的所有合作對象。</span><span class="sxs-lookup"><span data-stu-id="10a04-114">Unenlist all of the parties associated with each such role.</span></span>  
  
-   <span data-ttu-id="10a04-115">處理任何錯誤，讓有意義的資訊能傳回給使用者。</span><span class="sxs-lookup"><span data-stu-id="10a04-115">Handle any errors such that meaningful information is returned to the user.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="10a04-116">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="10a04-116">Where to Find This Sample</span></span>  
 <span data-ttu-id="10a04-117">這個範例位於下列 SDK 位置：</span><span class="sxs-lookup"><span data-stu-id="10a04-117">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="10a04-118">\<*範例路徑*\>\Admin\ExplorerOM\UnenlistParties\\</span><span class="sxs-lookup"><span data-stu-id="10a04-118">\<*Samples Path*\>\Admin\ExplorerOM\UnenlistParties\\</span></span>  
  
 <span data-ttu-id="10a04-119">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="10a04-119">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="10a04-120">檔案</span><span class="sxs-lookup"><span data-stu-id="10a04-120">File(s)</span></span>|<span data-ttu-id="10a04-121">Description</span><span class="sxs-lookup"><span data-stu-id="10a04-121">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="10a04-122">App.ico, AssemblyInfo.cs, UnenlistParties.csproj, UnenlistParties.sln, UnenlistParties.cs</span><span class="sxs-lookup"><span data-stu-id="10a04-122">App.ico, AssemblyInfo.cs, UnenlistParties.csproj, UnenlistParties.sln, UnenlistParties.cs</span></span>|<span data-ttu-id="10a04-123">專案、解決方案和原始程式檔，用於建置 Visual C# 命令列應用程式，以取消登錄特定組件的所有合作對象。</span><span class="sxs-lookup"><span data-stu-id="10a04-123">Project, solution, and source files for building a Visual C# command-line application that unenlists all of the parties for a particular assembly.</span></span>|  
  
### <a name="to-build-and-initialize-this-sample"></a><span data-ttu-id="10a04-124">若要建置並初始化這個範例</span><span class="sxs-lookup"><span data-stu-id="10a04-124">To build and initialize this sample</span></span>  
  
1.  <span data-ttu-id="10a04-125">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，開啟解決方案檔 UnenlistParties.sln。</span><span class="sxs-lookup"><span data-stu-id="10a04-125">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file UnenlistParties.sln.</span></span>  
  
2.  <span data-ttu-id="10a04-126">在**建置**功能表上，選取**建置方案**。</span><span class="sxs-lookup"><span data-stu-id="10a04-126">In the **Build** menu, select **Build Solution**.</span></span>  
  
### <a name="to-run-this-sample"></a><span data-ttu-id="10a04-127">執行此範例</span><span class="sxs-lookup"><span data-stu-id="10a04-127">To run this sample</span></span>  
  
1.  <span data-ttu-id="10a04-128">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="10a04-128">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="10a04-129">\<*範例路徑*\>\Admin\ExplorerOM\UnenlistParties\bin\Debug\\</span><span class="sxs-lookup"><span data-stu-id="10a04-129">\<*Samples Path*\>\Admin\ExplorerOM\UnenlistParties\bin\Debug\\</span></span>  
  
2.  <span data-ttu-id="10a04-130">執行 UnenlistParties.exe 檔案，它會傳遞下列其中一個命令列引數：</span><span class="sxs-lookup"><span data-stu-id="10a04-130">Run the file UnenlistParties.exe, passing one of the two following command-line arguments:</span></span>  
  
    -   <span data-ttu-id="10a04-131">**\<** ***AssemblyName* \>** 。</span><span class="sxs-lookup"><span data-stu-id="10a04-131">**\<** ***AssemblyName* \>**.</span></span> <span data-ttu-id="10a04-132">凡是與該組件名稱相關聯的合作對象都將取消登錄。</span><span class="sxs-lookup"><span data-stu-id="10a04-132">The name of an assembly from which all associated parties are to be unenlisted.</span></span> <span data-ttu-id="10a04-133">如果組件名稱包含空格，請用引號括住該名稱。</span><span class="sxs-lookup"><span data-stu-id="10a04-133">If the assembly name contains spaces, enclose the name in quotes.</span></span>  
  
    -   <span data-ttu-id="10a04-134">**/?.**</span><span class="sxs-lookup"><span data-stu-id="10a04-134">**/?.**</span></span> <span data-ttu-id="10a04-135">顯示說明。</span><span class="sxs-lookup"><span data-stu-id="10a04-135">Displays help.</span></span>  
  
     <span data-ttu-id="10a04-136">例如：</span><span class="sxs-lookup"><span data-stu-id="10a04-136">For example:</span></span>  
  
    ```  
    UnenlistParties "My BizTalk Assembly.dll"  
    ```  
  
     <span data-ttu-id="10a04-137">-或-</span><span class="sxs-lookup"><span data-stu-id="10a04-137">-OR-</span></span>  
  
    ```  
    UnenlistParties /?  
    ```  
  
## <a name="windows-powershell-script-example"></a><span data-ttu-id="10a04-138">Windows Powershell 指令碼範例</span><span class="sxs-lookup"><span data-stu-id="10a04-138">Windows Powershell Script Example</span></span>  
 <span data-ttu-id="10a04-139">下列 Windows Powershell 指令碼片段可以用來示範的相同功能**ExplorerOM**類別：</span><span class="sxs-lookup"><span data-stu-id="10a04-139">The following Windows Powershell script fragment can be used to demonstrate the same features of the **ExplorerOM** classes:</span></span>  
  
```  
#===================#  
#=== Main Script ===#  
#===================#  
  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect to the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
#=====================================================#  
#=== If no assembly name is specified, just list   ===#  
#=== the assemblies, roles and partyies enlisted.  ===#  
#=====================================================#  
  
if ($args[0] -eq $null)  
{  
  Write-Host `r`n===========================================================  
  Write-Host No assembly name provided for party unenlist operation.  
  Write-Host Listing Parties for each assembly on local BizTalk Server:  
  Write-Host ===========================================================`r`n  
  
  foreach ($assembly in $Catalog.Assemblies)  
  {  
    write-host $Assembly.Name`r`n  
  
    foreach ($role in $Assembly.Roles)  
    {  
      write-host `t($role.name)  
  
      foreach($party in $role.EnlistedParties)  
      {  
        Write-Host `t`t($party.Party.Name)  
      }  
      write-host  
    }  
  }  
  
  write-host  
}  
  
#=====================================================#  
#=== If assembly name is specified, remove parties ===#  
#=== enlisted in all roles for the assembly.       ===#  
#=====================================================#  
  
else  
{  
  $Assembly = $Catalog.Assemblies[$args[0]]  
  
  if ($assembly -eq $null)  
  {  
    write-host Assembly named $args[0] not found.`r`n  
  }   
  
  else  
  {  
    write-host `r`nUnenlisting parties from all roles in ($Assembly.Name)`r`n  
  
    foreach ($role in $Assembly.Roles)  
    {  
  
      $count = $role.EnlistedParties.count  
  
      for($c=0; $c -lt $count; $c++)  
      {  
        #==========================================================#  
        #=== Array index stays at zero because the collection   ===#  
        #=== changes after each item is removed.                ===#  
        #==========================================================#  
  
        $party = $role.EnlistedParties[0]  
  
        Write-Host Unenlisting ($party.Party.Name) from ($role.Name)...  
        $role.RemoveEnlistedParty($party)  
        Write-Host done.`r`n  
      }  
    }  
  
    write-Host Comitting changes...  
    $catalog.SaveChanges()  
    Write-Host done.`r`n  
  }  
}  
  
```  
  
 <span data-ttu-id="10a04-140">下列指令碼輸出是由從供應商組件的一部分 PartyResolution 範例取消登錄合作對象產生。</span><span class="sxs-lookup"><span data-stu-id="10a04-140">The following script output was generated from unenlisting parties from the Supplier assembly which is part of the PartyResolution sample.</span></span> <span data-ttu-id="10a04-141">PartyResolution 範例位於\<*範例路徑*\>\Admin\Orchestrations\PartyResolution 目錄。</span><span class="sxs-lookup"><span data-stu-id="10a04-141">The PartyResolution sample is located in the \<*Samples Path*\>\Admin\Orchestrations\PartyResolution directory.</span></span>  
  
```  
PS C:\> .\UnenlistParties.ps1 Supplier  
  
Unenlisting parties from all roles in Supplier  
  
Unenlisting ShipmentAgency1 from ShipmentRole ...  
done.  
  
Unenlisting ShipmentAgency2 from ShipmentRole ...  
done.  
  
Unenlisting BuyerAgency from Buyer ...  
done.  
  
Comitting changes...  
done.  
```  
  
## <a name="see-also"></a><span data-ttu-id="10a04-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="10a04-142">See Also</span></span>  
 [<span data-ttu-id="10a04-143">Admin-ExplorerOM (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="10a04-143">Admin-ExplorerOM (BizTalk Server Samples Folder)</span></span>](../core/admin-explorerom-biztalk-server-samples-folder.md)