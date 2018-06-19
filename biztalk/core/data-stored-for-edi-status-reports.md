---
title: EDI 狀態報告的儲存資料 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ec66e4d7-2694-499f-a60c-2f80fe643e12
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9395cb3895675e586576088f3d257dbf4115948f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25970620"
---
# <a name="data-stored-for-edi-status-reports"></a><span data-ttu-id="ad4fc-102">EDI 狀態報告的儲存資料</span><span class="sxs-lookup"><span data-stu-id="ad4fc-102">Data Stored for EDI Status Reports</span></span>
<span data-ttu-id="ad4fc-103">EDI 狀態報告中有兩個層級的報告： 第一個 if**開啟報告**協議，和第二個如果選取屬性**儲存交易集/內容報告**選取協議屬性。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-103">Two levels of reporting are available in EDI status reporting: the first if the **Turn ON Reporting** property is selected for an agreement, and the second if the **Store transaction set/payload reporting** property is selected for an agreement.</span></span> <span data-ttu-id="ad4fc-104">這些屬性可用於**一般屬性**頁面**一般**索引標籤中**協議屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-104">These properties are available in the **General Properties** page of the **General** tab in the **Agreement Properties** dialog box.</span></span>  
  
## <a name="data-stored-if-edi-reporting-is-activated"></a><span data-ttu-id="ad4fc-105">啟動 EDI 報告時的儲存資料</span><span class="sxs-lookup"><span data-stu-id="ad4fc-105">Data Stored If EDI Reporting Is Activated</span></span>  
 <span data-ttu-id="ad4fc-106">如果**開啟報告**協議中，選取屬性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會保留所有已傳送或接收之交換、 技術通知以及功能通知的記錄。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-106">If the **Turn ON Reporting** property is selected for an agreement, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will keep a record of all sent or received interchanges, technical acknowledgments, and functional acknowledgments.</span></span>  
  
 <span data-ttu-id="ad4fc-107">對於已接收的交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會儲存下列資訊：</span><span class="sxs-lookup"><span data-stu-id="ad4fc-107">For a received interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stores the following information:</span></span>  
  
-   <span data-ttu-id="ad4fc-108">所有已接收交換的記錄。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-108">A record of all received interchanges.</span></span> <span data-ttu-id="ad4fc-109">這是 EDI 狀態報告 UI 中顯示的第一筆資訊。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-109">This is the first information displayed in the status reporting UI for EDI.</span></span>  
  
-   <span data-ttu-id="ad4fc-110">包含於交換中之所有交易集的記錄。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-110">A record of all transaction sets contained in the interchange.</span></span> <span data-ttu-id="ad4fc-111">這並不包括啟用交易集儲存區時所儲存的所有詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-111">This does not include all the details that are stored when transaction-set storage is enabled.</span></span>  
  
-   <span data-ttu-id="ad4fc-112">出現在已接收交換中之所有技術通知的記錄。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-112">A record of all Technical acknowledgments present in the received interchange</span></span>  
  
-   <span data-ttu-id="ad4fc-113">出現在已接收交換中之所有功能通知的記錄。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-113">A record of all Functional acknowledgments present in the received interchange</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ad4fc-114">如果交換具有多個功能群組，狀態報告 UI 中就會儲存多個功能通知。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-114">If an interchange has multiple functional groups, multiple functional acknowledgments will be stored in the status reporting UI.</span></span> <span data-ttu-id="ad4fc-115">然而，如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 收到某個群組的重複功能通知，則 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 只會將最近一個功能通知儲存到狀態報告 UI 中。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-115">However, if [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives duplicate functional acknowledgments for a group, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will store only the last functional acknowledgment in the status reporting UI.</span></span>  
  
-   <span data-ttu-id="ad4fc-116">是否需要為已接收的交換產生技術通知。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-116">Whether a technical acknowledgment needs to be generated for the received interchange</span></span>  
  
-   <span data-ttu-id="ad4fc-117">是否需要為已接收的交易集產生功能通知。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-117">Whether functional acknowledgments need to be generated for the received transaction sets</span></span>  
  
 <span data-ttu-id="ad4fc-118">對於已傳送的交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會儲存下列資訊：</span><span class="sxs-lookup"><span data-stu-id="ad4fc-118">For a sent interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stores the following information:</span></span>  
  
-   <span data-ttu-id="ad4fc-119">已傳送交換的記錄。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-119">A record of the sent interchange</span></span>  
  
-   <span data-ttu-id="ad4fc-120">包含於交換中之所有交易集的記錄。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-120">A record of all transaction sets contained in the interchange</span></span>  
  
-   <span data-ttu-id="ad4fc-121">出現在已傳送交換中之所有技術通知的記錄。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-121">A record of all Technical acknowledgments present in the sent interchange</span></span>  
  
-   <span data-ttu-id="ad4fc-122">出現在已傳送交換中之所有功能通知的記錄。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-122">A record of all Functional acknowledgments present in the sent interchange</span></span>  
  
 <span data-ttu-id="ad4fc-123">EDI 狀態報告 UI 會將這些記錄相互關聯以顯示完整的資訊。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-123">EDI status reporting UI correlates these records to display complete information.</span></span> <span data-ttu-id="ad4fc-124">例如，如果 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 收到某個交換，而且需要向原始訊息的傳送者發送技術通知和功能通知，您便可以在狀態報告 UI 中輕易找到這項資訊。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-124">For example, if [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives an interchange, and a technical acknowledgment and a functional acknowledgment need to be sent to the sender of the original message, you can easily find this information in the status reporting UI.</span></span>  
  
## <a name="data-stored-if-transaction-set-storage-is-enabled"></a><span data-ttu-id="ad4fc-125">啟用交易集儲存區時的儲存資料</span><span class="sxs-lookup"><span data-stu-id="ad4fc-125">Data Stored If Transaction Set Storage Is Enabled</span></span>  
 <span data-ttu-id="ad4fc-126">如果**儲存報告的訊息內容**協議中，選取屬性[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會儲存已傳送或接收交換中找到的所有交易集的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-126">If the **Store message payload for reporting** property is selected for an agreement, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will store details of all transaction sets found in a sent or received interchange.</span></span> <span data-ttu-id="ad4fc-127">如果有啟動 EDI 報告，這個層級的狀態報告便會實作所有執行的第一層級報告，並會加上交易集的專屬資訊。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-127">This level of status reporting implements all of the first-level reporting performed if EDI reporting is activated, plus transaction-set specific information.</span></span> <span data-ttu-id="ad4fc-128">EDI 接收管線和傳送管線產生項目在 BAM 資料庫的每個內送和外寄群組或交易集 (雖然"**報告的儲存訊息內容**選取屬性)。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-128">The EDI receive pipeline and send pipeline make entries in the BAM database for each incoming and outgoing Group/Transaction Set (while the "**Store message payload reporting** property is selected).</span></span> <span data-ttu-id="ad4fc-129">如果該交換遭到拒絕，就不會產生任何項目。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-129">If the interchange is rejected, no entry is made.</span></span>  
  
 <span data-ttu-id="ad4fc-130">對於傳送或接收的交換，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]儲存下列資訊：</span><span class="sxs-lookup"><span data-stu-id="ad4fc-130">For a sent or received interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stores the following information:</span></span>  
  
-   <span data-ttu-id="ad4fc-131">交易集內容。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-131">The transaction set content.</span></span> <span data-ttu-id="ad4fc-132">在狀態報告 UI 中，您可以查看交換所包含的交易集，然後再檢視實際的交易集內容。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-132">In the status reporting UI, you can look at the transaction sets contained in an interchange, and then view the actual transaction set content.</span></span>  
  
-   <span data-ttu-id="ad4fc-133">有關交易集的其他詳細資訊包括如下：</span><span class="sxs-lookup"><span data-stu-id="ad4fc-133">More detailed information about a transaction set, including the following:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ad4fc-134">資訊</span><span class="sxs-lookup"><span data-stu-id="ad4fc-134">Information</span></span>|<span data-ttu-id="ad4fc-135">欄位或值</span><span class="sxs-lookup"><span data-stu-id="ad4fc-135">Field or Value</span></span>|  
|<span data-ttu-id="ad4fc-136">ApplicationSender</span><span class="sxs-lookup"><span data-stu-id="ad4fc-136">ApplicationSender</span></span>|<span data-ttu-id="ad4fc-137">(GS02 或\<UNG2.1(UNG2.2)\></span><span class="sxs-lookup"><span data-stu-id="ad4fc-137">(GS02 or \<UNG2.1(UNG2.2)\></span></span>|  
|<span data-ttu-id="ad4fc-138">ApplicationReceiver</span><span class="sxs-lookup"><span data-stu-id="ad4fc-138">ApplicationReceiver</span></span>|<span data-ttu-id="ad4fc-139">GS03 或\<UNG3.1(UNG3.2)\></span><span class="sxs-lookup"><span data-stu-id="ad4fc-139">GS03 or \<UNG3.1(UNG3.2)\></span></span>|  
|<span data-ttu-id="ad4fc-140">GroupDate</span><span class="sxs-lookup"><span data-stu-id="ad4fc-140">GroupDate</span></span>|<span data-ttu-id="ad4fc-141">GS04 或 UNG2.4</span><span class="sxs-lookup"><span data-stu-id="ad4fc-141">GS04 or UNG2.4</span></span>|  
|<span data-ttu-id="ad4fc-142">GroupTime</span><span class="sxs-lookup"><span data-stu-id="ad4fc-142">GroupTime</span></span>|<span data-ttu-id="ad4fc-143">GS05 或 UNG2.5</span><span class="sxs-lookup"><span data-stu-id="ad4fc-143">GS05 or UNG2.5</span></span>|  
|<span data-ttu-id="ad4fc-144">TransactionSetId</span><span class="sxs-lookup"><span data-stu-id="ad4fc-144">TransactionSetId</span></span>|<span data-ttu-id="ad4fc-145">ST01 或 UNH2.1 （AN 字串）</span><span class="sxs-lookup"><span data-stu-id="ad4fc-145">ST01 or  UNH2.1 (AN string)</span></span>|  
|<span data-ttu-id="ad4fc-146">InterchangeControlNo</span><span class="sxs-lookup"><span data-stu-id="ad4fc-146">InterchangeControlNo</span></span>|<span data-ttu-id="ad4fc-147">ISA13</span><span class="sxs-lookup"><span data-stu-id="ad4fc-147">ISA13</span></span>|  
|<span data-ttu-id="ad4fc-148">GroupControlNo</span><span class="sxs-lookup"><span data-stu-id="ad4fc-148">GroupControlNo</span></span>|<span data-ttu-id="ad4fc-149">GS06</span><span class="sxs-lookup"><span data-stu-id="ad4fc-149">GS06</span></span>|  
|<span data-ttu-id="ad4fc-150">BtsDocType</span><span class="sxs-lookup"><span data-stu-id="ad4fc-150">BtsDocType</span></span>|<span data-ttu-id="ad4fc-151">NameSpace + Root 節點名稱</span><span class="sxs-lookup"><span data-stu-id="ad4fc-151">NameSpace + Root node name</span></span>|  
|<span data-ttu-id="ad4fc-152">TransactionSetControlID</span><span class="sxs-lookup"><span data-stu-id="ad4fc-152">TransactionSetControlID</span></span>|<span data-ttu-id="ad4fc-153">ST02 或 UNH1</span><span class="sxs-lookup"><span data-stu-id="ad4fc-153">ST02 or UNH1</span></span>|  
|<span data-ttu-id="ad4fc-154">TransactionSetStatus</span><span class="sxs-lookup"><span data-stu-id="ad4fc-154">TransactionSetStatus</span></span>|<span data-ttu-id="ad4fc-155">Accepted、AcceptedWithError 或 Rejected</span><span class="sxs-lookup"><span data-stu-id="ad4fc-155">Accepted, AcceptedWithError, or Rejected</span></span>|  
|<span data-ttu-id="ad4fc-156">方向</span><span class="sxs-lookup"><span data-stu-id="ad4fc-156">Direction</span></span>|<span data-ttu-id="ad4fc-157">傳送或接收</span><span class="sxs-lookup"><span data-stu-id="ad4fc-157">Send or Receive</span></span>|  
|<span data-ttu-id="ad4fc-158">BtsProcessingTime</span><span class="sxs-lookup"><span data-stu-id="ad4fc-158">BtsProcessingTime</span></span>|<span data-ttu-id="ad4fc-159">在接收端：做為管線中戳記的 BTSReceiveTime (本地時間)</span><span class="sxs-lookup"><span data-stu-id="ad4fc-159">On receive side: BTSReceiveTime (local time) as stamped in the Pipeline</span></span><br /><br /> <span data-ttu-id="ad4fc-160">在傳送端：由 ASM 元件加上做為信封上戳記的 BTSSendTime (本地時間)</span><span class="sxs-lookup"><span data-stu-id="ad4fc-160">On send side: BTSSendTime as (local time) stamped on the envelope by the ASM component</span></span>|  
|<span data-ttu-id="ad4fc-161">BTS.MessageId</span><span class="sxs-lookup"><span data-stu-id="ad4fc-161">BTS.MessageId</span></span>|<span data-ttu-id="ad4fc-162">在接收端：來自訊息屬性的 BTSMessageId</span><span class="sxs-lookup"><span data-stu-id="ad4fc-162">On receive side: BTSMessageId from message properties</span></span><br /><br /> <span data-ttu-id="ad4fc-163">在傳送端：</span><span class="sxs-lookup"><span data-stu-id="ad4fc-163">On send side:</span></span><br /><br /> <span data-ttu-id="ad4fc-164">對於單一交易集：BTSMessageId</span><span class="sxs-lookup"><span data-stu-id="ad4fc-164">For single Transaction Set: BTSMessageId</span></span><br /><br /> <span data-ttu-id="ad4fc-165">對於輸出批次： 批次 (不是批次訊息的 BTSMessageId) 中的每個個別訊息的 TransactionSet BTSMessageId**附註：** 儲存體只 – 將不會顯示在 UI 中。</span><span class="sxs-lookup"><span data-stu-id="ad4fc-165">For outbound batch: TransactionSet BTSMessageId for each individual message in batch (not the BTSMessageId for the batch message) **Note:**  Storage only – will not be displayed in UI.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad4fc-166">請參閱</span><span class="sxs-lookup"><span data-stu-id="ad4fc-166">See Also</span></span>  
 <span data-ttu-id="ad4fc-167">[EDI 和 AS2 狀態報告的儲存資料](../core/data-stored-for-edi-and-as2-status-reports.md) </span><span class="sxs-lookup"><span data-stu-id="ad4fc-167">[Data Stored for EDI and AS2 Status Reports](../core/data-stored-for-edi-and-as2-status-reports.md) </span></span>  
 <span data-ttu-id="ad4fc-168">[針對批次狀態報告儲存的資料](../core/data-stored-for-batching-status-reports.md) </span><span class="sxs-lookup"><span data-stu-id="ad4fc-168">[Data Stored for Batching Status Reports](../core/data-stored-for-batching-status-reports.md) </span></span>  
 [<span data-ttu-id="ad4fc-169">AS2 狀態報告的儲存資料</span><span class="sxs-lookup"><span data-stu-id="ad4fc-169">Data Stored for AS2 Status Reports</span></span>](../core/data-stored-for-as2-status-reports.md)