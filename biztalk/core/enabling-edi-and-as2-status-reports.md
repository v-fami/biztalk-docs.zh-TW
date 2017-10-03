---
title: "啟用 EDI 和 AS2 狀態報告 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa40fbad-51ad-40e0-9fe3-68e54beb11a5
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cef3d25040c253badd0f517326cc7830b6962df8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="enabling-edi-and-as2-status-reports"></a><span data-ttu-id="33d90-102">啟用 EDI 和 AS2 狀態報告</span><span class="sxs-lookup"><span data-stu-id="33d90-102">Enabling EDI and AS2 Status Reports</span></span>
<span data-ttu-id="33d90-103">本主題描述如何設定 EDI 和 AS2 狀態報告中的**群組概觀**頁面[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="33d90-103">This topic describes how to configure the EDI and AS2 status reports in the **Group Overview** page of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span>  
  
 <span data-ttu-id="33d90-104">狀態報告追蹤資料會根據以下程序所選的儲存區屬性，儲存於 BizTalk 追蹤資料庫 (BizTalkDTADb)。</span><span class="sxs-lookup"><span data-stu-id="33d90-104">Status reporting tracking data is stored in the BizTalk tracking database (BizTalkDTADb) in accordance with the storage properties selected in the procedures below.</span></span> <span data-ttu-id="33d90-105">您可以設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來啟用每個協議的狀態報告。</span><span class="sxs-lookup"><span data-stu-id="33d90-105">You can configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to enable status reporting for each agreement.</span></span> <span data-ttu-id="33d90-106">您應該根據儲存的資料量，例行地封存使用中存放區的資料，最後如果適用要從封存存放區清除這些資料。</span><span class="sxs-lookup"><span data-stu-id="33d90-106">Depending upon the amount of data that you store, you should routinely archive the data from the active store and ultimately clean it out from the archival store, as appropriate.</span></span> <span data-ttu-id="33d90-107">如需管理 BizTalkDTADb 資料庫的詳細資訊，請參閱[封存和清除 BizTalk 追蹤資料庫](../core/archiving-and-purging-the-biztalk-tracking-database.md)。</span><span class="sxs-lookup"><span data-stu-id="33d90-107">For more information about managing the BizTalkDTADb database, see [Archiving and Purging the BizTalk Tracking Database](../core/archiving-and-purging-the-biztalk-tracking-database.md).</span></span>  
  
 <span data-ttu-id="33d90-108">您可以用三種方式啟用狀態報告：</span><span class="sxs-lookup"><span data-stu-id="33d90-108">You can enable status reports in three ways:</span></span>  
  
-   <span data-ttu-id="33d90-109">針對解析為協議的輸入或輸出 EDI 交換，啟用狀態報告。</span><span class="sxs-lookup"><span data-stu-id="33d90-109">Enable status reports for inbound or outbound EDI interchanges that resolved to an agreement.</span></span>  
  
-   <span data-ttu-id="33d90-110">針對 EDI 後援協議屬性啟用狀態報告，以便針對 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 無法判斷其適用協議的 EDI 交換啟動狀態報告。</span><span class="sxs-lookup"><span data-stu-id="33d90-110">Enable status reports for EDI fallback agreement properties, so status reporting is activated for EDI interchanges that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] could not determine an agreement for.</span></span>  
  
-   <span data-ttu-id="33d90-111">啟用 AS2 訊息的狀態報告</span><span class="sxs-lookup"><span data-stu-id="33d90-111">Enable status reports for AS2 messages.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="33d90-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="33d90-112">Prerequisites</span></span>  
 <span data-ttu-id="33d90-113">您必須以成員的登入[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Administrators 群組或 BizTalk Server B2B 操作員 」 群組。</span><span class="sxs-lookup"><span data-stu-id="33d90-113">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group or BizTalk Server B2B Operators group.</span></span>  
  
### <a name="to-enable-edi-status-reports-for-an-agreement"></a><span data-ttu-id="33d90-114">若要啟用協議的 EDI 狀態報告</span><span class="sxs-lookup"><span data-stu-id="33d90-114">To enable EDI status reports for an agreement</span></span>  
  
1.  <span data-ttu-id="33d90-115">在**[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理**主控台中，按一下 **合作對象**節點下的[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]和**BizTalk 群組**節點。</span><span class="sxs-lookup"><span data-stu-id="33d90-115">In the **[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration** Console, click the **Parties** node under the [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] and **BizTalk Group** nodes.</span></span>  
  
2.  <span data-ttu-id="33d90-116">在**合作對象與商務設定檔** 窗格中，按一下您要啟用狀態報告的 X12 或 EDIFACT 協議的合作對象。</span><span class="sxs-lookup"><span data-stu-id="33d90-116">In the **Parties and Business Profiles** pane, click the party that has the X12 or EDIFACT agreement for which you want to enable status reporting.</span></span>  
  
3.  <span data-ttu-id="33d90-117">在**協議**區段中，以滑鼠右鍵按一下您要啟用狀態報告，然後按一下協的議**屬性**。</span><span class="sxs-lookup"><span data-stu-id="33d90-117">In the **Agreements** section, right-click the agreement for which you want to enable status reporting and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="33d90-118">在**一般**索引標籤的**一般主控件設定**區段中，按一下**開啟報告**。</span><span class="sxs-lookup"><span data-stu-id="33d90-118">In the **General** tab, in the **Common Host Settings** section, click **Turn ON Reporting**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="33d90-119">這個步驟會讓訊息項目輸入到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中的狀態報告 UI。</span><span class="sxs-lookup"><span data-stu-id="33d90-119">This step causes message entries to be entered in the status report UI in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span>  
  
5.  <span data-ttu-id="33d90-120">選取**儲存交易集/內容 reporting** ，將交易集儲存在追蹤 (BizTalkDTADb) 資料庫的 EDI 資料表中。</span><span class="sxs-lookup"><span data-stu-id="33d90-120">Select **Store transaction set/payload for reporting** to store transaction sets in the EDI tables of the tracking (BizTalkDTADb) database.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="33d90-121">如果您在啟動批次處理協調流程的執行個體時啟用交易集的儲存區，就不會為所建立的批次儲存交易集。</span><span class="sxs-lookup"><span data-stu-id="33d90-121">If you enable storage of transaction sets while an instance of the batching orchestration is activated, transaction sets will not be stored for the batch being created.</span></span> <span data-ttu-id="33d90-122">然而，如果您在啟動批次處理協調流程的執行個體時停用交易集的儲存區，則批次處理過程中便會停用該儲存區。</span><span class="sxs-lookup"><span data-stu-id="33d90-122">However, if you disable storage of transaction sets while an instance of the batching orchestration is activated, the storage will be disabled in the middle of the batching.</span></span>  
  
6.  <span data-ttu-id="33d90-123">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="33d90-123">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="33d90-124">重新啟動 BizTalk 服務 (在 [電腦管理] 對話方塊中)。</span><span class="sxs-lookup"><span data-stu-id="33d90-124">Restart the BizTalk Service (in the Computer Management dialog box).</span></span> <span data-ttu-id="33d90-125">如果正在方案中使用 AS2EdiReceive 管線或 AS2EdiSend 管線，重新啟動 IIS Admin service (使用*iisreset*命令)，以及。</span><span class="sxs-lookup"><span data-stu-id="33d90-125">If the AS2EdiReceive pipeline or the AS2EdiSend pipeline is being used in your solution, restart the IIS Admin service (using the *iisreset* command), as well.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="33d90-126">BizTalk 服務在 EDI 狀態報告啟動或停用之後必須重新啟動，讓變更生效。</span><span class="sxs-lookup"><span data-stu-id="33d90-126">The BizTalk Service needs to be restarted after EDI status reporting has been activated or deactivated for the change to take effect.</span></span> <span data-ttu-id="33d90-127">如果解決方案中使用的是 AS2EdiReceive 或 AS2EdiSend 管線，則 BizTalk 服務和 IIS 服務都必須重新啟動，變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="33d90-127">If the AS2EdiReceive or AS2EdiSend pipeline is being used in your solution, both the BizTalk Service and the IIS service need to be restarted for the change to take effect.</span></span> <span data-ttu-id="33d90-128">請注意，啟用 AS2 狀態報告時則不需要。</span><span class="sxs-lookup"><span data-stu-id="33d90-128">Note that this is not necessary when enabling AS2 status reporting.</span></span>  
  
### <a name="to-enable-edi-status-reports-for-fallback-agreements"></a><span data-ttu-id="33d90-129">若要啟用後援協議的 EDI 狀態報告</span><span class="sxs-lookup"><span data-stu-id="33d90-129">To enable EDI status reports for fallback agreements</span></span>  
  
1.  <span data-ttu-id="33d90-130">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**節點，以滑鼠右鍵按一下**合作對象**，然後選取**X12 後援設定**或**EDIFACT 後援設定**。</span><span class="sxs-lookup"><span data-stu-id="33d90-130">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group** nodes, right-click **Parties**, and select **X12 Fallback Settings** or **EDIFACT Fallback Settings**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="33d90-131">在後援協議中設定狀態報告時，只有在尚未決定訊息的協議時組態才適用。</span><span class="sxs-lookup"><span data-stu-id="33d90-131">When you configure status reports in the fallback agreements, the configuration only applies when no agreement has been determined for a message.</span></span>  
  
2.  <span data-ttu-id="33d90-132">在**後援設定一般頁面**索引標籤上，按一下 **啟動 EDI 報告**。</span><span class="sxs-lookup"><span data-stu-id="33d90-132">In the **Fallback Settings General Pages** tab, click **Activate EDI reporting**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="33d90-133">這個步驟會讓訊息項目輸入到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中的狀態報告 UI。</span><span class="sxs-lookup"><span data-stu-id="33d90-133">This step causes message entries to be entered in the status report UI in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span>  
  
3.  <span data-ttu-id="33d90-134">選取**儲存交易集/內容 reporting** ，將交易集儲存在追蹤 (BizTalkDTADb) 資料庫的 EDI 資料表中。</span><span class="sxs-lookup"><span data-stu-id="33d90-134">Select **Store transaction set/payload for reporting** to store transaction sets in the EDI tables of the tracking (BizTalkDTADb) database.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="33d90-135">**對於 EDIFACT 編碼訊息**： 如果您選取這個屬性，則您也必須在 [EDI 全域屬性] 對話方塊的 [UNB 區段定義] 頁面中選取 UNB3.2 欄位 （辨識符號） 的值。</span><span class="sxs-lookup"><span data-stu-id="33d90-135">**For EDIFACT-encoded messages**: If you select this property, you must also select a value for the UNB3.2 field (Code qualifier) in the UNB Segment Definition page of the EDI Global Properties dialog box.</span></span> <span data-ttu-id="33d90-136">根據預設，並未設定此屬性，以及交換將遭擱置，如果**儲存交易集/內容 reporting**已選取，但並未為 UNB3.2 選取值。</span><span class="sxs-lookup"><span data-stu-id="33d90-136">This property is not set by default, and the interchange will be suspended if **Store transaction set/payload for reporting** is selected, but a value is not selected for UNB3.2.</span></span>  
  
4.  <span data-ttu-id="33d90-137">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="33d90-137">Click **OK**.</span></span>  
  
### <a name="to-enable-as2-status-reports"></a><span data-ttu-id="33d90-138">若要啟用 AS2 狀態報告</span><span class="sxs-lookup"><span data-stu-id="33d90-138">To enable AS2 status reports</span></span>  
  
1.  <span data-ttu-id="33d90-139">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]和**BizTalk 群組**節點，按一下**合作對象**節點。</span><span class="sxs-lookup"><span data-stu-id="33d90-139">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, under the [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)] and **BizTalk Group** nodes, click the **Parties** node.</span></span>  
  
2.  <span data-ttu-id="33d90-140">在**合作對象與商務設定檔** 窗格中，按一下您要啟用狀態報告的 X12 或 EDIFACT 協議的合作對象。</span><span class="sxs-lookup"><span data-stu-id="33d90-140">In the **Parties and Business Profiles** pane, click the party that has the X12 or EDIFACT agreement for which you want to enable status reporting.</span></span>  
  
3.  <span data-ttu-id="33d90-141">在**協議**區段中，以滑鼠右鍵按一下您要啟用狀態報告，然後按一下協的議**屬性**。</span><span class="sxs-lookup"><span data-stu-id="33d90-141">In the **Agreements** section, right-click the agreement for which you want to enable status reporting and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="33d90-142">在**一般主控件設定**區段中，按一下**開啟報告**。</span><span class="sxs-lookup"><span data-stu-id="33d90-142">In the **Common Host Settings** section, click **Turn ON Reporting**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="33d90-143">這個步驟會讓訊息項目輸入到 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管理主控台中的狀態報告 UI。</span><span class="sxs-lookup"><span data-stu-id="33d90-143">This step causes message entries to be entered in the status report UI in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.</span></span>  
  
5.  <span data-ttu-id="33d90-144">在單向協議索引標籤的**協議屬性**對話方塊中，按一下 **接收者訊息追蹤 (NRR)**頁面。</span><span class="sxs-lookup"><span data-stu-id="33d90-144">In the one-way agreement tab of the **Agreement Properties** dialog box, click the **Receiver Message Tracking (NRR)** page.</span></span>  
  
6.  <span data-ttu-id="33d90-145">在**接收者訊息追蹤 (NRR)**頁面上，按一下**為輸入的編碼 AS2 訊息啟用 NRR**以啟用內送訊息的電傳格式顯示。</span><span class="sxs-lookup"><span data-stu-id="33d90-145">In the **Receiver Message Tracking (NRR)** page, click **NRR enabled for inbound encoded AS2 messages** to enable display of the wire format of incoming messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="33d90-146">當您以滑鼠右鍵按一下 [AS2 訊息和相互關聯的 MDN 狀態] 頁面中的訊息，然後按一下時，將會顯示訊息的電傳格式**訊息電傳格式**。</span><span class="sxs-lookup"><span data-stu-id="33d90-146">The wire format of the message will be displayed when you right-click the message in the AS2 Message and Correlated MDN Status Page, and then click **Message Wire Format**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="33d90-147">**開啟報告**必須選取屬性，您才能啟用不可否認性資料庫中的任何資料的儲存體。</span><span class="sxs-lookup"><span data-stu-id="33d90-147">The **Turn ON Reporting** property must be selected for you to enable storage of any data in the non-repudiation database.</span></span> <span data-ttu-id="33d90-148">如果您選取這個屬性或其他啟用不可否認性資料庫中之儲存區的屬性，就會顯示快顯提示您啟動 AS2 報告。</span><span class="sxs-lookup"><span data-stu-id="33d90-148">If you select this or any of the other properties enabling storage in the non-repudiation database, a popup will be displayed prompting you to activate AS2 reporting.</span></span> <span data-ttu-id="33d90-149">如果您按一下**是**，將會為您啟動 AS2 報告。</span><span class="sxs-lookup"><span data-stu-id="33d90-149">If you click **Yes**, AS2 reporting will be activated for you.</span></span>  
  
7.  <span data-ttu-id="33d90-150">在**接收者訊息追蹤 (NRR)**頁面上，按一下**為輸入的解碼 AS2 訊息啟用 NRR**以啟用內送訊息的解碼格式顯示。</span><span class="sxs-lookup"><span data-stu-id="33d90-150">In the **Receiver Message Tracking (NRR)** page, click **NRR enabled for inbound decoded AS2 messages** to enable display of the decoded format of incoming messages.</span></span>  
  
8.  <span data-ttu-id="33d90-151">在**接收者訊息追蹤 (NRR)**頁面上，按一下**為輸出的 MDN 啟用 NRR**以啟用內送訊息 MDN 回應的顯示。</span><span class="sxs-lookup"><span data-stu-id="33d90-151">In the **Receiver Message Tracking (NRR)** page, click **NRR enabled for outbound MDN** to enable display of MDN responses to incoming messages.</span></span>  
  
9. <span data-ttu-id="33d90-152">在單向協議索引標籤的**協議屬性**對話方塊中，按一下 **寄件者訊息追蹤 (NRR)**頁面。</span><span class="sxs-lookup"><span data-stu-id="33d90-152">In the one-way agreement tab of the **Agreement Properties** dialog box, click the **Sender Message Tracking (NRR)** page.</span></span>  
  
10. <span data-ttu-id="33d90-153">在**寄件者訊息追蹤 (NRR)**頁面上，按一下**為輸出的編碼 AS2 訊息啟用 NRR**以啟用外寄訊息的電傳格式顯示。</span><span class="sxs-lookup"><span data-stu-id="33d90-153">In the **Sender Message Tracking (NRR)** page, click **NRR enabled for outbound encoded AS2 messages** to enable display of the wire format of outgoing messages.</span></span>  
  
11. <span data-ttu-id="33d90-154">在**寄件者訊息追蹤 (NRR)**頁面上，按一下**為輸出的解碼 AS2 訊息啟用 NRR**以啟用外寄訊息的解碼格式顯示。</span><span class="sxs-lookup"><span data-stu-id="33d90-154">In the **Sender Message Tracking (NRR)** page, click **NRR enabled for outbound decoded AS2 messages** to enable display of the decoded format of outgoing messages.</span></span>  
  
12. <span data-ttu-id="33d90-155">在**寄件者訊息追蹤 (NRR)**頁面上，按一下**為輸入的 MDN 啟用 NRR**以啟用外寄訊息 MDN 回應的顯示。</span><span class="sxs-lookup"><span data-stu-id="33d90-155">In the **Sender Message Tracking (NRR)** page, click **NRR enabled for inbound MDN** to enable display of MDN responses to outgoing messages.</span></span>  
  
13. <span data-ttu-id="33d90-156">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="33d90-156">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33d90-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33d90-157">See Also</span></span>  
 <span data-ttu-id="33d90-158">[監控 EDI 和 AS2 解決方案](../core/monitoring-edi-and-as2-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="33d90-158">[Monitoring EDI and AS2 Solutions](../core/monitoring-edi-and-as2-solutions.md) </span></span>  
 <span data-ttu-id="33d90-159">[設定 EDI 和 AS2 狀態報告](../core/configuring-an-edi-and-as2-status-report.md) </span><span class="sxs-lookup"><span data-stu-id="33d90-159">[Configuring an EDI and AS2 Status Report](../core/configuring-an-edi-and-as2-status-report.md) </span></span>  
 [<span data-ttu-id="33d90-160">EDI 和 AS2 狀態報告</span><span class="sxs-lookup"><span data-stu-id="33d90-160">EDI and AS2 Status Reporting</span></span>](../core/edi-and-as2-status-reporting.md)   