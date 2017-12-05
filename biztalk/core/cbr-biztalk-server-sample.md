---
title: "CBR （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: add16683-4090-4854-8d6e-923b58937e9d
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30811b4f0dba463d518bdd9cd8f6d227e0e79aac
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="cbr-biztalk-server-sample"></a><span data-ttu-id="ab87d-102">CBR （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="ab87d-102">CBR (BizTalk Server Sample)</span></span>
<span data-ttu-id="ab87d-103">CBR 範例將示範如何使用**ExplorerOM**系統管理物件來加入和設定新傳送埠的 BizTalk 訊息的內容為基礎的路由。</span><span class="sxs-lookup"><span data-stu-id="ab87d-103">The CBR sample demonstrates using the **ExplorerOM** administrative objects to add and configure new send ports for content-based routing of BizTalk messages.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ab87d-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="ab87d-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="ab87d-105">這個範例需要，藉由執行中的 setup.bat 部署 CBRSample \<*範例路徑*\>\Messaging\CBRSample 目錄。</span><span class="sxs-lookup"><span data-stu-id="ab87d-105">This sample requires that the CBRSample be deployed by running setup.bat located in the \<*Samples Path*\>\Messaging\CBRSample directory.</span></span>  
  
-   <span data-ttu-id="ab87d-106">您必須擁有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在此範例中使用的系統管理物件的系統管理權限。</span><span class="sxs-lookup"><span data-stu-id="ab87d-106">You must have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administrative privileges to use the administrative objects in this sample.</span></span>  
  
-   <span data-ttu-id="ab87d-107">Windows PowerShell 指令碼範例需要 Windows PowerShell 執行原則來允許指令碼執行。</span><span class="sxs-lookup"><span data-stu-id="ab87d-107">The Windows PowerShell script example requires the Windows PowerShell execution policy to allow script execution.</span></span> <span data-ttu-id="ab87d-108">如需詳細資訊，請參閱：[檢查執行原則](http://go.microsoft.com/fwlink/?LinkId=128930)。</span><span class="sxs-lookup"><span data-stu-id="ab87d-108">For more information see: [Examining the Execution Policy](http://go.microsoft.com/fwlink/?LinkId=128930).</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="ab87d-109">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="ab87d-109">What This Sample Does</span></span>  
 <span data-ttu-id="ab87d-110">這個範例示範如何使用中的系統管理物件**Microsoft.BizTalk.ExplorerOM** CBRApplication 範例中加入兩個新的連接埠的命名空間。</span><span class="sxs-lookup"><span data-stu-id="ab87d-110">This sample demonstrates using the administrative objects in the **Microsoft.BizTalk.ExplorerOM** namespace to add two new ports to the CBRApplication sample.</span></span> <span data-ttu-id="ab87d-111">這些新的連接埠是 CBRApplication 的範例連接埠。</span><span class="sxs-lookup"><span data-stu-id="ab87d-111">These new ports are example ports for CBRApplication.</span></span> <span data-ttu-id="ab87d-112">連接埠會使用 HTTP 配接器將訊息路由至假設 HTTP Web 服務位址設定。</span><span class="sxs-lookup"><span data-stu-id="ab87d-112">The ports are configured to route messages to a hypothetical HTTP Web service address by using the HTTP adapter.</span></span> <span data-ttu-id="ab87d-113">此範例會使用 **ExplorerOM** 物件示範下列作業：</span><span class="sxs-lookup"><span data-stu-id="ab87d-113">The sample demonstrates the following operations using the **ExplorerOM** objects:</span></span>  
  
-   <span data-ttu-id="ab87d-114">使用**AddNewSendPort**方法**應用程式**来加入新的傳送埠，呼叫以 CBRApplication SendportUSOrders 類別。</span><span class="sxs-lookup"><span data-stu-id="ab87d-114">Using the **AddNewSendPort** method of the **Application** class to add a new send port called SendportUSOrders to CBRApplication.</span></span> <span data-ttu-id="ab87d-115">連接埠設定為使用 HTTP 配接器與假設性的 Web 位址的傳輸。</span><span class="sxs-lookup"><span data-stu-id="ab87d-115">The port is configured to use the HTTP adapter for transport with a hypothetical Web address.</span></span>  
  
-   <span data-ttu-id="ab87d-116">將篩選加入至 SendportUSOrders 訂閱 CBRApplication 與在美國太平洋時區中的訊息國家/地區碼值為 100。</span><span class="sxs-lookup"><span data-stu-id="ab87d-116">Adding a filter to SendportUSOrders that subscribes to messages in CBRApplication with the U.S. Country Code value of 100.</span></span>  
  
-   <span data-ttu-id="ab87d-117">加入輸出對應來 SendportUSOrders CBRApplication 對應轉換美國為基礎的訊息。</span><span class="sxs-lookup"><span data-stu-id="ab87d-117">Adding the CBRApplication map for transforming U.S.-based messages to the outbound maps for SendportUSOrders.</span></span>  
  
-   <span data-ttu-id="ab87d-118">加入新的傳送埠呼叫 SendportCANOrders CBRApplication 及設定它使用 HTTP 配接器與假設性的 Web 位址的傳輸。</span><span class="sxs-lookup"><span data-stu-id="ab87d-118">Adding a new send port called SendportCANOrders to CBRApplication and configuring it to use the HTTP adapter for transport with a hypothetical Web address.</span></span>  
  
-   <span data-ttu-id="ab87d-119">將篩選加入至 SendportCANOrders 訂閱中 CBRApplication 加拿大的國碼/地區碼值為 200 的訊息。</span><span class="sxs-lookup"><span data-stu-id="ab87d-119">Adding a filter to SendportCANOrders that subscribes to messages in CBRApplication with the Canada Country Code value of 200.</span></span>  
  
-   <span data-ttu-id="ab87d-120">加入輸出對應來 SendportCANOrders CBRApplication 對應轉換加拿大為基礎的訊息。</span><span class="sxs-lookup"><span data-stu-id="ab87d-120">Adding the CBRApplication map for transforming Canadian-based messages to the outbound maps for SendportCANOrders.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="ab87d-121">此範例的位置</span><span class="sxs-lookup"><span data-stu-id="ab87d-121">Where To Find This Sample</span></span>  
 <span data-ttu-id="ab87d-122">這個範例位於下列 SDK 位置：</span><span class="sxs-lookup"><span data-stu-id="ab87d-122">The sample is located in the following SDK location:</span></span>  
  
 <span data-ttu-id="ab87d-123">\<*範例路徑*\>\Admin\ExplorerOM\CBR</span><span class="sxs-lookup"><span data-stu-id="ab87d-123">\<*Samples Path*\>\Admin\ExplorerOM\CBR</span></span>  
  
 <span data-ttu-id="ab87d-124">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="ab87d-124">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="ab87d-125">檔案</span><span class="sxs-lookup"><span data-stu-id="ab87d-125">File(s)</span></span>|<span data-ttu-id="ab87d-126">Description</span><span class="sxs-lookup"><span data-stu-id="ab87d-126">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ab87d-127">ContentBasedRouting.cs</span><span class="sxs-lookup"><span data-stu-id="ab87d-127">ContentBasedRouting.cs</span></span>|[!INCLUDE[btsVCSharp](../includes/btsvcsharp-md.md)]<span data-ttu-id="ab87d-128">這個範例中示範的作業的來源檔案。</span><span class="sxs-lookup"><span data-stu-id="ab87d-128"> source file for operations demonstrated in this sample.</span></span>|  
|<span data-ttu-id="ab87d-129">CBR.sln，CBR.csproj，CBR.suo</span><span class="sxs-lookup"><span data-stu-id="ab87d-129">CBR.sln, CBR.csproj, CBR.suo</span></span>|<span data-ttu-id="ab87d-130">此範例的方案和專案檔。</span><span class="sxs-lookup"><span data-stu-id="ab87d-130">Solution and project files for the sample.</span></span>|  
  
## <a name="building-and-running-this-sample"></a><span data-ttu-id="ab87d-131">建置和執行此範例</span><span class="sxs-lookup"><span data-stu-id="ab87d-131">Building and Running This Sample</span></span>  
  
#### <a name="to-build-this-sample"></a><span data-ttu-id="ab87d-132">建置此範例</span><span class="sxs-lookup"><span data-stu-id="ab87d-132">To build this sample</span></span>  
  
1.  <span data-ttu-id="ab87d-133">請確定您已完成建置、 部署和設定 CBRSample 的步驟。</span><span class="sxs-lookup"><span data-stu-id="ab87d-133">Make sure you have completed the steps for building, deploying, and configuring the CBRSample.</span></span> <span data-ttu-id="ab87d-134">這些步驟中提供[CBRSample （BizTalk Server 範例）](../core/cbrsample-biztalk-server-sample.md)。</span><span class="sxs-lookup"><span data-stu-id="ab87d-134">Those steps are provided in [CBRSample (BizTalk Server Sample)](../core/cbrsample-biztalk-server-sample.md).</span></span>  
  
2.  <span data-ttu-id="ab87d-135">在[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，開啟方案檔 CBR.sln。</span><span class="sxs-lookup"><span data-stu-id="ab87d-135">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open the solution file CBR.sln.</span></span>  
  
3.  <span data-ttu-id="ab87d-136">按一下 [ **建置** ] 功能表上的 [ **建置方案**]。</span><span class="sxs-lookup"><span data-stu-id="ab87d-136">On the **Build** menu, click **Build Solution**.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="ab87d-137">執行此範例</span><span class="sxs-lookup"><span data-stu-id="ab87d-137">To run this sample</span></span>  
  
1.  <span data-ttu-id="ab87d-138">開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]系統管理主控台並瀏覽至**CBRApplication**節點。</span><span class="sxs-lookup"><span data-stu-id="ab87d-138">Open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console and navigate to the **CBRApplication** node.</span></span>  
  
2.  <span data-ttu-id="ab87d-139">展開**CBRApplication**節點可讓您確認**傳送埠**節點目前已列為 [cbrussendport] 和 [cbrcansendport] 只有兩個連接埠。</span><span class="sxs-lookup"><span data-stu-id="ab87d-139">Expand the **CBRApplication** node to verify that the **Send Ports** node currently has only two ports listed as CBRUSSendPort and CBRCANSendPort.</span></span>  
  
3.  <span data-ttu-id="ab87d-140">開啟命令視窗並巡覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="ab87d-140">Open a command window and navigate to the following folder:</span></span>  
  
     <span data-ttu-id="ab87d-141">\<*範例路徑*\>\Admin\ExplorerOM\CBR\bin\Debug</span><span class="sxs-lookup"><span data-stu-id="ab87d-141">\<*Samples Path*\>\Admin\ExplorerOM\CBR\bin\Debug</span></span>  
  
4.  <span data-ttu-id="ab87d-142">執行檔案 CBR.exe。</span><span class="sxs-lookup"><span data-stu-id="ab87d-142">Run the file CBR.exe.</span></span>  
  
5.  <span data-ttu-id="ab87d-143">按 f5 鍵在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台來重新整理 下的檢視**傳送埠**節點。</span><span class="sxs-lookup"><span data-stu-id="ab87d-143">Press F5 in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console to refresh the view under the **Send Ports** node.</span></span> <span data-ttu-id="ab87d-144">您現在應該會看到兩個新連接埠新增至 CBRApplication 此範例。</span><span class="sxs-lookup"><span data-stu-id="ab87d-144">You should now see the two new ports added to CBRApplication by this sample.</span></span> <span data-ttu-id="ab87d-145">它們稱為 SendportUSOrders 和 SendportCANOrders。</span><span class="sxs-lookup"><span data-stu-id="ab87d-145">They are called SendportUSOrders and SendportCANOrders.</span></span>  
  
## <a name="windows-powershell-script-example"></a><span data-ttu-id="ab87d-146">Windows PowerShell 指令碼範例</span><span class="sxs-lookup"><span data-stu-id="ab87d-146">Windows PowerShell Script Example</span></span>  
 <span data-ttu-id="ab87d-147">下列 Windows PowerShell 指令碼可以用來示範 **ExplorerOM** 類別的相同功能。</span><span class="sxs-lookup"><span data-stu-id="ab87d-147">The following Windows PowerShell script can be used to demonstrate the same features of the **ExplorerOM** classes.</span></span> <span data-ttu-id="ab87d-148">不過，因為**新增**方法**SendPort.OutboundTranforms**集合標記中的內部**ExplorerOM**不能直接從呼叫的組件Windows PowerShell。</span><span class="sxs-lookup"><span data-stu-id="ab87d-148">However, because the **Add** method for the **SendPort.OutboundTranforms** collection is marked Internal in the **ExplorerOM** assembly it cannot be called directly from Windows PowerShell.</span></span> <span data-ttu-id="ab87d-149">此 Windows PowerShell 指令碼示範如何使用 BizTalk WMI 提供者，從 Windows PowerShell 輸出的轉換地圖加入至新的連接埠。</span><span class="sxs-lookup"><span data-stu-id="ab87d-149">This Windows PowerShell script demonstrates using the BizTalk WMI Provider from Windows PowerShell to add the outbound transform map to the new port.</span></span>  
  
```  
Function WMI_AddOutboundTransformToPort($transform,$strPortName)  
{  
    Write-Host "WMI Processing Transform...`r`nPortName `:"$strPortName  
    Write-Host "Transform `:"$transform.AssemblyQualifiedName  
  
    $WMIsendport = get-wmiobject MSBTS_SendPort -filter "Name=`"$strPortName`"" -namespace root\microsoftbiztalkserver  
    $WMIsendport.OutboundTransforms = $transform.AssemblyQualifiedName  
    [Void] $WMIsendport.Put()  
    [Void] $WMIsendport.Start()  
}  
  
#===================#  
#=== Main Script ===#  
#===================#  
  
#=== Make sure the ExplorerOM assembly is loaded ===#  
  
[void] [System.reflection.Assembly]::LoadWithPartialName("Microsoft.BizTalk.ExplorerOM")  
  
#=== Connect to the BizTalk Management database ===#  
  
$Catalog = New-Object Microsoft.BizTalk.ExplorerOM.BtsCatalogExplorer  
$Catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI"  
  
$CBRApp = $Catalog.Applications["CBRApplication"]  
  
if ($CBRApp -eq $null)  
{  
    Write-Host "`r`nFailed to find `"CBRApplication`" deployed on this BizTalk server."  
    Write-Host "You must deploy the SDK\Samples\Messaging\CBRSample in order to test this script.`r`n"  
}  
else  
{  
    #=== Register a trap handler for any exceptions ===#  
    $ErrorActionPreference="silentlycontinue"  
    trap { "Exception encountered:`r`n"; $_; "`r`nDiscarding Changes.`r`n";$Catalog.DiscardChanges();exit; }  
  
    #===================================#  
    #=== Create the U.S. Orders Port ===#  
    #===================================#  
  
    $USPort = $CBRApp.AddNewSendPort($false,$false)  
    $USPort.Name = "SendportUSOrders"  
    $USPort.PrimaryTransport.TransportType = $Catalog.ProtocolTypes["HTTP"]  
    $USPort.PrimaryTransport.Address = "http://process_orders_US.asp"  
    $USPort.SendPipeline = $Catalog.Pipelines["Microsoft.BizTalk.DefaultPipelines.XMLTransmit"]  
  
    #=== add the filter to subscribe to messages with U.S country code 100 ===#  
  
    $USPort.Filter = "<Filter><Group>" +  
                     "<Statement Property='BTS.ReceivePortName' Operator='0' Value='ReceivePortPO'/>" +   
                     "<Statement Property='CBRSample.CountryCode' Operator='0' Value='100'/>" +  
                     "</Group></Filter>"  
  
    Write-Host("`r`nAdding " + $UsPort.Name + " to catalog ...")  
    $Catalog.SaveChanges()  
  
    #=========================================================================================#  
    #=== SendPortTranformCollection::Add is marked internal in ExplorerOM for some reason. ===#  
    #=== Use WMI to set this as a workaround through PowerShell.                           ===#  
    #=========================================================================================#  
  
    WMI_AddOutboundTransformToPort $Catalog.Transforms["CBRSample.CBRInput2USMap"] $USport.Name  
  
    #=====================================#  
    #=== Create the Canada Orders Port ===#  
    #=====================================#  
  
    $CanadaPort = $CBRApp.AddNewSendPort($false,$false)  
    $CanadaPort.Name = "SendportCANOrders"  
    $CanadaPort.PrimaryTransport.TransportType = $Catalog.ProtocolTypes["HTTP"]  
    $CanadaPort.PrimaryTransport.Address = "http://process_orders_CAN.asp"  
    $CanadaPort.SendPipeline = $Catalog.Pipelines["Microsoft.BizTalk.DefaultPipelines.XMLTransmit"]  
  
    #=== add the filter to subscribe to messages with U.S country code 100 ===#  
  
    $CanadaPort.Filter = "<Filter><Group>" +  
                     "<Statement Property='BTS.ReceivePortName' Operator='0' Value='ReceivePortPO'/>" +   
                     "<Statement Property='CBRSample.CountryCode' Operator='0' Value='200'/>" +  
                     "</Group></Filter>"  
  
    Write-Host("`r`nAdding " + $UsPort.Name + " to catalog ...")  
    $Catalog.SaveChanges()  
  
    #=========================================================================================#  
    #=== SendPortTranformCollection::Add is marked internal in ExplorerOM for some reason. ===#  
    #=== Use WMI to set this as a workaround through PowerShell.                           ===#  
    #=========================================================================================#  
  
    WMI_AddOutboundTransformToPort $Catalog.Transforms["CBRSample.CBRInput2CANMap"] $CanadaPort.Name  
  
    Write-Host  
}  
```  
  
 <span data-ttu-id="ab87d-150">以下是執行 Windows PowerShell 指令碼來建立兩個新的連接埠的輸出範例。</span><span class="sxs-lookup"><span data-stu-id="ab87d-150">Here is an example output from running the Windows PowerShell script to create the two new ports.</span></span> <span data-ttu-id="ab87d-151">新的連接埠也可以驗證在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台，如上面所述。</span><span class="sxs-lookup"><span data-stu-id="ab87d-151">The new ports can also be verified in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console as mentioned above.</span></span>  
  
```  
PS C:\> .\CBR.ps1  
  
Adding SendportUSOrders to catalog ...  
WMI Processing Transform...  
PortName : SendportUSOrders  
Transform : CBRSample.CBRInput2USMap,CBRSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=ba2e1651515c6db7  
  
Adding SendportUSOrders to catalog ...  
WMI Processing Transform...  
PortName : SendportCANOrders  
Transform : CBRSample.CBRInput2CANMap,CBRSample, Version=1.0.0.0, Culture=neutral, PublicKeyToken=ba2e1651515c6db7  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab87d-152">請參閱</span><span class="sxs-lookup"><span data-stu-id="ab87d-152">See Also</span></span>  
 <span data-ttu-id="ab87d-153">[系統管理員 ExplorerOM （BizTalk Server 範例資料夾）](../core/admin-explorerom-biztalk-server-samples-folder.md) </span><span class="sxs-lookup"><span data-stu-id="ab87d-153">[Admin-ExplorerOM (BizTalk Server Samples Folder)](../core/admin-explorerom-biztalk-server-samples-folder.md) </span></span>  
 [<span data-ttu-id="ab87d-154">CBRSample (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="ab87d-154">CBRSample (BizTalk Server Sample)</span></span>](../core/cbrsample-biztalk-server-sample.md)