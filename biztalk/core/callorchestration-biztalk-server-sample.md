---
title: "CallOrchestration （BizTalk Server 範例） |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, examples
- orchestrations, calling
- examples, orchestrations
ms.assetid: 0c4194f0-c1e2-419a-8a1a-a3c96e8d2667
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9cf37bd2b4ceacfe38736cadd8343b4259db126e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="callorchestration-biztalk-server-sample"></a><span data-ttu-id="d39a4-102">CallOrchestration （BizTalk Server 範例）</span><span class="sxs-lookup"><span data-stu-id="d39a4-102">CallOrchestration (BizTalk Server Sample)</span></span>
<span data-ttu-id="d39a4-103">CallOrchestration 範例示範如何從一個協調流程呼叫另一個 BizTalk 協調流程。</span><span class="sxs-lookup"><span data-stu-id="d39a4-103">The CallOrchestration sample demonstrates how to call one BizTalk orchestration from another orchestration.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="d39a4-104">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="d39a4-104">What This Sample Does</span></span>  
 <span data-ttu-id="d39a4-105">此範例示範使用下列步驟順序呼叫另一個協調流程的協調流程：</span><span class="sxs-lookup"><span data-stu-id="d39a4-105">This sample demonstrates one orchestration calling another orchestration using the following sequence of steps:</span></span>  
  
1.  <span data-ttu-id="d39a4-106">主要協調流程收到訂單 (PO) 訊息。</span><span class="sxs-lookup"><span data-stu-id="d39a4-106">The primary orchestration receives a purchase order (PO) message.</span></span>  
  
2.  <span data-ttu-id="d39a4-107">主要協調流程呼叫次要協調流程，以決定 PO 的出貨價格。</span><span class="sxs-lookup"><span data-stu-id="d39a4-107">The primary orchestration calls the secondary orchestration to determine the shipping price for the PO.</span></span>  
  
3.  <span data-ttu-id="d39a4-108">次要協調流程計算要求的出貨價格，然後將它傳回主要協調流程。</span><span class="sxs-lookup"><span data-stu-id="d39a4-108">The secondary orchestration calculates the requested shipping price and returns it to the primary orchestration.</span></span>  
  
4.  <span data-ttu-id="d39a4-109">主要協調流程使用傳回的出貨價格更新 PO 訊息。</span><span class="sxs-lookup"><span data-stu-id="d39a4-109">The primary orchestration updates the PO message with the returned shipping price.</span></span>  
  
5.  <span data-ttu-id="d39a4-110">主要協調流程將更新的 PO 訊息放到資料夾中供您檢閱。</span><span class="sxs-lookup"><span data-stu-id="d39a4-110">The primary orchestration puts the updated PO message into a folder for your inspection.</span></span>  
  
## <a name="how-this-sample-is-designed-and-why"></a><span data-ttu-id="d39a4-111">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="d39a4-111">How This Sample is Designed and Why</span></span>  
 <span data-ttu-id="d39a4-112">此範例的主要目的是為您顯示如何從一個協調流程呼叫另一個協調流程。</span><span class="sxs-lookup"><span data-stu-id="d39a4-112">The primary purpose of this sample is to show you how to call an orchestration from within another orchestration.</span></span> <span data-ttu-id="d39a4-113">呼叫協調流程的功能可讓您將商務程序切割為可重複使用的元件。</span><span class="sxs-lookup"><span data-stu-id="d39a4-113">The ability to call orchestrations gives you a way to divide your business processes into reusable components.</span></span> <span data-ttu-id="d39a4-114">您可將常用的程序列入個別的協調流程中，供其他人重複使用。</span><span class="sxs-lookup"><span data-stu-id="d39a4-114">You can factor your common processes out into separate orchestrations for others to re-use.</span></span>  
  
 <span data-ttu-id="d39a4-115">在此範例中，**呼叫協調流程**receivePO.odx 中的圖形叫用 findShippingPrice.odx，並會等待巢狀協調流程 findShippingPrice.odx 計算並傳送訂單之前傳回出貨價格順序。</span><span class="sxs-lookup"><span data-stu-id="d39a4-115">In this sample, the **Call Orchestration** shape in receivePO.odx invokes findShippingPrice.odx and waits for the nested orchestration, findShippingPrice.odx, to calculate and return the shipping price before sending the purchase order.</span></span> <span data-ttu-id="d39a4-116">協調流程 findShippingPrice.odx 使用下列邏輯計算出貨價格：</span><span class="sxs-lookup"><span data-stu-id="d39a4-116">The orchestration findShippingPrice.odx uses the following logic to calculate the shipping price:</span></span>  
  
```  
If ( weight * shippingRate ) < minShippingPrice Then  
    shippingPrice = minShippingPrice  
Else  
    shippingPrice = weight * shippingRate  
End If  
```  
  
 <span data-ttu-id="d39a4-117">範例 PO 輸入檔 InputPO.xml 指定重量為 20，使 PO 輸出訊息將其出貨價格從 10 變更為 20。</span><span class="sxs-lookup"><span data-stu-id="d39a4-117">The sample input PO file, InputPO.xml, specifies a weight of 20, resulting in the output PO message having its shipping price changed from 10 to 20.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d39a4-118">您無法從不可部分完成的協調流程呼叫執行時間很長的交易。</span><span class="sxs-lookup"><span data-stu-id="d39a4-118">You cannot call a long-running transaction from an atomic orchestration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d39a4-119">使用之間的差別**呼叫協調流程**圖形和**啟動協調流程**圖形是，在呼叫協調流程時，呼叫端會等待巢狀協調流程傳回之後，繼續進行。</span><span class="sxs-lookup"><span data-stu-id="d39a4-119">The difference between using the **Call Orchestration** shape and the **Start Orchestration** shape is that when calling an orchestration, the caller waits for the nested orchestration to return before continuing.</span></span> <span data-ttu-id="d39a4-120">若是從一個協調流程啟動另一個協調流程，在呼叫者初始化動作之後，呼叫者會繼續進行程序流程中的下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="d39a4-120">When starting an orchestration from an orchestration, after the caller initiates the action, the caller moves forward to the next step in the process flow.</span></span> <span data-ttu-id="d39a4-121">呼叫者所叫用的協調流程會獨立執行，直到完成程序流程。</span><span class="sxs-lookup"><span data-stu-id="d39a4-121">The orchestration that was invoked by the caller runs independently until it finishes the process flow.</span></span> <span data-ttu-id="d39a4-122">如需詳細資訊，請參閱[如何設定呼叫協調流程圖形](../core/how-to-configure-the-call-orchestration-shape.md)。</span><span class="sxs-lookup"><span data-stu-id="d39a4-122">For more information, see [How to Configure the Call Orchestration Shape](../core/how-to-configure-the-call-orchestration-shape.md).</span></span> <span data-ttu-id="d39a4-123">另請參閱[如何設定啟動協調流程圖形](../core/how-to-configure-the-start-orchestration-shape.md)。</span><span class="sxs-lookup"><span data-stu-id="d39a4-123">Also see [How to Configure the Start Orchestration Shape](../core/how-to-configure-the-start-orchestration-shape.md).</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="d39a4-124">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="d39a4-124">Where to Find This Sample</span></span>  
 <span data-ttu-id="d39a4-125">\<*範例路徑*\>\Orchestrations\CallOrchestration\\</span><span class="sxs-lookup"><span data-stu-id="d39a4-125">\<*Samples Path*\>\Orchestrations\CallOrchestration\\</span></span>  
  
 <span data-ttu-id="d39a4-126">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="d39a4-126">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|<span data-ttu-id="d39a4-127">檔案</span><span class="sxs-lookup"><span data-stu-id="d39a4-127">File(s)</span></span>|<span data-ttu-id="d39a4-128">Description</span><span class="sxs-lookup"><span data-stu-id="d39a4-128">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d39a4-129">CallOrchestration.btproj, CallOrchestration.sln</span><span class="sxs-lookup"><span data-stu-id="d39a4-129">CallOrchestration.btproj, CallOrchestration.sln</span></span>|<span data-ttu-id="d39a4-130">這個範例的專案及解決方案檔案。</span><span class="sxs-lookup"><span data-stu-id="d39a4-130">Project and solution files for this sample.</span></span>|  
|<span data-ttu-id="d39a4-131">CallOrchestrationBinding.xml</span><span class="sxs-lookup"><span data-stu-id="d39a4-131">CallOrchestrationBinding.xml</span></span>|<span data-ttu-id="d39a4-132">用於自動化設定，例如連接埠繫結。</span><span class="sxs-lookup"><span data-stu-id="d39a4-132">Used for automated setup such as port binding.</span></span>|  
|<span data-ttu-id="d39a4-133">Cleanup.bat</span><span class="sxs-lookup"><span data-stu-id="d39a4-133">Cleanup.bat</span></span>|<span data-ttu-id="d39a4-134">用來解除部署組件，以及將它從全域組件快取中移除。</span><span class="sxs-lookup"><span data-stu-id="d39a4-134">Used to undeploy assemblies and remove them from the global assembly cache.</span></span> <span data-ttu-id="d39a4-135">移除傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="d39a4-135">Removes send and receive ports.</span></span> <span data-ttu-id="d39a4-136">視需要移除 Microsoft Internet Information Services (IIS) 虛擬目錄。</span><span class="sxs-lookup"><span data-stu-id="d39a4-136">Removes Microsoft Internet Information Services (IIS) virtual directories as needed.</span></span>|  
|<span data-ttu-id="d39a4-137">findShippingPrice.odx</span><span class="sxs-lookup"><span data-stu-id="d39a4-137">findShippingPrice.odx</span></span>|<span data-ttu-id="d39a4-138">做為次要協調流程的 BizTalk 協調流程，從主要協調流程 receivePO.odx 呼叫。</span><span class="sxs-lookup"><span data-stu-id="d39a4-138">BizTalk orchestration that serves as a secondary orchestration, called from the primary orchestration, receivePO.odx.</span></span>|  
|<span data-ttu-id="d39a4-139">InputPO.xml</span><span class="sxs-lookup"><span data-stu-id="d39a4-139">InputPO.xml</span></span>|<span data-ttu-id="d39a4-140">符合 PO.xsd 檔案中定義之結構描述的範例 PO 輸入訊息。</span><span class="sxs-lookup"><span data-stu-id="d39a4-140">Sample input PO message that conforms to the schema defined in the file PO.xsd.</span></span>|  
|<span data-ttu-id="d39a4-141">PO.xsd</span><span class="sxs-lookup"><span data-stu-id="d39a4-141">PO.xsd</span></span>|<span data-ttu-id="d39a4-142">結構描述，定義範例輸入檔案 InputPO.xml 等 PO 輸入訊息的結構，以及定義結構描述中之三個項目的屬性升級。</span><span class="sxs-lookup"><span data-stu-id="d39a4-142">Schema that defines the structure of inbound PO messages such as the sample input file InputPO.xml, and defines property promotion for all three elements in the schema.</span></span>|  
|<span data-ttu-id="d39a4-143">PropertySchema.xsd</span><span class="sxs-lookup"><span data-stu-id="d39a4-143">PropertySchema.xsd</span></span>|<span data-ttu-id="d39a4-144">參與結構描述 PO.xsd 中之三個項目之屬性升級的屬性結構描述檔案。</span><span class="sxs-lookup"><span data-stu-id="d39a4-144">Property schema file that participates in property promotion for all three elements in the schema PO.xsd.</span></span>|  
|<span data-ttu-id="d39a4-145">receivePO.odx</span><span class="sxs-lookup"><span data-stu-id="d39a4-145">receivePO.odx</span></span>|<span data-ttu-id="d39a4-146">做為此範例中之主要協調流程的 BizTalk 協調流程。</span><span class="sxs-lookup"><span data-stu-id="d39a4-146">BizTalk orchestration that serves as the primary orchestration in this sample.</span></span> <span data-ttu-id="d39a4-147">它會從接收資料夾擷取 PO 訊息，然後呼叫另一個協調流程 findShippingPrice.odx，來計算和更新出貨價格。</span><span class="sxs-lookup"><span data-stu-id="d39a4-147">It retrieves PO messages from the receive folder and then calls the other orchestration, findShippingPrice.odx, to calculate and update the shipping price.</span></span>|  
|<span data-ttu-id="d39a4-148">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="d39a4-148">Setup.bat</span></span>|<span data-ttu-id="d39a4-149">用來建置和初始化此範例。</span><span class="sxs-lookup"><span data-stu-id="d39a4-149">Used to build and initialize this sample.</span></span>|  
  
## <a name="building-and-initializing-this-sample"></a><span data-ttu-id="d39a4-150">建置和初始化此範例</span><span class="sxs-lookup"><span data-stu-id="d39a4-150">Building and Initializing This Sample</span></span>  
  
#### <a name="to-build-and-initialize-the-callorchestration-sample"></a><span data-ttu-id="d39a4-151">建置和初始化 CallOrchestration 範例</span><span class="sxs-lookup"><span data-stu-id="d39a4-151">To build and initialize the CallOrchestration sample</span></span>  
  
1.  <span data-ttu-id="d39a4-152">在命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="d39a4-152">In a command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="d39a4-153">\<*範例路徑*\>\Orchestrations\CallOrchestration\\</span><span class="sxs-lookup"><span data-stu-id="d39a4-153">\<*Samples Path*\>\Orchestrations\CallOrchestration\\</span></span>  
  
2.  <span data-ttu-id="d39a4-154">執行檔案 Setup.bat，這會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d39a4-154">Run the file Setup.bat, which performs the following actions:</span></span>  
  
    -   <span data-ttu-id="d39a4-155">在 CallOrchestration 資料夾中建立此範例的輸入 (In) 和輸出 (Out) 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d39a4-155">Creates the input (In) and output (Out) folders for this sample in the CallOrchestration folder.</span></span>  
  
    -   <span data-ttu-id="d39a4-156">編譯並部署此範例的 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 專案，包括兩個協調流程。</span><span class="sxs-lookup"><span data-stu-id="d39a4-156">Compiles and deploys the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] project, containing both orchestrations, for this sample.</span></span>  
  
    -   <span data-ttu-id="d39a4-157">建立並繫結 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收位置，以及傳送埠和接收埠。</span><span class="sxs-lookup"><span data-stu-id="d39a4-157">Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports.</span></span>  
  
    -   <span data-ttu-id="d39a4-158">啟用接收位置並啟動傳送埠。</span><span class="sxs-lookup"><span data-stu-id="d39a4-158">Enables the receive location, and starts the send port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d39a4-159">在嘗試執行此範例之前，您必須確認 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 沒有在建置和初始化的程序中報告任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="d39a4-159">You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.</span></span>  
  
## <a name="running-this-sample"></a><span data-ttu-id="d39a4-160">執行此範例</span><span class="sxs-lookup"><span data-stu-id="d39a4-160">Running This Sample</span></span>  
  
#### <a name="to-run-the-callorchestration-sample"></a><span data-ttu-id="d39a4-161">執行 CallOrchestration 範例</span><span class="sxs-lookup"><span data-stu-id="d39a4-161">To run the CallOrchestration sample</span></span>  
  
1.  <span data-ttu-id="d39a4-162">將檔案 InputPO.xml 的複本放置到 In 資料夾。</span><span class="sxs-lookup"><span data-stu-id="d39a4-162">Put a copy of the file InputPO.xml into the In folder.</span></span>  
  
2.  <span data-ttu-id="d39a4-163">觀察在 Out 資料夾中建立的 XML PO 更新檔案。</span><span class="sxs-lookup"><span data-stu-id="d39a4-163">Observe the updated XML PO file created in the Out folder.</span></span> <span data-ttu-id="d39a4-164">它包含已修改的原始 PO 訊息，此訊息包括如上述說明中計算出的出貨成本。</span><span class="sxs-lookup"><span data-stu-id="d39a4-164">It contains the original PO message, modified to include a shipping cost calculated as explained earlier.</span></span> <span data-ttu-id="d39a4-165">這個檔案的名稱的格式是\< *MessageID*\>.xml，其中 *\<MessageID\>* 產生來唯一識別訊息的 GUID.</span><span class="sxs-lookup"><span data-stu-id="d39a4-165">The format of the name of this file is \<*MessageID*\>.xml, where *\<MessageID\>* is the GUID generated to uniquely identify the message.</span></span>  
  
## <a name="uninstalling-this-sample"></a><span data-ttu-id="d39a4-166">解除安裝這個範例</span><span class="sxs-lookup"><span data-stu-id="d39a4-166">Uninstalling This Sample</span></span>  
  
#### <a name="to-uninstall-the-callorchestration-sample"></a><span data-ttu-id="d39a4-167">解除安裝 CallOrchestration 範例</span><span class="sxs-lookup"><span data-stu-id="d39a4-167">To uninstall the CallOrchestration sample</span></span>  
  
1.  <span data-ttu-id="d39a4-168">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 命令視窗中，瀏覽至下列資料夾：</span><span class="sxs-lookup"><span data-stu-id="d39a4-168">In a [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] command window, navigate to the following folder:</span></span>  
  
     <span data-ttu-id="d39a4-169">\<*範例路徑*\>\Orchestrations\CallOrchestration\\</span><span class="sxs-lookup"><span data-stu-id="d39a4-169">\<*Samples Path*\>\Orchestrations\CallOrchestration\\</span></span>  
  
2.  <span data-ttu-id="d39a4-170">執行 Cleanup.bat。</span><span class="sxs-lookup"><span data-stu-id="d39a4-170">Run Cleanup.bat.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d39a4-171">請參閱</span><span class="sxs-lookup"><span data-stu-id="d39a4-171">See Also</span></span>  
 [<span data-ttu-id="d39a4-172">協調流程 (BizTalk Server Samples 資料夾)</span><span class="sxs-lookup"><span data-stu-id="d39a4-172">Orchestrations (BizTalk Server Samples Folder)</span></span>](../core/orchestrations-biztalk-server-samples-folder.md)