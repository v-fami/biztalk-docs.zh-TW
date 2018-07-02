---
title: 相互關聯的內送交易集與外寄批次 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2fbe40f8-7379-42be-b8a7-070ce8a7ce26
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b44f89133cbfb7f5925f975a723b84c715180c7a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013799"
---
# <a name="correlating-an-incoming-transaction-set-with-an-outgoing-batch"></a><span data-ttu-id="9b2cf-102">使內送交易集與外寄批次相互關聯</span><span class="sxs-lookup"><span data-stu-id="9b2cf-102">Correlating an Incoming Transaction Set with an Outgoing Batch</span></span>
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9b2cf-103"> 可讓您將提交至「批次處理協調流程」的 EDI 交易集與外寄批次相互關聯。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-103"> enables you to correlate an EDI transaction set submitted to the Batching Orchestration with an outgoing batch.</span></span> <span data-ttu-id="9b2cf-104">您可以透過讓提交至「批次處理協調流程」(BTSInterchangeID) 的狀態報告項目與協調流程 (ActivityID) 的狀態報告項目相互關聯，藉此完成這項操作。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-104">You do so by correlating a status reporting entry for the transaction set submitted to the Batching Orchestration (the BTSInterchangeID) to a status reporting entry for the orchestration (ActivityID).</span></span> <span data-ttu-id="9b2cf-105">此相互關聯是使用 BusinessMessageJournal BAM 活動中的項目執行。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-105">This correlation is performed using entries in the BusinessMessageJournal BAM activity.</span></span> <span data-ttu-id="9b2cf-106">這些項目是由「批次處理協調流程」在接收批次元素時建立。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-106">These entries are created by the Batching Orchestration when a batch element is received.</span></span>  
  
> [!IMPORTANT]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9b2cf-107"> EDI 狀態報告和交易集追蹤已啟用協議時，才會建立在 BusinessMessageJournal 活動中的項目。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-107"> will make entries in the BusinessMessageJournal activity only if EDI status reporting and Transaction Set tracking is enabled for the agreement.</span></span>  
  
 <span data-ttu-id="9b2cf-108">下列章節會說明下列內容：</span><span class="sxs-lookup"><span data-stu-id="9b2cf-108">The sections below describe the following:</span></span>  
  
- <span data-ttu-id="9b2cf-109">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 如何儲存追蹤資料</span><span class="sxs-lookup"><span data-stu-id="9b2cf-109">How [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] saves tracking data</span></span>  
  
- <span data-ttu-id="9b2cf-110">如何建立自訂管線元件來啟用相互關聯</span><span class="sxs-lookup"><span data-stu-id="9b2cf-110">How you can create a custom pipeline component to enable correlation</span></span>  
  
- <span data-ttu-id="9b2cf-111">如何使內送交易集與外寄批次相互關聯</span><span class="sxs-lookup"><span data-stu-id="9b2cf-111">How you can correlate an incoming transaction set with an outgoing batch.</span></span>  
  
- <span data-ttu-id="9b2cf-112">如何在已知批次中所包含交易集的 BTSInterchangeID 時查詢 BusinessMessageJournal 活動以判斷批次的 BTSInterchangeID。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-112">How you can query the BusinessMessageJournal activity to determine the BTSInterchangeID of the batch if you know the BTSInterchangeID of the transaction set contained in the batch.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9b2cf-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="9b2cf-113">Prerequisites</span></span>  
 <span data-ttu-id="9b2cf-114">您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-114">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators or [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B Operators group.</span></span>  
  
## <a name="changes-to-the-activities"></a><span data-ttu-id="9b2cf-115">活動的變更</span><span class="sxs-lookup"><span data-stu-id="9b2cf-115">Changes to the Activities</span></span>  
 <span data-ttu-id="9b2cf-116">「批次處理協調流程」會在 BatchingActivity、TransactionSetActivity 和 BusinessMessageJournal BAM 活動中建立項目。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-116">The Batching Orchestration makes entries in the BatchingActivity, TransactionSetActivity, and BusinessMessageJournal BAM activities.</span></span> <span data-ttu-id="9b2cf-117">為交易集通過[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]交易集的批次包含這些活動資料表中將下列項目：</span><span class="sxs-lookup"><span data-stu-id="9b2cf-117">As a transaction set moves through [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will make the following entries in these activity tables for the transaction set and the batch that includes it:</span></span>  
  
1.  <span data-ttu-id="9b2cf-118">當 EDI 解譯器處理內送 EDI 交換時，會在 InterchangeStatusActivity 和 TransactionSetActivity 資料表中建立項目。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-118">When the EDI disassembler processes an incoming EDI interchange, it creates entries in the InterchangeStatusActivity and the TransactionSetActivity tables.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9b2cf-119">如需有關 BAM 活動的詳細資訊，請參閱[來追蹤 EDI-AS2 訊息的 BAM 活動建立](../core/bam-activities-created-to-track-edi-as2-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-119">For more information about the BAM activities, see [BAM Activities Created to Track EDI-AS2 Messages](../core/bam-activities-created-to-track-edi-as2-messages.md).</span></span>  
  
2.  <span data-ttu-id="9b2cf-120">當「批次處理協調流程」產生時，協調流程就會在 BatchingActivity 中建立一個項目。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-120">When the Batching Orchestration is instantiated, the orchestration creates an entry in the BatchingActivity.</span></span> <span data-ttu-id="9b2cf-121">BAM 子系統會為 ActivityID 建立一個值。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-121">The BAM subsystem creates a value for the ActivityID.</span></span>  
  
3.  <span data-ttu-id="9b2cf-122">批次處理協調流程挑選了交易集之後，就會在 TransactionSetActivity 資料表中建立交易集的項目。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-122">After the batching orchestration has picked up the transaction set, it creates an entry for the transaction set in the TransactionSetActivity table.</span></span>  
  
4.  <span data-ttu-id="9b2cf-123">協調流程會在 BusinessMessageJournal 活動中建立一個項目。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-123">The orchestration creates an entry in the BusinessMessageJournal activity.</span></span> <span data-ttu-id="9b2cf-124">它會將此活動的 MessageTrackingID 欄位設定為協調流程在 TransactionSetActivity 資料表中所建立項目的 ActivityID 欄位值。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-124">It sets the MessageTrackingID field of this activity to the value of the ActivityID field of the entry that the orchestration created in TransactionSetActivity table.</span></span> <span data-ttu-id="9b2cf-125">此外還會將 BTSInterchangeID 欄位設為交易集的 BTS.InterchangeID 內容屬性，以及將 BTSMessageID 欄位設為交易集的 BTS.MessageID 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-125">It also sets the BTSInterchangeID field to the BTS.InterchangeID context property for the transaction set and the BTSMessageID field to the BTS.MessageID context property for the transaction set.</span></span>  
  
5.  <span data-ttu-id="9b2cf-126">協調流程會在 BusinessMessageJournal 活動中建立第二個項目。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-126">The orchestration creates a second entry in the BusinessMessageJournal activity.</span></span> <span data-ttu-id="9b2cf-127">它會將 MessageTrackingID 欄位設定為協調流程在 TransactionSetActivity 資料表中所建立項目的 ActivityID 欄位，</span><span class="sxs-lookup"><span data-stu-id="9b2cf-127">It sets the MessageTrackingID field to the ActivityID field of the entry that the orchestration created in TransactionSetActivity table.</span></span> <span data-ttu-id="9b2cf-128">以及將 BTSInterchangeID 欄位設為批次的 BTS.InterchangeID 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-128">It sets the BTSInterchangeID field to the BTS.InterchangeID context property for the batch.</span></span> <span data-ttu-id="9b2cf-129">不過不會設定 BTSMessageID。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-129">It does not set the BTSMessageID.</span></span> <span data-ttu-id="9b2cf-130">另外還會將 ContainerActivityID 設為 BatchingActivity 中 ActivityID 的值。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-130">It sets the ContainerActivityID to the value of the ActivityID in the BatchingActivity.</span></span>  
  
## <a name="creating-a-custom-pipeline-component-for-enabling-correlation"></a><span data-ttu-id="9b2cf-131">建立自訂管線元件來啟用相互關聯</span><span class="sxs-lookup"><span data-stu-id="9b2cf-131">Creating a Custom Pipeline Component for Enabling Correlation</span></span>  
 <span data-ttu-id="9b2cf-132">若要建立內送交易集與包含交易集的外寄批次之間的相互關聯，您必須建立自訂管線元件。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-132">To set up correlation of an incoming transaction set with an outgoing batch that contains that transaction set, you need to create a custom pipeline component.</span></span> <span data-ttu-id="9b2cf-133">此管線元件應在 EDI 解譯器之後，並且在 EDIReceive 管線的 BatchMarker 元件之前。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-133">This pipeline component should come after the EDI Disassembler and before the BatchMarker component of the EDIReceive pipeline.</span></span> <span data-ttu-id="9b2cf-134">此管線元件必須在 BusinessMessageJournal 活動中建立一個項目。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-134">This pipeline component needs to create an entry in the BusinessMessageJournal activity.</span></span> <span data-ttu-id="9b2cf-135">在此項目中，BTSInterchangeID 欄位應設為 BTS.InterchangeID 內容屬性，而 BTSMessageID 欄位應設為 BTS.MessageID 內容屬性。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-135">In this entry, the BTSInterchangeID field should be set to the BTS.InterchangeID context property and the BTSMessageID field should be set to the BTS.MessageID context property.</span></span>  
  
## <a name="looking-up-the-interchangeid-for-a-transaction-set-in-a-batch"></a><span data-ttu-id="9b2cf-136">查閱批次中交易集的 InterchangeID</span><span class="sxs-lookup"><span data-stu-id="9b2cf-136">Looking Up the InterchangeID for a Transaction Set in a Batch</span></span>  
 <span data-ttu-id="9b2cf-137">您可以透過使用 BatchingActivity 資料表和 BusinessMessageJournal 活動中的項目，使收到的交換與包含交換中交易集的批次相互關聯，如下所述。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-137">You correlate a received interchange, and the batch that contains the transaction set from the interchange, by using the entries in the BatchingActivity table and the BusinessMessageJournal activity, as described below.</span></span>  
  
### <a name="to-correlate-an-incoming-transaction-set-with-an-outgoing-batch-that-contains-that-transaction-set"></a><span data-ttu-id="9b2cf-138">使內送交易集與包含該交易集的外寄批次相互關聯</span><span class="sxs-lookup"><span data-stu-id="9b2cf-138">To correlate an incoming transaction set with an outgoing batch that contains that transaction set</span></span>  
  
1.  <span data-ttu-id="9b2cf-139">判斷 BatchingActivity 資料表中批次的 ActivityID 值。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-139">Determine the value of ActivityID for the batch in the BatchingActivity table.</span></span>  
  
2.  <span data-ttu-id="9b2cf-140">在 BusinessMessageJournal 活動資料表的 ContainerActivityID 欄位中搜尋 ActivityID 值。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-140">Search for the ActivityID value in the ContainerActivityID field of the BusinessMessageJournal activity table.</span></span>  
  
3.  <span data-ttu-id="9b2cf-141">在 ContainerActivityID 識別的記錄中，查閱與批次相關聯的 MessageTrackingID 欄位值。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-141">In the record identified by the ContainerActivityID, look up the value of the MessageTrackingID field, which is associated with the batch.</span></span>  
  
4.  <span data-ttu-id="9b2cf-142">使用與 BusinessMessageJournal 活動資料表中批次相關聯的 MessageTrackingID 欄位值，在 BusinessMessageJournal 活動資料表中其他記錄的 MessageTrackingID 欄位中搜尋相同的值。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-142">Using the value of the MessageTrackingID field associated with the batch in the BusinessMessageJournal activity table, search for the same value in the MessageTrackingID field of other records in the BusinessMessageJournal activity table.</span></span> <span data-ttu-id="9b2cf-143">找到的所有記錄都會與批次中的交易集相關，如同「批次處理協調流程」所記錄。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-143">Any records found are associated with transaction sets in the batch, as recorded by the Batching Orchestration.</span></span>  
  
5.  <span data-ttu-id="9b2cf-144">在與 BusinessMessageJournal 活動資料表中交易集相關的記錄中，查閱 BTSInterchangeID 欄位的值。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-144">In a record associated with a transaction set in the BusinessMessageJournal activity table, look up the value of the BTSInterchangeID field.</span></span>  
  
6.  <span data-ttu-id="9b2cf-145">您可以使用 BTSInterchangeID 的值，查閱之前在 BusinessMessageJournal 活動資料表中建立的交易集記錄，如自訂管線元件所記錄。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-145">Using the value of the BTSInterchangeID, you can look up a record for the transaction set that was created in the BusinessMessageJournal activity table, as recorded by the custom pipeline component.</span></span> <span data-ttu-id="9b2cf-146">您也可以查閱 TransactionSetActivity 資料表中的交易集記錄。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-146">You can also look up a record for the transaction set in the TransactionSetActivity table.</span></span>  
  
## <a name="querying-businessmessagejournal"></a><span data-ttu-id="9b2cf-147">查詢 BusinessMessageJournal</span><span class="sxs-lookup"><span data-stu-id="9b2cf-147">Querying BusinessMessageJournal</span></span>  
 <span data-ttu-id="9b2cf-148">如果交易集報告已啟用，而且您知道所收到交換的 BTSInterchangeID，則可以使用下列 [SQL 查詢] 找出包含提交至「批次處理協調流程」之交易集的批次 BTSInterchangeID。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-148">If transaction set reporting is enabled, and you know the BTSInterchangeID of the received interchange, you can use the following SQL Query to find out the BTSInterchangeID of the batch that contains the transaction set submitted to the Batching Orchestration.</span></span> <span data-ttu-id="9b2cf-149">您可以使用此程式碼建立自訂應用程式，以檢視批次中的訊息。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-149">With this code, you can create a custom application to gain visibility into the messages in a batch.</span></span>  
  
> [!IMPORTANT]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="9b2cf-150"> EDI 狀態報告和交易集追蹤已啟用協議時，才會建立在 BusinessMessageJournal 活動中的項目。</span><span class="sxs-lookup"><span data-stu-id="9b2cf-150"> will make entries in the BusinessMessageJournal activity only if EDI status reporting and Transaction Set tracking is enabled for the agreement.</span></span>  
  
```  
Select MessageTrackingID  
From BusinessMessageJournal  
Where BTSInterchangeID = <given InterchangeID of the receive interchange>  
  
Select BTSInterchangeID  
From BusinessMessageJournal  
Where MessageTrackingID = <MessageTrackingID from the previous query> and BTSInterchangeID = <given InterchangeID>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b2cf-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b2cf-151">See Also</span></span>  
 <span data-ttu-id="9b2cf-152">[建立用來追蹤 EDI-AS2 訊息的 BAM 活動](../core/bam-activities-created-to-track-edi-as2-messages.md) </span><span class="sxs-lookup"><span data-stu-id="9b2cf-152">[BAM Activities Created to Track EDI-AS2 Messages](../core/bam-activities-created-to-track-edi-as2-messages.md) </span></span>  
 [<span data-ttu-id="9b2cf-153">啟用 EDI 和 AS2 狀態報告</span><span class="sxs-lookup"><span data-stu-id="9b2cf-153">Enabling EDI and AS2 Status Reports</span></span>](../core/enabling-edi-and-as2-status-reports.md)