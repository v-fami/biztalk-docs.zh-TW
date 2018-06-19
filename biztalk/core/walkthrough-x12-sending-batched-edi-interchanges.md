---
title: 逐步解說 (X12)： 傳送批次 EDI 交換 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b80ea79b-6112-49bd-90e8-9a0a0e604df8
caps.latest.revision: 54
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d5ce491b5cf9ff3d1c142599edee4e6c5f6a324
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22292030"
---
# <a name="walkthrough-x12-sending-batched-edi-interchanges"></a><span data-ttu-id="dd4d2-102">逐步解說 (X12)：傳送批次 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="dd4d2-102">Walkthrough (X12): Sending Batched EDI Interchanges</span></span>
<span data-ttu-id="dd4d2-103">本逐步解說提供一組逐步程序，說明如何使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 建立可在合作對象之間傳送批次 EDI 交換的解決方案。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-103">This walkthrough provides a set of step-by-step procedures that creates a solution for sending batched EDI interchanges from one party to another using [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="dd4d2-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="dd4d2-104">Prerequisites</span></span>  
 <span data-ttu-id="dd4d2-105">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-105">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
## <a name="how-the-solution-sends-batched-edi-interchanges"></a><span data-ttu-id="dd4d2-106">解決方案傳送批次 EDI 交換的方式</span><span class="sxs-lookup"><span data-stu-id="dd4d2-106">How the Solution Sends Batched EDI Interchanges</span></span>  
 <span data-ttu-id="dd4d2-107">解決方案會執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="dd4d2-107">The solution will do the following:</span></span>  
  
1.  <span data-ttu-id="dd4d2-108">接收位置接收來自 EDI 交換**合作對象 A**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-108">The receive location receives an EDI interchange from a **Party A**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd4d2-109">這份清單中的事件可能不會按照所示的順序發生。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-109">The events in this list may not occur in the order shown.</span></span>  
  
2.  <span data-ttu-id="dd4d2-110">接收管線將交換的 EDI 格式轉換為內部 XML 格式，</span><span class="sxs-lookup"><span data-stu-id="dd4d2-110">The receive pipeline converts the EDI format of the interchange to internal XML format.</span></span> <span data-ttu-id="dd4d2-111">並判斷要批次處理該交換。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-111">The receive pipeline determines that the interchange is to be batched.</span></span> <span data-ttu-id="dd4d2-112">因此，BatchMarkerReceivePipeline 元件會升級 `EDI.ToBeBatched==True` 和 `EDI.BatchId` 屬性。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-112">As a result, the BatchMarkerReceivePipeline component promotes the `EDI.ToBeBatched==True` and `EDI.BatchId` properties.</span></span> <span data-ttu-id="dd4d2-113">接著將該交換放入 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-113">It then drops the interchange into the MessageBox.</span></span>  
  
3.  <span data-ttu-id="dd4d2-114">「批次協調流程」根據 `EDI.ToBeBatched==True` 和 `EDI.BatchId==%BatchID%` 訂閱了這個訊息，因而從 MessageBox 擷取收到的交換。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-114">The Batching Orchestration retrieves the received interchange from the MessageBox, because it subscribes to the message based upon `EDI.ToBeBatched==True` and `EDI.BatchId==%BatchID%`.</span></span>  
  
4.  <span data-ttu-id="dd4d2-115">接收位置收到當初傳來第一個交換的同一個合作對象所傳來的第二個 EDI 交換。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-115">The receive location receives a second EDI interchange from the same party that sent the first interchange.</span></span>  
  
5.  <span data-ttu-id="dd4d2-116">接收位置依照步驟 2 中的方式處理交換，然後將交換放置在 MessageBox 中。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-116">The receive location processes the interchange as in step 2, and then drops the interchange into the MessageBox.</span></span>  
  
6.  <span data-ttu-id="dd4d2-117">「批次處理協調流程」依照步驟 3 中的方式擷取交換。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-117">The Batching Orchestration retrieves the interchange as in step 3.</span></span>  
  
7.  <span data-ttu-id="dd4d2-118">在達到釋放準則後 (釋放準則定義了交換的比對方式)，「批次協調流程」將所有交換組合成一個交換，然後升級 `EDI.ToBeBatched==False`、`EDI.BatchName` 和 `EDI.DestinationPartyName` 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-118">After the release criteria is met (release criteria defines how the interchanges have to be matched), the Batching Orchestration assembles the interchange containing all the interchanges, and then promotes the `EDI.ToBeBatched==False`, `EDI.BatchName` and `EDI.DestinationPartyName` context properties.</span></span> <span data-ttu-id="dd4d2-119">它會卸除批次的交換放入 MessageBox。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-119">It drops the batched interchange into the MessageBox.</span></span>  
  
8.  <span data-ttu-id="dd4d2-120">傳送埠透過訂閱 `EDI.ToBeBatched`==False、`EDI.BatchName` 和 `EDI.DestinationPartyName` 這些內容屬性，來收取批次交換。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-120">The send port picks up the batched interchange by subscribing on the context properties `EDI.ToBeBatched`==False, `EDI.BatchName` and `EDI.DestinationPartyName`.</span></span>  
  
9. <span data-ttu-id="dd4d2-121">傳送管線將其他屬性套用至批次交換的信封，然後將交換傳送至目的合作對象，**合作對象 B**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-121">The send pipeline applies additional properties to the envelope of the batched interchange, and then sends the interchange to destination party, **Party B**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd4d2-122">如需詳細資訊，請參閱[組合批次 EDI 交換](../core/assembling-a-batched-edi-interchange.md)。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-122">For more information, see [Assembling a Batched EDI Interchange](../core/assembling-a-batched-edi-interchange.md).</span></span>  
  
 <span data-ttu-id="dd4d2-123">下圖顯示這個解決方案的架構。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-123">The following figure shows the architecture for this solution.</span></span>  
  
 <span data-ttu-id="dd4d2-124">![傳送批次 EDI 交換](../core/media/93a09e3c-476d-4bd2-a0e3-b5b219858791.gif "93a09e3c-476d-4bd2-a0e3-b5b219858791")</span><span class="sxs-lookup"><span data-stu-id="dd4d2-124">![Sending batched EDI interchanges](../core/media/93a09e3c-476d-4bd2-a0e3-b5b219858791.gif "93a09e3c-476d-4bd2-a0e3-b5b219858791")</span></span>  
  
## <a name="the-functionality-in-this-solution"></a><span data-ttu-id="dd4d2-125">此解決方案中的功能</span><span class="sxs-lookup"><span data-stu-id="dd4d2-125">The Functionality in this Solution</span></span>  
 <span data-ttu-id="dd4d2-126">為了完成這個逐步解說，將會啟用下列功能：</span><span class="sxs-lookup"><span data-stu-id="dd4d2-126">For the purposes of this walkthrough, the following functionality will be enabled:</span></span>  
  
-   <span data-ttu-id="dd4d2-127">這個解決方案是專為使用 X12 編碼 (而非 EDIFACT 編碼) 的交換所設計。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-127">The solution is designed for interchanges using X12 encoding, not EDIFACT encoding.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd4d2-128">用於 HIPAA 與 EDIFACT 編碼的組態，與用於 X12 編碼的組態近乎相同。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-128">The configuration used for HIPAA and for EDIFACT encoding is closely parallel to that used for X12 encoding.</span></span>  
  
-   <span data-ttu-id="dd4d2-129">將不會傳回技術或功能通知，以回應原本收到的交換或任何傳送的批次交換。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-129">Technical or functional acknowledgments will not be returned in response to the interchange originally received or any batched interchange that is sent.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd4d2-130">如需產生 EDI 通知的資訊，請參閱[(X12) 逐步解說： 接收 EDI 交換並傳送傳回通知](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md)。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-130">For information about generating EDI acknowledgments, see [Walkthrough (X12): Receiving EDI Interchanges and Sending Back an Acknowledgement](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md).</span></span>  
  
-   <span data-ttu-id="dd4d2-131">這個解決方案會使用單向接收埠和靜態單向傳送埠，</span><span class="sxs-lookup"><span data-stu-id="dd4d2-131">This solution uses a one-way receive port and a static one-way send port.</span></span> <span data-ttu-id="dd4d2-132">因此會將這些連接埠設定為 FILE 傳輸類型。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-132">These ports will be configured with the FILE transport type.</span></span>  
  
-   <span data-ttu-id="dd4d2-133">將會啟用 EDI 報告。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-133">EDI reporting will be enabled.</span></span>  
  
-   <span data-ttu-id="dd4d2-134">將會儲存交易集，以從交換狀態報告中檢視交易集。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-134">Transaction sets will be saved for viewing from the interchange status report.</span></span>  
  
## <a name="configuring-and-testing-the-walkthrough"></a><span data-ttu-id="dd4d2-135">設定和測試逐步解說</span><span class="sxs-lookup"><span data-stu-id="dd4d2-135">Configuring and Testing the Walkthrough</span></span>  
 <span data-ttu-id="dd4d2-136">這個解決方案所需的程序包含下列步驟：</span><span class="sxs-lookup"><span data-stu-id="dd4d2-136">The procedures required for this solution include the following:</span></span>  
  
-   <span data-ttu-id="dd4d2-137">將必要的訊息結構描述加入 BizTalk 專案，然後建置並部署此專案，因此 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可以使用此結構描述處理訊息。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-137">Add the required message schema(s) to a BizTalk project, and then build and deploy the project, making the schema(s) available for use by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in processing the messages.</span></span>  
  
-   <span data-ttu-id="dd4d2-138">更新中的 SQL 配接器的輪詢間隔**BatchControlMessageReccvLoc**接收位置，如此當您按一下 立即啟動批次處理協調流程**啟動**按鈕傳送控制訊息會啟動批次處理協調流程執行個體。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-138">Update the polling interval for the SQL adapter in the **BatchControlMessageReccvLoc** receive location, so that the batching orchestration will be promptly activated when you click the **Start** button to send the control message that will activate a batching orchestration instance.</span></span>  
  
-   <span data-ttu-id="dd4d2-139">建立接收埠，讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收來自合作對象的 EDI X12 編碼 .txt 輸入訊息。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-139">Create a receive port for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to receive the EDI X12-encoded .txt input messages from a party.</span></span>  
  
-   <span data-ttu-id="dd4d2-140">為合作對象 A 與合作對象 B 建立合作對象 (交易夥伴)。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-140">Create a party (trading partner) for both Party A and Party B.</span></span>  
  
-   <span data-ttu-id="dd4d2-141">分別為兩個交易夥伴建立商務設定檔。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-141">Create a business profile each for both the trading partners.</span></span>  
  
-   <span data-ttu-id="dd4d2-142">設定讓訊息收得到的 EDI 屬性，以建立這兩個設定檔之間的協議。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-142">Create an agreement between the two profiles by configuring the EDI properties for the message to be received.</span></span> <span data-ttu-id="dd4d2-143">設定讓批次訊息傳送得出去的 EDI 屬性。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-143">Configure the EDI properties for the batched message to be sent.</span></span> <span data-ttu-id="dd4d2-144">就這個解決方案而言，請設定協議，讓 BizTalk Server 每收到兩個 850 交換，就傳送批次交換給 Party B。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-144">For this solution, configure the agreements such that BizTalk Server will send a batch to Party B whenever two 850 interchanges are received.</span></span>  
  
-   <span data-ttu-id="dd4d2-145">建立傳送埠，讓 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 傳送批次 EDI 交換給交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-145">Create a send port for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to send the batched EDI interchange to the trading partner.</span></span> <span data-ttu-id="dd4d2-146">此傳送埠將是靜態單向傳送埠。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-146">This send port will be a static one-way send port.</span></span>  
  
-   <span data-ttu-id="dd4d2-147">使傳送埠與會負責批次處理交換的協議產生關聯。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-147">Associate the send port with the agreement that processes the interchanges and batches them.</span></span>  
  
-   <span data-ttu-id="dd4d2-148">將兩個測試 EDI 交換放置在與接收位置相關聯的本機資料夾中，並確認 BizTalk Server 已將批次交換放置在與傳送埠相關聯的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-148">Drop two test EDI interchanges into the local folder associated with the receive location, and verifying that BizTalk Server has dropped a batched interchange into the folder associated with the send port.</span></span>  
  
### <a name="configuring-the-walkthrough"></a><span data-ttu-id="dd4d2-149">設定逐步解說</span><span class="sxs-lookup"><span data-stu-id="dd4d2-149">Configuring the Walkthrough</span></span>  
 <span data-ttu-id="dd4d2-150">本節說明設定逐步解說的程序。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-150">This section describes the procedures to configure the walkthrough.</span></span>  
  
##### <a name="to-deploy-the-message-schema"></a><span data-ttu-id="dd4d2-151">若要部署訊息結構描述</span><span class="sxs-lookup"><span data-stu-id="dd4d2-151">To deploy the message schema</span></span>  
  
1.  <span data-ttu-id="dd4d2-152">在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 中，建立或開啟 BizTalk 專案。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-152">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], create or open a BizTalk project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd4d2-153">本主題假設您已經在「BizTalk EDI 應用程式」中加入了自己應用程式的參考 (包含 EDI 結構描述、管線和協調流程)，</span><span class="sxs-lookup"><span data-stu-id="dd4d2-153">This topic assumes that you have already added a reference from your application to the BizTalk EDI Application, which contains EDI schemas, pipelines, and orchestrations.</span></span> <span data-ttu-id="dd4d2-154">如果沒有，請參閱[如何將參考加入至 BizTalk Server EDI 應用程式](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782)。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-154">If not, see [How to Add a Reference to the BizTalk Server EDI Application](http://msdn.microsoft.com/library/7af066fb-372f-4709-b566-c8d6b4a9d782).</span></span>  
  
2.  <span data-ttu-id="dd4d2-155">以滑鼠右鍵按一下您的專案，指向**新增**，然後按一下 **現有項目**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-155">Right-click your project, point to **Add**, and then click **Existing Item**.</span></span> <span data-ttu-id="dd4d2-156">移至 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\X12\00401，然後按兩下與測試訊息對應的結構描述。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-156">Move to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI\X12\00401, and then double-click the schema corresponding to your test message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd4d2-157">如果 EDI 結構描述尚未解壓縮至 \XSD_Schema\EDI 資料夾，執行**MicrosoftEdiXSDTemplates.exe** \XSD_Schema\EDI 資料夾，將結構描述解壓縮至預設資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-157">If the EDI schemas have not been unzipped into the \XSD_Schema\EDI folders, execute the **MicrosoftEdiXSDTemplates.exe** file in the \XSD_Schema\EDI folder to unzip the schemas into the default folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd4d2-158">對於測試訊息，您可以使用「EDI 介面開發人員」教學課程中所使用的 850 範例訊息。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-158">For a test message, you can use the 850 sample message used for the EDI Interface Developer tutorial.</span></span> <span data-ttu-id="dd4d2-159">這是檔案中的 SamplePO.txt [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\\。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-159">This file is SamplePO.txt in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\\.</span></span> <span data-ttu-id="dd4d2-160">如果這樣做，您就必須使用位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI 中的結構描述 x12_00401_850.xsd。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-160">If you do so, you must use the schema x12_00401_850.xsd located in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI.</span></span>  
  
3.  <span data-ttu-id="dd4d2-161">設定組件金鑰檔案，然後建置並部署組件。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-161">Set the assembly key file, and then build and deploy the assembly.</span></span>  
  
##### <a name="to-update-the-polling-interval"></a><span data-ttu-id="dd4d2-162">若要更新輪詢間隔</span><span class="sxs-lookup"><span data-stu-id="dd4d2-162">To update the polling interval</span></span>  
  
1.  <span data-ttu-id="dd4d2-163">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，開啟**BizTalk 群組**，**應用程式**， **BizTalk EDI 應用程式**節點，和**接收位置**節點。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-163">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, open the **BizTalk Group**, **Applications**, **BizTalk EDI Application** nodes, and **Receive Locations** nodes.</span></span> <span data-ttu-id="dd4d2-164">在下**接收位置**] 節點，以滑鼠右鍵按一下**BatchControlMessageRecvLoc**，然後按一下 [**屬性**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-164">Under the **Receive Locations** node, right-click **BatchControlMessageRecvLoc**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="dd4d2-165">針對 SQL 傳輸類型，按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-165">For the SQL transport type, click **Configure**.</span></span>  
  
3.  <span data-ttu-id="dd4d2-166">在**SQL 傳輸屬性**對話方塊方塊中，將輪詢間隔設定為較小的值。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-166">In the **SQL Transport Properties** dialog box, set the polling interval to a smaller value.</span></span> <span data-ttu-id="dd4d2-167">例如，您可以變更**輪詢的度量單位**至**秒**，而不是變更輪詢間隔為 5 秒，以分鐘為單位。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-167">For example, you can change **Polling Unit of Measure** to **Seconds**, instead of minutes, to change the polling interval to 5 seconds.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd4d2-168">變更輪詢間隔可確保立即啟動批次處理協調流程。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-168">Changing the polling interval ensures that the batching orchestration will be promptly activated.</span></span>  
  
4.  <span data-ttu-id="dd4d2-169">按一下**確定**，然後按一下 **確定**一次。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-169">Click **OK**, and then click **OK** again.</span></span>  
  
##### <a name="to-create-a-one-way-receive-port-to-receive-the-edi-messages-to-be-batched"></a><span data-ttu-id="dd4d2-170">若要建立單向接收埠以接收要批次處理的 EDI 訊息</span><span class="sxs-lookup"><span data-stu-id="dd4d2-170">To create a one-way receive port to receive the EDI messages to be batched</span></span>  
  
1.  <span data-ttu-id="dd4d2-171">建立本機資料夾以接收要批次處理的 EDI 訊息。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-171">Create a local folder to receive the EDI messages to be batched.</span></span>  
  
2.  <span data-ttu-id="dd4d2-172">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**接收埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **單向接收埠。**</span><span class="sxs-lookup"><span data-stu-id="dd4d2-172">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Receive Ports** node under the **BizTalk Application 1** node, point to **New**, and then click **One-way Receive Port.**</span></span>  
  
3.  <span data-ttu-id="dd4d2-173">將接收連接埠，再按一下**接收位置**在主控台樹狀目錄中。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-173">Name the receive port, and then click **Receive Locations** in the console tree.</span></span>  
  
4.  <span data-ttu-id="dd4d2-174">按一下 **[新增]**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-174">Click **New**.</span></span>  
  
5.  <span data-ttu-id="dd4d2-175">接收位置命名，選取**檔案**如**類型**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-175">Name the receive location, select **FILE** for **Type**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="dd4d2-176">輸入的資料夾**接收資料夾**，和遮罩**檔案遮罩**，例如 **\*.txt**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-176">Enter a folder for **Receive folder**, and a mask for **File Mask**, such as **\*.txt**.</span></span>  
  
7.  <span data-ttu-id="dd4d2-177">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-177">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="dd4d2-178">如**接收管線**，選取**EdiReceive**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-178">For **Receive pipeline**, select **EdiReceive**.</span></span>  
  
9. <span data-ttu-id="dd4d2-179">按一下**確定**，然後按一下 **確定**一次。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-179">Click **OK**, and then click **OK** again.</span></span>  
  
10. <span data-ttu-id="dd4d2-180">在主控台樹狀目錄中，按一下**接收位置**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-180">In the console tree, click **Receive Locations**.</span></span> <span data-ttu-id="dd4d2-181">在**接收位置** 窗格中，以滑鼠右鍵按一下您接收位置，然後按一下**啟用**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-181">In the **Receive Locations** pane, right-click your receive location, and then click **Enable**.</span></span>  
  
##### <a name="to-create-a-party-and-a-business-profile-for-party-a"></a><span data-ttu-id="dd4d2-182">為合作對象 A 建立合作對象與商務設定檔</span><span class="sxs-lookup"><span data-stu-id="dd4d2-182">To create a party and a business profile for Party A</span></span>  
  
1.  <span data-ttu-id="dd4d2-183">以滑鼠右鍵按一下**合作對象**節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下 **合作對象**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-183">Right-click the **Parties** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, point to **New**, and then click **Party**.</span></span>  
  
2.  <span data-ttu-id="dd4d2-184">輸入的名稱中的合作對象**名稱**文字方塊，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-184">Enter a name for the party in the **Name** text box, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd4d2-185">藉由選取**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定正在建立的合作對象為相同的組織同時裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dd4d2-185">By selecting the **Local BizTalk processes messages received by the Party OR supports sending messages from this party** check box, you can specify that the party being created is for the same organization that is also hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="dd4d2-186">據此，建立協議時將會啟用或停用某些屬性。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-186">Based on that, some properties will be enabled or disabled when you create an agreement.</span></span> <span data-ttu-id="dd4d2-187">不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-187">However, for this walkthrough, you can leave this check box selected.</span></span>  
  
3.  <span data-ttu-id="dd4d2-188">以滑鼠右鍵按一下合作對象名稱，指向**新增**，然後按一下 **商務設定檔**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-188">Right-click the party name, point to **New**, and then click **Business Profile**.</span></span>  
  
4.  <span data-ttu-id="dd4d2-189">在**設定檔屬性**對話方塊**一般**頁面上，輸入**PartyA_Profile**中**名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-189">In the **Profile Properties** dialog box, on the **General** page, enter **PartyA_Profile** in the **Name** text box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd4d2-190">當您建立合作對象時，會同時建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-190">When you create a party, a profile is also created.</span></span> <span data-ttu-id="dd4d2-191">您可以重新命名再使用該設定檔，而不需建立新設定檔。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-191">You can rename and use that profile instead of creating a new one.</span></span> <span data-ttu-id="dd4d2-192">若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-192">To rename a profile, right-click the profile and select **Properties**.</span></span> <span data-ttu-id="dd4d2-193">在**一般**頁面上，指定設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-193">In the **General** page, specify a name for the profile.</span></span>  
  
##### <a name="to-create-a-party-and-a-business-profile-for-party-b"></a><span data-ttu-id="dd4d2-194">若要為 Party B 建立合作對象與商務設定檔</span><span class="sxs-lookup"><span data-stu-id="dd4d2-194">To create a party and a business profile for Party B</span></span>  
  
1.  <span data-ttu-id="dd4d2-195">以滑鼠右鍵按一下**合作對象**節點[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，指向**新增**，然後按一下 **合作對象**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-195">Right-click the **Parties** node in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, point to **New**, and then click **Party**.</span></span>  
  
2.  <span data-ttu-id="dd4d2-196">輸入的名稱中的合作對象**名稱**文字方塊，然後再按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-196">Enter a name for the party in the **Name** text box, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd4d2-197">藉由選取**本機 BizTalk 會處理合作對象或支援此合作對象傳送訊息所收到的訊息**核取方塊，您可以指定正在建立的合作對象為相同的組織同時裝載[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dd4d2-197">By selecting the **Local BizTalk processes messages received by the Party OR supports sending messages from this party** check box, you can specify that the party being created is for the same organization that is also hosting [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="dd4d2-198">據此，建立協議時將會啟用或停用某些屬性。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-198">Based on that, some properties will be enabled or disabled when you create an agreement.</span></span> <span data-ttu-id="dd4d2-199">不過，就本逐步解說而言，您可以讓這個核取方塊保持選取狀態。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-199">However, for this walkthrough, you can leave this check box selected.</span></span>  
  
3.  <span data-ttu-id="dd4d2-200">以滑鼠右鍵按一下合作對象名稱，指向**新增**，然後按一下 **商務設定檔**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-200">Right-click the party name, point to **New**, and then click **Business Profile**.</span></span>  
  
4.  <span data-ttu-id="dd4d2-201">在**設定檔屬性**對話方塊**一般**頁面上，輸入**PartyB_Profile**中**名稱**文字方塊。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-201">In the **Profile Properties** dialog box, on the **General** page, enter **PartyB_Profile** in the **Name** text box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd4d2-202">當您建立合作對象時，會同時建立設定檔。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-202">When you create a party, a profile is also created.</span></span> <span data-ttu-id="dd4d2-203">您可以重新命名再使用該設定檔，而不需建立新設定檔。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-203">You can rename and use that profile instead of creating a new one.</span></span> <span data-ttu-id="dd4d2-204">若要重新命名設定檔，以滑鼠右鍵按一下 設定檔，然後選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-204">To rename a profile, right-click the profile and select **Properties**.</span></span> <span data-ttu-id="dd4d2-205">在**一般**頁面上，指定設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-205">In the **General** page, specify a name for the profile.</span></span>  
  
##### <a name="to-create-an-agreement-between-the-two-business-profiles"></a><span data-ttu-id="dd4d2-206">在兩個商務設定檔之間建立協議</span><span class="sxs-lookup"><span data-stu-id="dd4d2-206">To create an agreement between the two business profiles</span></span>  
  
1.  <span data-ttu-id="dd4d2-207">以滑鼠右鍵按一下**PartyA_Profile**，指向 **新增**，然後按一下 **協議**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-207">Right-click **PartyA_Profile**, point to **New**, and then click **Agreement**.</span></span>  
  
2.  <span data-ttu-id="dd4d2-208">在**一般屬性** 頁面上，針對**名稱**文字方塊中，輸入協議的名稱。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-208">In the **General Properties** page, for the **Name** text box, enter a name for the agreement.</span></span>  
  
3.  <span data-ttu-id="dd4d2-209">從**通訊協定**下拉式清單中，選取**X12**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-209">From the **Protocol** drop-down list, select **X12**.</span></span>  
  
4.  <span data-ttu-id="dd4d2-210">在**第二個夥伴** 區段中，從**名稱**下拉式清單中，選取**Party**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-210">In the **Second Partner** section, from the **Name** drop-down list, select **PartyB**.</span></span>  
  
5.  <span data-ttu-id="dd4d2-211">在**第二個夥伴** 區段中，從**設定檔**下拉式清單中，選取**PartyB_Profile**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-211">In the **Second Partner** section, from the **Profile** drop-down list, select **PartyB_Profile**.</span></span>  
  
     <span data-ttu-id="dd4d2-212">您會發現兩個新的索引標籤取得旁新增**一般** 索引標籤。每個索引標籤各用於設定一個單向協議，而每個單向協議各代表一筆完整的訊息交易 (包含訊息傳輸與通知傳輸)。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-212">You will notice that two new tabs get added next to the **General** tab. Each tab is for configuring a one-way agreement and each one-way agreement represents one complete transaction of message (including message transfer and acknowledgement transfer).</span></span>  
  
6.  <span data-ttu-id="dd4d2-213">在**一般**索引標籤**一般屬性**頁面上，於**一般主控件設定**區段中，選取**開啟報告**，然後選取**儲存報告的訊息內容**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-213">In the **General** tab, on the **General Properties** page, in the **Common Host Settings** section, select **Turn ON reporting**, and then select **Store message payload for reporting**.</span></span>  
  
7.  <span data-ttu-id="dd4d2-214">在上執行下列工作**party a-> partyb**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-214">Perform the following tasks on the **PartyA->PartyB** tab.</span></span>  
  
    1.  <span data-ttu-id="dd4d2-215">在**識別碼**頁面**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，和**ISA8**) 對應到您的測試訊息中標頭欄位的值。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-215">On the **Identifiers** page under the **Interchange Settings** section, enter values for the qualifier and identifier fields (**ISA5**, **ISA6**, **ISA7**, and **ISA8**) that correspond to the values for those header fields in your test message.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="dd4d2-216">對於傳送者和接收者，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 需要辨識符號與識別碼欄位，才能執行協議解析。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-216">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] requires the qualifier and identifier fields for sender and receiver in order to perform agreement resolution.</span></span> <span data-ttu-id="dd4d2-217">它會比對的值**ISA5**， **ISA6**， **ISA7**，和**ISA8**交換標頭與協議屬性中。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-217">It will match the values of **ISA5**, **ISA6**, **ISA7**, and **ISA8** in the interchange header with those in the properties of an agreement.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="dd4d2-218">也比對傳送者辨識符號和識別項 （不需接收者辨識符號和識別項） 來解析協議。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-218"> will also resolve the agreement by matching the sender qualifier and identifier (without the receiver qualifier and identifier).</span></span> <span data-ttu-id="dd4d2-219">若 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法解析協議，它將會使用後援協議屬性。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-219">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] cannot resolve the agreement, it will use the fallback agreement properties.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="dd4d2-220">如果您使用 「 EDI 介面開發人員教學課程 」 中的 SamplePO.txt 檔案做為測試訊息，設定**ISA5**至**ZZ**， **ISA6**至**THEM**， **ISA7**至**ZZ**，和**ISA8**至**美國**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-220">If you are using the SamplePO.txt file from the “EDI Interface Developer Tutorial” as your test message, set **ISA5** to **ZZ**, **ISA6** to **THEM**, **ISA7** to **ZZ**, and **ISA8** to **US**.</span></span>  
  
    2.  <span data-ttu-id="dd4d2-221">在**驗證**頁面**交換設定**區段中，請確定**檢查重複的 ISA13**未選項。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-221">On the **Validation** page under the **Interchange Settings** section, make sure **Check for duplicate ISA13** option is unchecked.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="dd4d2-222">清除**檢查重複的 ISA13**屬性可讓您接收相同訊息的多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-222">Clearing the **Check for duplicate ISA13** property enables you to receive multiple instances of the same message.</span></span>  
  
    3.  <span data-ttu-id="dd4d2-223">在**字元集和分隔符號**頁面**交換設定**區段中，選取**CR LF**選項。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-223">On the **Charset and Separators** page under the **Interchange Settings** section, select the **CR LF** option.</span></span>  
  
    4.  <span data-ttu-id="dd4d2-224">在**批次組態**頁面**交換設定**區段中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="dd4d2-224">On the **Batch Configuration** page under the **Interchange Settings** section, do the following:</span></span>  
  
        1.  <span data-ttu-id="dd4d2-225">按一下**新批次**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-225">Click **New Batch**.</span></span>  
  
        2.  <span data-ttu-id="dd4d2-226">在下**識別** 區段中，針對**批次名稱**文字、 輸入`Batch1`。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-226">Under the **Identification** section, for **Batch Name** text, enter `Batch1`.</span></span>  
  
        3.  <span data-ttu-id="dd4d2-227">在下**篩選**區段中，按一下**篩選** 按鈕，然後在**批次篩選條件**對話方塊方塊中，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="dd4d2-227">Under the **Filter** section, click the **Filter** button, and in the **Batch Filter** dialog box, do the following:</span></span>  
  
            1.  <span data-ttu-id="dd4d2-228">按一下下方的空白儲存格**屬性**資料行，然後選取**BTS。ReceivePortName**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-228">Click the empty cell under the **Property** column and select **BTS.ReceivePortName**.</span></span>  
  
            2.  <span data-ttu-id="dd4d2-229">按一下下方的空白儲存格**運算子**資料行，然後選取 **==** 。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-229">Click the empty cell under the **Operator** column and select **==**.</span></span>  
  
            3.  <span data-ttu-id="dd4d2-230">按一下下方的空白儲存格**值**資料行，然後輸入您稍早建立的接收埠名稱。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-230">Click the empty cell under the **Value** column and enter the name of the receive port you created earlier.</span></span>  
  
            4.  <span data-ttu-id="dd4d2-231">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-231">Click **OK**.</span></span>  
  
        4.  <span data-ttu-id="dd4d2-232">在下**發行**區段中，選取**最大數目的交易集**選項，從下拉式清單中選取**交換**，並在文字方塊中輸入的數目將批次處理的交換。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-232">Under the **Release** section, select the **Maximum number of transaction sets in** option, from the drop-down select **Interchange**, and in the text box enter the number of interchanges that will be batched.</span></span> <span data-ttu-id="dd4d2-233">在此解決方案中，您將會批次處理兩個交換，因此請在文字方塊中，輸入`2`。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-233">In this solution, you will be batching two interchanges, so in the text box, enter `2`.</span></span>  
  
        5.  <span data-ttu-id="dd4d2-234">在下**啟用**區段中，選取**立即開始**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-234">Under the **Activation** section, select **Start immediately**.</span></span>  
  
    5.  <span data-ttu-id="dd4d2-235">在**信封**頁面**交易集設定**區段中，輸入在格線的第一行中的所有資料行的值。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-235">On the **Envelopes** page under the **Transaction Set Settings** section, enter values for all columns in the first line of the grid.</span></span>  
  
        |<span data-ttu-id="dd4d2-236">使用</span><span class="sxs-lookup"><span data-stu-id="dd4d2-236">Use this</span></span>|<span data-ttu-id="dd4d2-237">動作</span><span class="sxs-lookup"><span data-stu-id="dd4d2-237">To do this</span></span>|  
        |--------------|----------------|  
        |<span data-ttu-id="dd4d2-238">**預設值**</span><span class="sxs-lookup"><span data-stu-id="dd4d2-238">**Default**</span></span>|<span data-ttu-id="dd4d2-239">選取**預設**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-239">Select **Default**.</span></span> <span data-ttu-id="dd4d2-240">**注意：** 當您選取這個資料列的預設值為**GS1**， **GS2**， **GS3**， **GS7**，和**GS8**可用即使值**交易類型**，**版本/版次**，和**目標命名空間**都不符合訊息。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-240">**Note:**  When you select this row as the default, the values for **GS1**, **GS2**, **GS3**, **GS7**, and **GS8** are used even if the values for **Transaction Type**, **Version/Release**, and **Target namespace** are not a match for the message.</span></span>|  
        |<span data-ttu-id="dd4d2-241">**交易類型**</span><span class="sxs-lookup"><span data-stu-id="dd4d2-241">**Transaction Type**</span></span>|<span data-ttu-id="dd4d2-242">選取的測試訊息，訊息類型**850-Purchase Order**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-242">Select the message type of your test message, **850 - Purchase Order**.</span></span>|  
        |<span data-ttu-id="dd4d2-243">**版本/版次**</span><span class="sxs-lookup"><span data-stu-id="dd4d2-243">**Version/Release**</span></span>|<span data-ttu-id="dd4d2-244">輸入 EDI 版本， **00401**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-244">Enter the EDI version, **00401**.</span></span>|  
        |<span data-ttu-id="dd4d2-245">**目標命名空間**</span><span class="sxs-lookup"><span data-stu-id="dd4d2-245">**Target namespace**</span></span>|<span data-ttu-id="dd4d2-246">選取**http://schemas.microsoft.com/BizTalk/Edi/X12/2006**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-246">Select **http://schemas.microsoft.com/BizTalk/Edi/X12/2006**.</span></span>|  
        |<span data-ttu-id="dd4d2-247">**GS1**</span><span class="sxs-lookup"><span data-stu-id="dd4d2-247">**GS1**</span></span>|<span data-ttu-id="dd4d2-248">確認已選取測試訊息的訊息類型， **PO-Purchase Order (850)**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-248">Verify that the message type of the test message is selected, **PO - Purchase Order (850)**.</span></span>|  
        |<span data-ttu-id="dd4d2-249">**GS2**</span><span class="sxs-lookup"><span data-stu-id="dd4d2-249">**GS2**</span></span>|<span data-ttu-id="dd4d2-250">例如，輸入應用程式傳送者的值**Purchasing**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-250">Enter a value for the Application sender, for example, **Purchasing**.</span></span>|  
        |<span data-ttu-id="dd4d2-251">**GS3**</span><span class="sxs-lookup"><span data-stu-id="dd4d2-251">**GS3**</span></span>|<span data-ttu-id="dd4d2-252">例如，應用程式接收者中，輸入的值 **[ordercontrol]**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-252">Enter a value for the Application receiver, for example, **OrderControl**.</span></span>|  
        |<span data-ttu-id="dd4d2-253">**GS4**</span><span class="sxs-lookup"><span data-stu-id="dd4d2-253">**GS4**</span></span>|<span data-ttu-id="dd4d2-254">選取您想要的日期格式。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-254">Select the date format that you want.</span></span> <span data-ttu-id="dd4d2-255">**注意：** 您必須在下拉式清單中選取值，不只是按一下欄位以顯示預設值。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-255">**Note:**  You have to select the value in the drop-down list, not just click in the field to display the default.</span></span> <span data-ttu-id="dd4d2-256">如果您按一下欄位而未從下拉式清單中選取值，實際上不會選取值。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-256">If you click in the field without selecting the value from the drop-down list, the value will not actually be selected.</span></span>|  
        |<span data-ttu-id="dd4d2-257">**GS5**</span><span class="sxs-lookup"><span data-stu-id="dd4d2-257">**GS5**</span></span>|<span data-ttu-id="dd4d2-258">選擇您要的時間格式。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-258">Select the time format that you want.</span></span>|  
        |<span data-ttu-id="dd4d2-259">**GS7**</span><span class="sxs-lookup"><span data-stu-id="dd4d2-259">**GS7**</span></span>|<span data-ttu-id="dd4d2-260">選取**X-Accredited 的 Standards Committee X12**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-260">Select **X - Accredited Standards Committee X12**.</span></span>|  
        |<span data-ttu-id="dd4d2-261">**GS8**</span><span class="sxs-lookup"><span data-stu-id="dd4d2-261">**GS8**</span></span>|<span data-ttu-id="dd4d2-262">確認已輸入 EDI 版本， **00401**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-262">Verify that the EDI version has been entered, **00401**.</span></span>|  
  
        > [!NOTE]
        >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="dd4d2-263">將值，來設定 GS01、 GS02、 GS03、 GS04、 GS05、 GS07 和 GS08 輸出的輸入值為基礎的通知**交易類型**，**版本/版次**，和**目標命名空間**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-263"> will set the values for GS01, GS02, GS03, GS04, GS05, GS07, and GS08 of the outbound acknowledgments based on the values entered for **Transaction Type**, **Version/Release**, and **Target namespace**.</span></span> <span data-ttu-id="dd4d2-264">傳送管線會嘗試將交易集類型、X12 版本和目標命名空間，與訊息標頭中的對應值進行比對。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-264">The send pipeline attempts to match the transaction set type, the X12 version, and the target namespace with the corresponding values in the header of the message.</span></span> <span data-ttu-id="dd4d2-265">如果成功，它會使用相關聯的 GS 值**交易類型**，**版本/版次**，和**目標命名空間**值。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-265">If successful, it uses the GS values associated with the **Transaction Type**, **Version/Release**, and **Target namespace** values.</span></span>  
  
8.  <span data-ttu-id="dd4d2-266">在上執行下列工作**partyb-> party a**  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-266">Perform the following tasks on the **PartyB->PartyA** tab.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd4d2-267">在此逐步解說中，我們在索引標籤中指定必要值，以便可以順利地建立協議。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-267">In this walkthrough, we specify the required value in the tab so that an agreement can be successfully created.</span></span> <span data-ttu-id="dd4d2-268">若要成功地建立協議，兩個單向協議索引標籤必須已定義的值**ISA5**， **ISA6**， **ISA7**，和**ISA8**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-268">To successfully create an agreement, both one-way agreement tabs must have values defined for **ISA5**, **ISA6**, **ISA7**, and **ISA8**.</span></span>  
  
    1.  <span data-ttu-id="dd4d2-269">在**識別碼**頁面**交換設定**區段中，輸入辨識符號和識別項欄位的值 (**ISA5**， **ISA6**， **ISA7**，和**ISA8**) 對應到您的測試訊息中標頭欄位的值。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-269">On the **Identifiers** page under the **Interchange Settings** section, enter values for the qualifier and identifier fields (**ISA5**, **ISA6**, **ISA7**, and **ISA8**) that correspond to the values for those header fields in your test message.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="dd4d2-270">如果您使用 「 EDI 介面開發人員教學課程 」 中的 SamplePO.txt 檔案做為測試訊息，設定**ISA5**至**ZZ**， **ISA6**至**美國**， **ISA7**至**ZZ**，和**ISA8**至**THEM**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-270">If you are using the SamplePO.txt file from the “EDI Interface Developer Tutorial” as your test message, set **ISA5** to **ZZ**, **ISA6** to **US**, **ISA7** to **ZZ**, and **ISA8** to **THEM**.</span></span>  
  
9. <span data-ttu-id="dd4d2-271">按一下 **[套用]**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-271">Click **Apply**.</span></span>  
  
10. <span data-ttu-id="dd4d2-272">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-272">Click **OK**.</span></span> <span data-ttu-id="dd4d2-273">新增的協議會列在**協議**區段**合作對象與商務設定檔**窗格。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-273">The newly added agreement is listed in the **Agreements** section of the **Parties and Business Profiles** pane.</span></span> <span data-ttu-id="dd4d2-274">預設會啟用新增的協議。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-274">The newly added agreement is enabled by default.</span></span>  
  
##### <a name="to-create-a-static-one-way-send-port-to-send-the-batched-edi-interchange"></a><span data-ttu-id="dd4d2-275">若要建立靜態單向傳送埠以傳送批次 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="dd4d2-275">To create a static one-way send port to send the batched EDI interchange</span></span>  
  
1.  <span data-ttu-id="dd4d2-276">建立本機資料夾以將批次 EDI 訊息傳送至其中。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-276">Create a local folder to send the batched EDI message to.</span></span>  
  
2.  <span data-ttu-id="dd4d2-277">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**傳送埠**節點下的**BizTalk Application 1**節點，指向**新增**，然後按一下  **靜態單向傳送埠。**</span><span class="sxs-lookup"><span data-stu-id="dd4d2-277">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, right-click the **Send Ports** node under the **BizTalk Application 1** node, point to **New**, and then click **Static One-way Send Port.**</span></span>  
  
3.  <span data-ttu-id="dd4d2-278">在**傳送埠屬性**對話方塊、 傳送埠的名稱。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-278">In the **Send Port Properties** dialog box, name the send port.</span></span>  
  
4.  <span data-ttu-id="dd4d2-279">在**傳輸**區段中，選取**檔案**如**類型**，然後按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-279">In the **Transport** section, select **FILE** for **Type**, and then click **Configure**.</span></span>  
  
5.  <span data-ttu-id="dd4d2-280">輸入的資料夾**目的地資料夾**，和**檔案名稱**，例如 **%MessageID%.txt**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-280">Enter a folder for **Destination folder**, and a **File name**, such as **%MessageID%.txt**.</span></span>  
  
6.  <span data-ttu-id="dd4d2-281">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-281">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="dd4d2-282">在**傳送管線**，選取**EdiSend**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-282">In **Send pipeline**, select **EdiSend**.</span></span>  
  
8.  <span data-ttu-id="dd4d2-283">在主控台樹狀目錄中，選取**篩選**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-283">In the console tree, select **Filters**.</span></span> <span data-ttu-id="dd4d2-284">在**篩選**頁面上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="dd4d2-284">On the **Filters** page, do the following:</span></span>  
  
    1.  <span data-ttu-id="dd4d2-285">在方格的第一行中，選取**EDI。DestinationPartyName**如**屬性**，  **==** 如**運算子**，您所選取的合作對象傳送的批次名稱**值**，和**和**如**分組**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-285">On the first line of the grid, select **EDI.DestinationPartyName** for **Property**, **==** for **Operator**, the name you selected for the party to send the batch to for **Value**, and **And** for **Group by**.</span></span>  
  
    2.  <span data-ttu-id="dd4d2-286">在第二行中，選取**EDI。ToBeBatched**如**屬性**，  **==** 如**運算子**，和**False**如**值**，和**和**如**分組**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-286">On the second line, select **EDI.ToBeBatched** for **Property**, **==** for **Operator**, and **False** for **Value**, and **And** for **Group by**.</span></span>  
  
    3.  <span data-ttu-id="dd4d2-287">在第三行中，選取**EDI。BatchName**如**屬性**，  **==** 如**運算子**，和的批次名稱**值**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-287">On the third line, select **EDI.BatchName** for **Property**, **==** for **Operator**, and the name of the batch for **Value**.</span></span>  
  
9. <span data-ttu-id="dd4d2-288">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-288">Click **OK**.</span></span>  
  
10. <span data-ttu-id="dd4d2-289">在主控台樹狀目錄中，按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-289">In the console tree, click **Send Ports**.</span></span> <span data-ttu-id="dd4d2-290">在**傳送埠**] 窗格中，以滑鼠右鍵按一下您的傳送埠，然後按一下 [**啟動**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-290">In the **Send Ports** pane, right-click your send port, and then click **Start**.</span></span>  
  
##### <a name="to-associate-the-send-port-with-the-agreement-created-for-batching"></a><span data-ttu-id="dd4d2-291">若要讓傳送埠與建立要用於批次處理的協議產生關聯</span><span class="sxs-lookup"><span data-stu-id="dd4d2-291">To associate the send port with the agreement created for batching</span></span>  
  
1.  <span data-ttu-id="dd4d2-292">以滑鼠右鍵按一下您稍早建立的協議，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-292">Right-click the agreement you created earlier and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="dd4d2-293">在**協議屬性**對話方塊**party a-> partyb**索引標籤上，按一下 **傳送埠**的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-293">In the **Agreement Properties** dialog box, on the **PartyA->PartyB** tab, click **Send Ports** in the left pane.</span></span>  
  
3.  <span data-ttu-id="dd4d2-294">在**傳送埠**頁面**交換設定**區段中，將您稍早建立的傳送埠產生關聯。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-294">On the **Send Ports** page under the **Interchange Settings** section, associate the send port that you created earlier.</span></span> <span data-ttu-id="dd4d2-295">在**傳送埠**方格下方**名稱**資料行，按一下空白儲存格，然後從下拉式清單中，選取 傳送埠。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-295">In the **Send ports** grid, under the **Name** column, click an empty cell, and from the drop-down list, select the send port.</span></span>  
  
4.  <span data-ttu-id="dd4d2-296">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-296">Click **OK**.</span></span>  
  
### <a name="testing-the-walkthrough"></a><span data-ttu-id="dd4d2-297">測試逐步解說</span><span class="sxs-lookup"><span data-stu-id="dd4d2-297">Testing the Walkthrough</span></span>  
 <span data-ttu-id="dd4d2-298">本節提供關於如何測試逐步解說的資訊。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-298">This section provides information on how to test the walkthrough.</span></span>  
  
##### <a name="to-test-the-walkthrough"></a><span data-ttu-id="dd4d2-299">若要測試逐步解說</span><span class="sxs-lookup"><span data-stu-id="dd4d2-299">To test the walkthrough</span></span>  
  
1.  <span data-ttu-id="dd4d2-300">在 [Windows 檔案總管] 中，開啟與接收位置相關聯的本機資料夾，然後將測試 EDI 交換放置在該資料夾中。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-300">In Windows Explorer, open the local folder associated with the receive location, and drop a test EDI interchange into the folder.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd4d2-301">對於測試訊息，您可以使用「EDI 介面開發人員」教學課程中所使用的 850 範例訊息。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-301">For a test message, you can use the 850 sample message used for the EDI Interface Developer tutorial.</span></span> <span data-ttu-id="dd4d2-302">這是檔案中的 SamplePO.txt [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\\。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-302">This file is SamplePO.txt in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\\.</span></span> <span data-ttu-id="dd4d2-303">如果這樣做，您就必須使用位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI 中的結構描述 x12_00401_850.xsd。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-303">If you do so, you must use the schema x12_00401_850.xsd located in [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\EDI Interface Developer Tutorial\Inbound_EDI.</span></span>  
  
2.  <span data-ttu-id="dd4d2-304">將測試 EDI 交換的第二份複本放置到該資料夾中。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-304">Drop a second copy of the test EDI interchange into the folder.</span></span>  
  
3.  <span data-ttu-id="dd4d2-305">開啟您為了放置交換而與傳送埠產生關聯的資料夾，然後開啟批次交換。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-305">Open the folder that you associated with the send port for interchanges, and open the batched interchange.</span></span> <span data-ttu-id="dd4d2-306">確認此交換包含一組 ISA 與 GS 標頭和兩個交易集。</span><span class="sxs-lookup"><span data-stu-id="dd4d2-306">Verify that the interchange contains one set of ISA and GS headers, and two transaction sets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd4d2-307">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd4d2-307">See Also</span></span>  
 <span data-ttu-id="dd4d2-308">[開發和設定 BizTalk Server EDI 解決方案](../core/developing-and-configuring-biztalk-server-edi-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="dd4d2-308">[Developing and Configuring BizTalk Server EDI Solutions](../core/developing-and-configuring-biztalk-server-edi-solutions.md) </span></span>  
 <span data-ttu-id="dd4d2-309">[設定外寄批次](../core/configuring-an-outgoing-batch.md) </span><span class="sxs-lookup"><span data-stu-id="dd4d2-309">[Configuring an Outgoing Batch](../core/configuring-an-outgoing-batch.md) </span></span>  
 <span data-ttu-id="dd4d2-310">[組合批次的 EDI 交換](../core/assembling-a-batched-edi-interchange.md) </span><span class="sxs-lookup"><span data-stu-id="dd4d2-310">[Assembling a Batched EDI Interchange](../core/assembling-a-batched-edi-interchange.md) </span></span>  
 <span data-ttu-id="dd4d2-311">[組合批次的 EDI 交換](../core/assembling-a-batched-edi-interchange.md) </span><span class="sxs-lookup"><span data-stu-id="dd4d2-311">[Assembling a Batched EDI Interchange](../core/assembling-a-batched-edi-interchange.md) </span></span>  
 <span data-ttu-id="dd4d2-312">[逐步解說 (X12)： 接收 EDI 交換並傳回通知](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md) </span><span class="sxs-lookup"><span data-stu-id="dd4d2-312">[Walkthrough (X12): Receiving EDI Interchanges and Sending Back an Acknowledgement](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md) </span></span>  
 [<span data-ttu-id="dd4d2-313">逐步解說 (X12)： 傳送 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="dd4d2-313">Walkthrough (X12): Sending EDI Interchanges</span></span>](../core/walkthrough-x12-sending-edi-interchanges.md)