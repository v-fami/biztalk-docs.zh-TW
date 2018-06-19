---
title: 傳送埠群組 （BizTalk Server 範例） |Microsoft 文件
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
ms.openlocfilehash: c9bb4a3453539a4c1329e9b0a2de6b46785b53fd
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25974884"
---
# <a name="sendportgroups-biztalk-server-sample"></a><span data-ttu-id="c5f89-102">傳送埠群組 （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="c5f89-102">SendPortGroups (BizTalk Server Sample)</span></span>
<span data-ttu-id="c5f89-103">傳送埠群組範例示範如何列舉使用和管理傳送埠群組**Microsoft.BizTalk.ExplorerOM**系統管理類別。</span><span class="sxs-lookup"><span data-stu-id="c5f89-103">The SendPortGroups sample demonstrates how to enumerate and manage send port groups by using the **Microsoft.BizTalk.ExplorerOM** administration classes.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c5f89-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="c5f89-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="c5f89-105">您必須擁有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在此範例中使用的系統管理物件的系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="c5f89-105">You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.</span></span>  
  
-   <span data-ttu-id="c5f89-106">Windows PowerShell 指令碼需要 Windows PowerShell 執行原則以允許執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="c5f89-106">The Windows PowerShell script requires the Windows PowerShell execution policy to allow script execution.</span></span> <span data-ttu-id="c5f89-107">如需詳細資訊，請參閱 [檢查執行原則](http://go.microsoft.com/fwlink/?LinkId=128930)。</span><span class="sxs-lookup"><span data-stu-id="c5f89-107">For more information see [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="c5f89-108">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="c5f89-108">What This Sample Does</span></span>  
 <span data-ttu-id="c5f89-109">這個範例示範如何使用**BtsCatalogExplorer**和**SendPortGroup**類別**Microsoft.BizTalk.ExplorerOM**命名空間管理傳送埠群組在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="c5f89-109">This sample demonstrates using the **BtsCatalogExplorer** and **SendPortGroup** classes from the **Microsoft.BizTalk.ExplorerOM** namespace to manage send port groups in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span> <span data-ttu-id="c5f89-110">此範例以 Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c5f89-110">The sample is written in Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)].</span></span> <span data-ttu-id="c5f89-111">本主題也包含 Windows PowerShell 範例指令碼。</span><span class="sxs-lookup"><span data-stu-id="c5f89-111">A Windows PowerShell example script is also included in this topic.</span></span> <span data-ttu-id="c5f89-112">此範例會示範下列作業：</span><span class="sxs-lookup"><span data-stu-id="c5f89-112">The sample demonstrates the following operations:</span></span>  
  
-   <span data-ttu-id="c5f89-113">使用連接到 「 BizTalk 管理 」 資料庫**BtsCatalogExplorer**類別。</span><span class="sxs-lookup"><span data-stu-id="c5f89-113">Connecting to the BizTalk Management database by using the **BtsCatalogExplorer** class.</span></span>  
  
-   <span data-ttu-id="c5f89-114">建立新的傳送埠群組，名為 「 我將傳送埠群組 」。</span><span class="sxs-lookup"><span data-stu-id="c5f89-114">Creating a new send port group named “My Send Port Group”.</span></span>  
  
-   <span data-ttu-id="c5f89-115">列舉的傳送埠群組，以顯示新建立傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="c5f89-115">Enumerating send port groups to display the newly created send port group.</span></span>  
  
-   <span data-ttu-id="c5f89-116">正在刪除新的傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="c5f89-116">Deleting the new send port group.</span></span>  
  
 <span data-ttu-id="c5f89-117">其他函式會在此範例，但不是會在執行[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]版本。</span><span class="sxs-lookup"><span data-stu-id="c5f89-117">Additional functions are present in the sample but are not executed in the [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)] version.</span></span>  <span data-ttu-id="c5f89-118">PowerShell 範例指令碼將示範一些額外的函式。</span><span class="sxs-lookup"><span data-stu-id="c5f89-118">Some of the additional functions are demonstrated in the PowerShell example script.</span></span> <span data-ttu-id="c5f89-119">其他函式將示範下列功能：</span><span class="sxs-lookup"><span data-stu-id="c5f89-119">The additional functions demonstrate the following functionality:</span></span>  
  
-   <span data-ttu-id="c5f89-120">將傳送埠加入至新建立的傳送埠群組 （涵蓋在 PowerShell 範例）。</span><span class="sxs-lookup"><span data-stu-id="c5f89-120">Adding a send port to the newly created send port group (covered in the PowerShell example).</span></span>  
  
-   <span data-ttu-id="c5f89-121">從傳送埠群組 （涵蓋在 PowerShell 範例） 刪除傳送埠。</span><span class="sxs-lookup"><span data-stu-id="c5f89-121">Deleting a send port from the send port group (covered in the PowerShell example).</span></span>  
  
-   <span data-ttu-id="c5f89-122">啟動傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="c5f89-122">Starting the send port group.</span></span>  
  
-   <span data-ttu-id="c5f89-123">停止傳送埠群組。</span><span class="sxs-lookup"><span data-stu-id="c5f89-123">Stopping the send port group.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="c5f89-124">此範例的位置</span><span class="sxs-lookup"><span data-stu-id="c5f89-124">Where To Find This Sample</span></span>  
 <span data-ttu-id="c5f89-125">這個範例位於下列 SDK 位置：</span><span class="sxs-lookup"><span data-stu-id="c5f89-125">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="c5f89-126">\<*範例路徑*\>\Admin\ExplorerOM\SendPortGroups</span><span class="sxs-lookup"><span data-stu-id="c5f89-126">\<*Samples Path*\>\Admin\ExplorerOM\SendPortGroups</span></span>  
  
 <span data-ttu-id="c5f89-127">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="c5f89-127">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="c5f89-128">檔案</span><span class="sxs-lookup"><span data-stu-id="c5f89-128">File(s)</span></span>|<span data-ttu-id="c5f89-129">Description</span><span class="sxs-lookup"><span data-stu-id="c5f89-129">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5f89-130">SendPortGroups.cs</span><span class="sxs-lookup"><span data-stu-id="c5f89-130">SendPortGroups.cs</span></span>|[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]<span data-ttu-id="c5f89-131">這個範例中示範的作業的來源檔案。</span><span class="sxs-lookup"><span data-stu-id="c5f89-131"> source file for operations demonstrated in this sample.</span></span>|  
|<span data-ttu-id="c5f89-132">SendPortGroups.sln，SendPortGroups.csproj，SendPortGroups.suo</span><span class="sxs-lookup"><span data-stu-id="c5f89-132">SendPortGroups.sln, SendPortGroups.csproj, SendPortGroups.suo</span></span>|<span data-ttu-id="c5f89-133">此範例的方案和專案檔。</span><span class="sxs-lookup"><span data-stu-id="c5f89-133">Solution and project files for the sample.</span></span>|  
  
## <a name="building-and-running-this-sample"></a><span data-ttu-id="c5f89-134">建置和執行此範例</span><span class="sxs-lookup"><span data-stu-id="c5f89-134">Building and Running This Sample</span></span>  
  
#### <a name="to-build-this-sample"></a><span data-ttu-id="c5f89-135">建置此範例</span><span class="sxs-lookup"><span data-stu-id="c5f89-135">To build this sample</span></span>  
  
1.  <span data-ttu-id="c5f89-136">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟方案檔 SendPortGroups.sln。</span><span class="sxs-lookup"><span data-stu-id="c5f89-136">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file SendPortGroups.sln.</span></span>  
  
2.  <span data-ttu-id="c5f89-137">在 [方案總管] 中，按兩下**SendPortGroups.cs**開啟範例程式碼。</span><span class="sxs-lookup"><span data-stu-id="c5f89-137">In Solution Explorer, double click **SendPortGroups.cs** to open the sample code.</span></span>  
  
3.  <span data-ttu-id="c5f89-138">尋找`root.ConnectionString`中`CreateSendPortGroup`函式。</span><span class="sxs-lookup"><span data-stu-id="c5f89-138">Find the `root.ConnectionString` in the `CreateSendPortGroup` function.</span></span>  <span data-ttu-id="c5f89-139">您必須變更為正確地指向裝載 BizTalk 管理資料庫的 SQL server 的伺服器規格。</span><span class="sxs-lookup"><span data-stu-id="c5f89-139">You must change the server specification to correctly point to the SQL server hosting your BizTalk Management database.</span></span>  <span data-ttu-id="c5f89-140">您也可以使用句號 （.） 來連接到本機 SQL server。</span><span class="sxs-lookup"><span data-stu-id="c5f89-140">You can also use a period (.) to connect to the local SQL server.</span></span>  <span data-ttu-id="c5f89-141">例如：</span><span class="sxs-lookup"><span data-stu-id="c5f89-141">For example:</span></span>  
  
    ```  
    root.ConnectionString = "Integrated Security=SSPI;database=BizTalkMgmtDb;server=.";  
    ```  
  
4.  <span data-ttu-id="c5f89-142">重複步驟 3 來執行下列功能：</span><span class="sxs-lookup"><span data-stu-id="c5f89-142">Repeat step 3 for the following functions:</span></span>  
  
    -   <span data-ttu-id="c5f89-143">**EnumerateSendPortGroups**</span><span class="sxs-lookup"><span data-stu-id="c5f89-143">**EnumerateSendPortGroups**</span></span>  
  
    -   <span data-ttu-id="c5f89-144">**DeleteSendPortGroup**</span><span class="sxs-lookup"><span data-stu-id="c5f89-144">**DeleteSendPortGroup**</span></span>  
  
5.  <span data-ttu-id="c5f89-145">儲存**SendPortGroups.cs**。</span><span class="sxs-lookup"><span data-stu-id="c5f89-145">Save **SendPortGroups.cs**.</span></span>  
  
6.  <span data-ttu-id="c5f89-146">在主功能表中，按一下 **建置**，然後按一下 **建置方案**。</span><span class="sxs-lookup"><span data-stu-id="c5f89-146">On the main menu, click **Build**, and then click **Build Solution**.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="c5f89-147">執行此範例</span><span class="sxs-lookup"><span data-stu-id="c5f89-147">To run this sample</span></span>  
  
1.  <span data-ttu-id="c5f89-148">開啟命令視窗並巡覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="c5f89-148">Open a command window and navigate to the following folder:</span></span>  
  
     <span data-ttu-id="c5f89-149">\<*範例路徑*\>\Admin\ExplorerOM\SendPortGroups\bin\Debug</span><span class="sxs-lookup"><span data-stu-id="c5f89-149">\<*Samples Path*\>\Admin\ExplorerOM\SendPortGroups\bin\Debug</span></span>  
  
2.  <span data-ttu-id="c5f89-150">執行檔案 SendPortGroups.exe。</span><span class="sxs-lookup"><span data-stu-id="c5f89-150">Run the file SendPortGroups.exe.</span></span>  
  
## <a name="windows-powershell-script-example"></a><span data-ttu-id="c5f89-151">Windows PowerShell 指令碼範例</span><span class="sxs-lookup"><span data-stu-id="c5f89-151">Windows PowerShell Script Example</span></span>  
 <span data-ttu-id="c5f89-152">下列 Windows PowerShell 指令碼片段可以用來示範的相同功能**ExplorerOM**類別：</span><span class="sxs-lookup"><span data-stu-id="c5f89-152">The following Windows PowerShell script fragment can be used to demonstrate the same features of the **ExplorerOM** classes:</span></span>  
  
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
  
 <span data-ttu-id="c5f89-153">以下是範例預期從執行 Windows PowerShell 指令碼範例的輸出。</span><span class="sxs-lookup"><span data-stu-id="c5f89-153">Here is example expected output from running the Windows PowerShell script sample.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5f89-154">請參閱</span><span class="sxs-lookup"><span data-stu-id="c5f89-154">See Also</span></span>  
 [<span data-ttu-id="c5f89-155">Admin-ExplorerOM (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="c5f89-155">Admin-ExplorerOM (BizTalk Server Samples Folder)</span></span>](../core/admin-explorerom-biztalk-server-samples-folder.md)