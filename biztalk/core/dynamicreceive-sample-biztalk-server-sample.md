---
title: DynamicReceive 範例 （BizTalk Server 範例） |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0fa7c934-7ec3-45ad-b226-c8c53934ecb1
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af89bac79614268f4648f688d8cabfc913ed2277
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974127"
---
# <a name="dynamicreceive-sample-biztalk-server-sample"></a><span data-ttu-id="e0cdf-102">DynamicReceive 範例 (BizTalk Server 範例)</span><span class="sxs-lookup"><span data-stu-id="e0cdf-102">DynamicReceive Sample (BizTalk Server Sample)</span></span>
<span data-ttu-id="e0cdf-103">DynamicReceive 範例示範在動態指定 MQSeries 佇列的 URI 時，如何從 MQSeries 佇列接收 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 訊息。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-103">The DynamicReceive sample demonstrates how to receive [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] messages from an MQSeries queue when the URI for the MQSeries queue is specified dynamically.</span></span>  
  
## <a name="what-this-sample-does"></a><span data-ttu-id="e0cdf-104">此範例的用途</span><span class="sxs-lookup"><span data-stu-id="e0cdf-104">What This Sample Does</span></span>  
 <span data-ttu-id="e0cdf-105">此範例會動態建立 MQSeries 佇列所指定**queueManager**，**佇列**，並**server**變數。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-105">This sample dynamically creates an MQSeries queue as specified by the **queueManager**, **queue**, and **server** variables.</span></span> <span data-ttu-id="e0cdf-106">它會啟用動態接收案例，並取得[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]中指定的篩選準則為基礎的動態指定 MQSeries 佇列的訊息**MQMD_MsgId**並**MQMD_CorrelId**訊息屬性。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-106">It enables a dynamic receive scenario and obtains [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] messages from the dynamically specified MQSeries queue based on the filter criteria specified in the **MQMD_MsgId** and **MQMD_CorrelId** message properties.</span></span>  
  
## <a name="how-this-sample-was-designed-and-why"></a><span data-ttu-id="e0cdf-107">此範例的設計方式和原因</span><span class="sxs-lookup"><span data-stu-id="e0cdf-107">How This Sample Was Designed and Why</span></span>  
 <span data-ttu-id="e0cdf-108">MQSeries 配接器可以透過在協調流程中指定佇列的 URI 位址，從 MQSeries 佇列動態接收訊息。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-108">The MQSeries adapter can dynamically receive messages from an MQSeries queue by specifying the URI address of the queue in the orchestration.</span></span> <span data-ttu-id="e0cdf-109">您可以在協調流程中使用請求-回應傳送埠來達成這項功能。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-109">This functionality is achieved by using a solicit-response send port in the orchestration.</span></span>  
  
 <span data-ttu-id="e0cdf-110">若要動態接收訊息，指定下列項目中的**運算式**協調流程中的圖形：</span><span class="sxs-lookup"><span data-stu-id="e0cdf-110">To dynamically receive messages, specify the following in an **Expression** shape in the orchestration:</span></span>  
  
1. <span data-ttu-id="e0cdf-111">啟用動態接收藉由設定下列屬性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]訊息： **MQSeries.DynamicReceive** = `'Yes'`</span><span class="sxs-lookup"><span data-stu-id="e0cdf-111">Enable dynamic receive by setting the following property on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] message: **MQSeries.DynamicReceive** = `'Yes'`</span></span>  
  
2. <span data-ttu-id="e0cdf-112">設定連接埠 URI，以指定取得訊息的來源位址。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-112">Specify the address from which to get the messages by setting the port URI.</span></span> <span data-ttu-id="e0cdf-113">您可以選擇指定下列選項：</span><span class="sxs-lookup"><span data-stu-id="e0cdf-113">Optionally you can specify the following:</span></span>  
  
   -   <span data-ttu-id="e0cdf-114">之前收到的訊息，使用指定的等待間隔**MQSeries.WaitInterval**訊息上的屬性。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-114">Specify the wait interval before getting the messages by using the **MQSeries.WaitInterval** property on the message.</span></span>  
  
   -   <span data-ttu-id="e0cdf-115">指定接收訊息的比對準則。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-115">Specify match criteria for receiving messages.</span></span> <span data-ttu-id="e0cdf-116">比對準則的選項包括**訊息識別碼**， **CorrelationID**， **GroupID**，以及**MessageSequenceNumber**。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-116">The match criteria options are **Message ID**, **CorrelationID**, **GroupID**, and **MessageSequenceNumber**.</span></span> <span data-ttu-id="e0cdf-117">請參閱 < 屬性相關至 BizTalk Server >，網址[ http://go.microsoft.com/fwlink/?LinkId=89396 ](http://go.microsoft.com/fwlink/?LinkId=89396)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-117">See "Properties Related to BizTalk Server" at [http://go.microsoft.com/fwlink/?LinkId=89396](http://go.microsoft.com/fwlink/?LinkId=89396) for more details.</span></span>  
  
   <span data-ttu-id="e0cdf-118">使用這些屬性建立訊息之後，便會使用請求-回應傳送埠將它傳送到 MQSeries 佇列。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-118">After the message is created with these properties it is sent to the MQSeries queue by using a solicit-response send port.</span></span> <span data-ttu-id="e0cdf-119">這個傳送埠會使用指定的比對選項，讓配接器從指定的 URI 接收訊息。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-119">The port specifies the adapter to receive messages from the specified URI with the indicated match options.</span></span> <span data-ttu-id="e0cdf-120">產生的結果如下：</span><span class="sxs-lookup"><span data-stu-id="e0cdf-120">The following actions result:</span></span>  
  
- <span data-ttu-id="e0cdf-121">如果符合用來取得訊息的篩選準則，便會從佇列擷取訊息，然後再將訊息傳回給協調流程。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-121">If the filter criteria to obtain a message are satisfied, then the message is retrieved from the queue and is sent back to the orchestration.</span></span>  
  
- <span data-ttu-id="e0cdf-122">如果不符合用來取得訊息的篩選準則，則會傳回虛擬回應。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-122">If the filter criteria to obtain a message are not satisfied, a dummy response is returned.</span></span> <span data-ttu-id="e0cdf-123">這表示指定的選項並未從佇列傳回任何訊息。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-123">This is an indication that the specified options did not return any messages from the queue.</span></span>  
  
  <span data-ttu-id="e0cdf-124">使用動態接收功能可以讓您擁有更多的彈性，因為您不需要有固定的接收位置。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-124">Using the dynamic receive functionality gives you additional flexibility because a fixed receive location is not required.</span></span> <span data-ttu-id="e0cdf-125">在某些情況下，您可能必須等到執行階段才會知道 URI。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-125">In some cases, you may not know the URI until run time.</span></span> <span data-ttu-id="e0cdf-126">動態接收功能可讓您動態決定訊息的取得來源。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-126">Dynamic receive functionality allows you to dynamically determine from where to obtain messages.</span></span> <span data-ttu-id="e0cdf-127">這也表示您不需要在協調流程內實作佇列合約。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-127">It also means you do not need to implement a queuing contract within an orchestration.</span></span>  <span data-ttu-id="e0cdf-128">您可以等待，以根據指定的比對準則，使用動態指定的 URI 從 MQSeries 佇列取得訊息。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-128">You can wait to obtain messages by using a dynamically specified URI from the MQSeries queue based on the specified match criteria.</span></span>  
  
## <a name="where-to-find-this-sample"></a><span data-ttu-id="e0cdf-129">可在何處找到此範例</span><span class="sxs-lookup"><span data-stu-id="e0cdf-129">Where to Find This Sample</span></span>  
 <span data-ttu-id="e0cdf-130">\<*範例路徑*\>\Samples\AdaptersUsage\MQSeriesAdapter\DynamicReceive</span><span class="sxs-lookup"><span data-stu-id="e0cdf-130">\<*Samples Path*\>\Samples\AdaptersUsage\MQSeriesAdapter\DynamicReceive</span></span>  
  
 <span data-ttu-id="e0cdf-131">下表顯示此範例中的檔案，並描述其用途。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-131">The following table shows the files in this sample and describes their purpose.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e0cdf-132">檔案</span><span class="sxs-lookup"><span data-stu-id="e0cdf-132">File</span></span>|<span data-ttu-id="e0cdf-133">描述</span><span class="sxs-lookup"><span data-stu-id="e0cdf-133">Description</span></span>|  
|<span data-ttu-id="e0cdf-134">DynamicReceive.btproj,</span><span class="sxs-lookup"><span data-stu-id="e0cdf-134">DynamicReceive.btproj,</span></span><br /><br /> <span data-ttu-id="e0cdf-135">DynamicReceive.sln</span><span class="sxs-lookup"><span data-stu-id="e0cdf-135">DynamicReceive.sln</span></span>|<span data-ttu-id="e0cdf-136">應用程式的專案和方案檔。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-136">Project and solution files for the application.</span></span>|  
|<span data-ttu-id="e0cdf-137">DynamicReceive e.odx</span><span class="sxs-lookup"><span data-stu-id="e0cdf-137">DynamicReceive e.odx</span></span>|<span data-ttu-id="e0cdf-138">應用程式的 BizTalk 協調流程檔案。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-138">The BizTalk orchestration file for the application.</span></span>|  
|<span data-ttu-id="e0cdf-139">Setup.bat</span><span class="sxs-lookup"><span data-stu-id="e0cdf-139">Setup.bat</span></span>|<span data-ttu-id="e0cdf-140">用來建立金鑰檔、編譯專案及部署專案的批次檔。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-140">Batch file to create the key file, compile the project, and deploy it.</span></span>|  
  
## <a name="how-to-use-this-sample"></a><span data-ttu-id="e0cdf-141">如何使用此範例</span><span class="sxs-lookup"><span data-stu-id="e0cdf-141">How to Use This Sample</span></span>  
 <span data-ttu-id="e0cdf-142">指定**Microsoft.XLANGs.BaseTypes.Address**對於您的解決方案。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-142">Specify the **Microsoft.XLANGs.BaseTypes.Address** that makes sense for your solution.</span></span> <span data-ttu-id="e0cdf-143">變更**MQSeries.WaitInterval**來指定當您預期收到的回應訊息。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-143">Change the **MQSeries.WaitInterval** to specify when you expect to receive the response messages.</span></span> <span data-ttu-id="e0cdf-144">更新 (或加入) 比對選項；如果您想取得所有訊息，則請移除比對選項。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-144">Update (or add) the match options, or remove them if you plan to obtain all messages.</span></span>  
  
## <a name="building-and-running-the-sample"></a><span data-ttu-id="e0cdf-145">建置和執行範例</span><span class="sxs-lookup"><span data-stu-id="e0cdf-145">Building and Running the Sample</span></span>  
  
#### <a name="to-create-the-sample"></a><span data-ttu-id="e0cdf-146">若要建立範例</span><span class="sxs-lookup"><span data-stu-id="e0cdf-146">To create the sample</span></span>  
  
1. <span data-ttu-id="e0cdf-147">在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中建立新的協調流程。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-147">Create a new orchestration project in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
2. <span data-ttu-id="e0cdf-148">啟用動態接收作業，藉由設定**MQSeries.DynamicReceive**屬性上的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]訊息給`'Yes'`。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-148">Enable the dynamic receive operation by setting the **MQSeries.DynamicReceive** property on the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] message to `'Yes'`.</span></span>  
  
3. <span data-ttu-id="e0cdf-149">指定要從其中取得訊息的設定位址**連接埠 URI**。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-149">Specify the address from which to obtain the messages by setting the **Port URI**.</span></span>  
  
4. <span data-ttu-id="e0cdf-150">可以選擇指定下列兩個選項：</span><span class="sxs-lookup"><span data-stu-id="e0cdf-150">Optionally the following two properties can be specified:</span></span>  
  
   1.  <span data-ttu-id="e0cdf-151">之前使用，以取得訊息，指定等待間隔**MQSeries.WaitInterval**訊息上的屬性。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-151">Specify a wait interval before getting the messages by using the **MQSeries.WaitInterval** property on the message.</span></span>  
  
   2.  <span data-ttu-id="e0cdf-152">指定接收訊息的比對準則。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-152">Specify match criteria for receiving messages.</span></span> <span data-ttu-id="e0cdf-153">如需詳細資訊，請參閱「比對選項」說明。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-153">See "Match options" help for more details.</span></span>  
  
5. <span data-ttu-id="e0cdf-154">在協調流程中變更下列變數，以指定取得訊息的來源：</span><span class="sxs-lookup"><span data-stu-id="e0cdf-154">Change the following variables in the orchestration to specify where to get the messages from:</span></span>  
  
   -   <span data-ttu-id="e0cdf-155">**佇列**， **queueManager**，以及**server**。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-155">**Queue**, **queueManager**, and **server**.</span></span> <span data-ttu-id="e0cdf-156">這些用來建置 URI**運算式**圖形。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-156">These are used to build the URI in the **Expression** shape.</span></span>  
  
6. <span data-ttu-id="e0cdf-157">修改**運算式**圖形，以視需要取消註解動態佇列建立和比對選項。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-157">Modify the **Expression** shape to comment out dynamic queue creation and match options as necessary.</span></span>  
  
7. <span data-ttu-id="e0cdf-158">您可以使用下列其中一種方法來建置及部署專案：</span><span class="sxs-lookup"><span data-stu-id="e0cdf-158">You can build and deploy the project in either of the following ways:</span></span>  
  
   -   <span data-ttu-id="e0cdf-159">開啟方案，以滑鼠右鍵按一下方案總管 中的專案，按一下**屬性**檢視專案屬性。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-159">Open the solution, right click the project in Solution explorer and click **Properties** to view project properties.</span></span> <span data-ttu-id="e0cdf-160">在 [簽署] 索引標籤上按一下**\<新增...\>** 中**選擇強式名稱金鑰檔**下拉式方塊。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-160">On the Signing tab click **\<New...\>** in the **Choose a strong name key file** drop down box.</span></span> <span data-ttu-id="e0cdf-161">然後提供金鑰檔名稱，並部署。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-161">Then provide a key file name and deploy.</span></span>  
  
   -   <span data-ttu-id="e0cdf-162">或者，執行用來建立金鑰檔、建置專案及部署專案的 setup.bat 檔案。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-162">Alternatively, run the setup.bat file which creates the key file, builds the project and deploys it.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="e0cdf-163">執行範例</span><span class="sxs-lookup"><span data-stu-id="e0cdf-163">To run the sample</span></span>  
  
1.  <span data-ttu-id="e0cdf-164">將協調流程繫結到 BizTalk 主控件。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-164">Bind the orchestration to the BizTalk Host.</span></span>  
  
2.  <span data-ttu-id="e0cdf-165">啟用協調流程建立的檔案接收埠。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-165">Enable the file receive port created by the orchestration.</span></span> <span data-ttu-id="e0cdf-166">變更檔案接收位置從**c:\temp\in**至適當的檔案資料夾。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-166">Change the file receive location from **c:\temp\in** to the proper file folder.</span></span>  
  
3.  <span data-ttu-id="e0cdf-167">登錄並啟動建立的兩個傳送埠。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-167">Enlist and start the two send ports that were created.</span></span> <span data-ttu-id="e0cdf-168">其中一個連接埠屬於動態的請求-回應連接埠類型，另一個則是檔案傳送埠，也是傳送訊息的佇列。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-168">One port is a dynamic solicit-response port type, while the other is a file send port and is the queue where the message will be sent.</span></span> <span data-ttu-id="e0cdf-169">請務必將它設定為正確的位置。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-169">Ensure that this is set to the correct location.</span></span>  
  
4.  <span data-ttu-id="e0cdf-170">若要啟動協調流程，請將檔案放到輸入資料夾中。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-170">To start the orchestration, drop a file in the input folder.</span></span> <span data-ttu-id="e0cdf-171">這樣會叫用 MQSeries 配接器並呼叫**MQSAgent2** COM + 元件，以取得訊息指定的伺服器上。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-171">This invokes the MQSeries adapter and calls the **MQSAgent2** COM+ component on the specified server to obtain the message.</span></span> <span data-ttu-id="e0cdf-172">接收訊息會出現在檔案傳送埠中指定的資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-172">The received message appears in the folder location specified in the file send port.</span></span>  
  
5.  <span data-ttu-id="e0cdf-173">如果沒有任何訊息找到符合指定準則**運算式**圖形，將虛擬訊息放入輸出資料夾。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-173">If no message is found that matches the criteria specified in the **Expression** shape, a dummy message is dropped into the output folder.</span></span> <span data-ttu-id="e0cdf-174">若要停用比對選項，請取消註解中的最後兩行**運算式**圖形。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-174">To disable match options, comment out the last two lines in the **Expression** shape.</span></span>  
  
## <a name="comments"></a><span data-ttu-id="e0cdf-175">註解</span><span class="sxs-lookup"><span data-stu-id="e0cdf-175">Comments</span></span>  
  
-   <span data-ttu-id="e0cdf-176">如果佇列採動態方式建立，但卻不會動態刪除，則在啟動下一個協調流程時，將會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-176">If the queue is being dynamically created, but not deleted, it will result in errors when the next orchestration instance is activated.</span></span>  
  
-   <span data-ttu-id="e0cdf-177">雖然這個範例只指定了一種選項，但是還有其他方法可以動態設定 URI。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-177">There are other ways to set the URI dynamically; this sample specifies just one option.</span></span> <span data-ttu-id="e0cdf-178">例如，URI 可以透過讀取訊息內容中的某個屬性來設定。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-178">For example, the URI could be set by reading some property in the message context.</span></span>  
  
-   <span data-ttu-id="e0cdf-179">如果佇列中沒有任何訊息符合比對選項，便會傳回虛擬訊息。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-179">If there are no messages in the queue that satisfy the match options, a dummy message is returned.</span></span>  
  
-   <span data-ttu-id="e0cdf-180">因為這個範例使用的是動態傳送埠，所以可能必須指定其他選項，例如重試和交易。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-180">Because this sample uses dynamic send ports, other options may need to be specified, such as retry and transactions.</span></span> <span data-ttu-id="e0cdf-181">將訊息傳送到動態請求-回應連接埠之前，請先使用配接器所公開的內容屬性來設定這些選項。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-181">Use the context properties exposed by the adapter to set these options before sending the message out to the dynamic solicit-response port.</span></span>  
  
-   <span data-ttu-id="e0cdf-182">MQSeries 佇列可以建立及使用刪除動態**MQSAdapterAdmin2**介面。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-182">MQSeries queues can be created and deleted dynamically by using the **MQSAdapterAdmin2** interface.</span></span> <span data-ttu-id="e0cdf-183">如何動態建立 MQSeries 佇列的範例，請參閱 < 支援的佇列的管理 >，網址[ http://go.microsoft.com/fwlink/?LinkId=89400 ](http://go.microsoft.com/fwlink/?LinkId=89400)。</span><span class="sxs-lookup"><span data-stu-id="e0cdf-183">For an example of how to dynamically create MQSeries queues, see "Support for Queue Management" at [http://go.microsoft.com/fwlink/?LinkId=89400](http://go.microsoft.com/fwlink/?LinkId=89400).</span></span>