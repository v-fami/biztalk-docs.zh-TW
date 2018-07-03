---
title: ReceivePorts （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c403005d-5e0e-4015-b138-6318e03192af
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06925777afa60ee6b11d42a17bac004665cfe7ec
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37023916"
---
# <a name="receiveports-biztalk-server-sample"></a><span data-ttu-id="c40aa-102">ReceivePorts （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="c40aa-102">ReceivePorts (BizTalk Server Sample)</span></span>
<span data-ttu-id="c40aa-103">ReceivePorts 範例示範如何建立新接收埠，使用**ExplorerOM**系統管理類別。</span><span class="sxs-lookup"><span data-stu-id="c40aa-103">The ReceivePorts sample demonstrates how to create a new receive port by using the **ExplorerOM** administrative classes.</span></span>  

## <a name="prerequisites"></a><span data-ttu-id="c40aa-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="c40aa-104">Prerequisites</span></span>  

- <span data-ttu-id="c40aa-105">您必須擁有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理權限才能在此範例中使用的系統管理物件。</span><span class="sxs-lookup"><span data-stu-id="c40aa-105">You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.</span></span>  

- <span data-ttu-id="c40aa-106">Windows PowerShell 指令碼需要 Windows PowerShell 執行原則，以允許執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="c40aa-106">The Windows PowerShell script requires the Windows PowerShell execution policy to allow script execution.</span></span> <span data-ttu-id="c40aa-107">如需詳細資訊，請參閱 [檢查執行原則](http://go.microsoft.com/fwlink/?LinkId=128930)。</span><span class="sxs-lookup"><span data-stu-id="c40aa-107">For more information see [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).</span></span>  

## <a name="what-this-sample-does"></a><span data-ttu-id="c40aa-108">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="c40aa-108">What This Sample Does</span></span>  
 <span data-ttu-id="c40aa-109">此範例示範如何使用**BtsCatalogExplorer**並**ReceivePort**類別**Microsoft.BizTalk.ExplorerOM**加入新的命名空間接收埠以[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c40aa-109">This sample demonstrates using the **BtsCatalogExplorer** and **ReceivePort** classes from the **Microsoft.BizTalk.ExplorerOM** namespace to add a new receive port to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="c40aa-110">此範例以 Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c40aa-110">The sample is written in Microsoft [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)].</span></span> <span data-ttu-id="c40aa-111">本主題也包含 Windows PowerShell 範例指令碼。</span><span class="sxs-lookup"><span data-stu-id="c40aa-111">A Windows PowerShell example script is also included in this topic.</span></span> <span data-ttu-id="c40aa-112">此範例會示範下列作業：</span><span class="sxs-lookup"><span data-stu-id="c40aa-112">The sample demonstrates the following operations:</span></span>  

-   <span data-ttu-id="c40aa-113">使用連接到 「 BizTalk 管理 」 資料庫**BtsCatalogExplorer**類別。</span><span class="sxs-lookup"><span data-stu-id="c40aa-113">Connecting to the BizTalk Management database by using the **BtsCatalogExplorer** class.</span></span>  

-   <span data-ttu-id="c40aa-114">加入新接收埠，使用**AddNewReceivePort**方法。</span><span class="sxs-lookup"><span data-stu-id="c40aa-114">Adding a new receive port by using the **AddNewReceivePort** method.</span></span>  

-   <span data-ttu-id="c40aa-115">列舉接收埠。</span><span class="sxs-lookup"><span data-stu-id="c40aa-115">Enumerating receive ports.</span></span>  

-   <span data-ttu-id="c40aa-116">刪除接收埠。</span><span class="sxs-lookup"><span data-stu-id="c40aa-116">Deleting receive ports.</span></span>  

## <a name="where-to-find-this-sample"></a><span data-ttu-id="c40aa-117">此範例的位置</span><span class="sxs-lookup"><span data-stu-id="c40aa-117">Where To Find This Sample</span></span>  
 <span data-ttu-id="c40aa-118">這個範例位於下列 SDK 位置：</span><span class="sxs-lookup"><span data-stu-id="c40aa-118">The sample is located in the following SDK location:</span></span>  

 <span data-ttu-id="c40aa-119">\<*範例路徑*\>\Admin\ExplorerOM\ReceivePorts</span><span class="sxs-lookup"><span data-stu-id="c40aa-119">\<*Samples Path*\>\Admin\ExplorerOM\ReceivePorts</span></span>  

 <span data-ttu-id="c40aa-120">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="c40aa-120">The following table shows the files in this sample and describes their purpose.</span></span>  


|                 <span data-ttu-id="c40aa-121">檔案</span><span class="sxs-lookup"><span data-stu-id="c40aa-121">File(s)</span></span>                  |                                                 <span data-ttu-id="c40aa-122">描述</span><span class="sxs-lookup"><span data-stu-id="c40aa-122">Description</span></span>                                                  |
|------------------------------------------|--------------------------------------------------------------------------------------------------------------|
|             <span data-ttu-id="c40aa-123">ReceivePorts.cs</span><span class="sxs-lookup"><span data-stu-id="c40aa-123">ReceivePorts.cs</span></span>              | [!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]<span data-ttu-id="c40aa-124"> 此範例中示範的作業的原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="c40aa-124"> source file for operations demonstrated in this sample.</span></span> |
| <span data-ttu-id="c40aa-125">ReceivePorts.sln 和 ReceivePorts.csproj</span><span class="sxs-lookup"><span data-stu-id="c40aa-125">ReceivePorts.sln and ReceivePorts.csproj</span></span> |                                  <span data-ttu-id="c40aa-126">此範例的方案和專案檔案。</span><span class="sxs-lookup"><span data-stu-id="c40aa-126">Solution and project file for the sample.</span></span>                                   |

## <a name="building-and-running-this-sample"></a><span data-ttu-id="c40aa-127">建置和執行此範例</span><span class="sxs-lookup"><span data-stu-id="c40aa-127">Building and Running This Sample</span></span>  

#### <a name="to-build-this-sample"></a><span data-ttu-id="c40aa-128">建置此範例</span><span class="sxs-lookup"><span data-stu-id="c40aa-128">To build this sample</span></span>  

1. <span data-ttu-id="c40aa-129">在  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟方案檔 ReceivePorts.sln。</span><span class="sxs-lookup"><span data-stu-id="c40aa-129">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file ReceivePorts.sln.</span></span>  

2. <span data-ttu-id="c40aa-130">按一下 [ **建置** ] 功能表上的 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="c40aa-130">On the **Build** menu, click **Build Solution**.</span></span>  

#### <a name="to-run-this-sample"></a><span data-ttu-id="c40aa-131">執行此範例</span><span class="sxs-lookup"><span data-stu-id="c40aa-131">To run this sample</span></span>  

1.  <span data-ttu-id="c40aa-132">開啟命令視窗並巡覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="c40aa-132">Open a command window and navigate to the following folder:</span></span>  

     <span data-ttu-id="c40aa-133">\<*範例路徑*\>\Admin\ExplorerOM\ReceivePorts\bin\Debug</span><span class="sxs-lookup"><span data-stu-id="c40aa-133">\<*Samples Path*\>\Admin\ExplorerOM\ReceivePorts\bin\Debug</span></span>  

2.  <span data-ttu-id="c40aa-134">執行檔案 ReceivePorts.exe。</span><span class="sxs-lookup"><span data-stu-id="c40aa-134">Run the file ReceivePorts.exe.</span></span> <span data-ttu-id="c40aa-135">新接收埠可建立並顯示在連接埠的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="c40aa-135">The new receive port should be created and shown in the port enumeration.</span></span> <span data-ttu-id="c40aa-136">列舉型別之後，會立即移除接收埠。</span><span class="sxs-lookup"><span data-stu-id="c40aa-136">After the enumeration the receive port is immediately removed.</span></span>  

## <a name="windows-powershell-script-example"></a><span data-ttu-id="c40aa-137">Windows PowerShell 指令碼範例</span><span class="sxs-lookup"><span data-stu-id="c40aa-137">Windows PowerShell Script Example</span></span>  
 <span data-ttu-id="c40aa-138">下列 Windows PowerShell 範例指令碼可以用來示範相同的功能**ExplorerOM**類別：</span><span class="sxs-lookup"><span data-stu-id="c40aa-138">The following Windows PowerShell example script can be used to demonstrate the same features of the **ExplorerOM** classes:</span></span>  

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

 <span data-ttu-id="c40aa-139">以下是執行 Windows PowerShell 指令碼，來建立新的範例接收埠：</span><span class="sxs-lookup"><span data-stu-id="c40aa-139">Here is an example of running the Windows PowerShell script to create the new receive port:</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="c40aa-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c40aa-140">See Also</span></span>  
 [<span data-ttu-id="c40aa-141">Admin-ExplorerOM (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="c40aa-141">Admin-ExplorerOM (BizTalk Server Samples Folder)</span></span>](../core/admin-explorerom-biztalk-server-samples-folder.md)