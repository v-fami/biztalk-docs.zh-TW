---
title: EDI 批次處理的已知問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 510ac82b-8a02-4135-87b7-0a5f288f5317
caps.latest.revision: 38
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c33be4da2db28fb38c3f81d3d1aaa5316a0a16a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997167"
---
# <a name="known-issues-with-edi-batching"></a><span data-ttu-id="1bc3b-102">EDI 批次處理的已知問題</span><span class="sxs-lookup"><span data-stu-id="1bc3b-102">Known Issues with EDI Batching</span></span>
<span data-ttu-id="1bc3b-103">本主題說明中批次處理的已知的問題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-103">This topic describes known issues with batching in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="subdocument-splitting-was-not-performed-even-though-the-subdocument-annotation-was-set-to-yes"></a><span data-ttu-id="1bc3b-104">子文件分割並未執行，即使子文件註解設定為 [是]</span><span class="sxs-lookup"><span data-stu-id="1bc3b-104">Subdocument Splitting Was Not Performed Even Though the Subdocument Annotation Was Set to Yes</span></span>  
 <span data-ttu-id="1bc3b-105">**徵兆**</span><span class="sxs-lookup"><span data-stu-id="1bc3b-105">**Symptom**</span></span>  
  
 <span data-ttu-id="1bc3b-106">即使該交換之 HIPAA 結構描述的 subdocument_creation_break 註解設為 [是]。 未 HIPAA 交換分割成子文件</span><span class="sxs-lookup"><span data-stu-id="1bc3b-106">A HIPAA interchange was not split into subdocuments even though the subdocument_creation_break annotation within the HIPAA schema for that interchange was set to "Yes."</span></span>  
  
 <span data-ttu-id="1bc3b-107">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="1bc3b-107">**Possible Cause**</span></span>  
  
- <span data-ttu-id="1bc3b-108">輸入的批次處理選項傳送合作對象已設定為 「 保留交換 」。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-108">The Inbound batch processing option for the sending party was set to "Preserve Interchange."</span></span> <span data-ttu-id="1bc3b-109">HIPAA 文件就不會分割成子文件的情況下，即使 HIPAA 結構描述 subdocument_creation_break 註解設為 [是]。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-109">A HIPAA document will not be split into subdocuments if this is the case, even though the subdocument_creation_break annotation within the HIPAA schema is set to "Yes."</span></span>  
  
- <span data-ttu-id="1bc3b-110">Subdocument_break 註釋已設定為 [是]，但 subdocument_creation_break 註解未設定為 [是]。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-110">The subdocument_break annotation was set to “Yes”, but the subdocument_creation_break annotation was not set to “Yes”.</span></span>  
  
  <span data-ttu-id="1bc3b-111">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="1bc3b-111">**Resolution**</span></span>  
  
- <span data-ttu-id="1bc3b-112">在 [**驗證和通知的產生設定**頁面**EDI 屬性**傳送合作對象] 對話方塊中設定**輸入批次處理**選項屬性任一**將交換分割為交易集-交易集發生錯誤時暫停**或是**將交換分割為交易集-暫停發生錯誤的交換**。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-112">In the **Validation and ACK Generation Settings** page of the **EDI Properties** dialog box for the sending party, set the **Inbound batch processing** option property to either **Split Interchange as Transaction Sets – suspend Transaction Sets on Error** or **Split Interchange as Transaction Sets – suspend Interchange on Error**.</span></span>  
  
- <span data-ttu-id="1bc3b-113">除非 subdocument_creation_break 註解設為 [是]，否則 HIPAA 文件不會分割成子文件。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-113">A HIPAA document will not be split into subdocuments unless the subdocument_creation_break annotation is set to “Yes.”</span></span>  
  
## <a name="validation-of-a-batch-may-fail-if-batch-configuration-settings-are-changed-while-the-batch-orchestration-is-activated"></a><span data-ttu-id="1bc3b-114">如果在批次協調流程啟動時變更批次組態設定，驗證批次可能會失敗</span><span class="sxs-lookup"><span data-stu-id="1bc3b-114">Validation of a Batch May Fail if Batch Configuration Settings Are Changed While the Batch Orchestration Is Activated</span></span>  
 <span data-ttu-id="1bc3b-115">當批次處理協調流程正在處理批次時，如果變更批次組態設定，該批次將不會套用新的組態設定。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-115">If you change batch configuration settings while the batching orchestration is processing a batch, the new configuration settings will not be picked up for that batch.</span></span> <span data-ttu-id="1bc3b-116">這可能會在傳送管線中產生驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-116">This can result in validation errors in the send pipeline.</span></span>  
  
 <span data-ttu-id="1bc3b-117">這些設定位於 [EDI 屬性] 對話方塊 [批次] 頁面。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-117">These settings are in the Batches page of the EDI Properties dialog box.</span></span>  
  
 <span data-ttu-id="1bc3b-118">若要解決這個問題，請重新啟動與批次處理協調流程相關的主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-118">To resolve this issue, restart the host instance(s) associated with the batching orchestration(s).</span></span> <span data-ttu-id="1bc3b-119">這會讓批次組態設定的變更立即生效。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-119">This will cause the change to the batch configuration settings to take place immediately.</span></span>  
  
## <a name="the-batchcontrolmessagerecvloc-receive-location-can-only-run-on-a-32-bit-computer-or-in-wow-on-a-64-bit-computer"></a><span data-ttu-id="1bc3b-120">BatchControlMessageRecvLoc 接收位置只能在 32 位元電腦或 64 位元電腦上的 WOW 執行</span><span class="sxs-lookup"><span data-stu-id="1bc3b-120">The BatchControlMessageRecvLoc Receive Location Can Only Run on a 32-Bit Computer or in WOW on a 64-Bit Computer</span></span>  
 <span data-ttu-id="1bc3b-121">SQL 配接器只能在 32 位元電腦或 64 位元電腦的 WOW64 模擬器下運作。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-121">SQL adapters only work on 32-bit computers or when running under the WOW64 emulator on 64-bit computers.</span></span> <span data-ttu-id="1bc3b-122">因此，由安裝程式安裝並使用 SQL 配接器的 BatchControlMessageRecvLoc 接收位置也只能在 32 位元電腦或 64 位元電腦的 WOW 下運作。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-122">As a result, the BatchControlMessageRecvLoc receive location, which is installed by the setup program and uses the SQL adapter, will only work on a 32-bit computer or when running under WOW on a 64-bit computer.</span></span> <span data-ttu-id="1bc3b-123">批次處理需要使用此接收位置。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-123">This receive location is required for batch processing.</span></span>  
  
 <span data-ttu-id="1bc3b-124">在 64 位元電腦上的 WOW 下執行 BatchControlMessageRecvLoc 接收位置時，請在不同的主機中執行批次處理協調流程。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-124">When running the BatchControlMessageRecvLoc receive location under WOW on a 64-bit computer, you should run the batching orchestrations in a different host.</span></span> <span data-ttu-id="1bc3b-125">如果與接收位置在同一個主機上執行，則批次處理協調流程也會在 WOW 下執行，那麼就失去了在 64 位元電腦上執行的優勢。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-125">If they are run on the same host as the receive location, the batching orchestrations would also run under WOW, and you would lose the advantages of running on a 64-bit computer.</span></span>  
  
## <a name="a-batch-can-be-picked-up-by-an-unintended-send-port"></a><span data-ttu-id="1bc3b-126">批次可能會由非指定的傳送埠取用</span><span class="sxs-lookup"><span data-stu-id="1bc3b-126">A Batch Can Be Picked Up By an Unintended Send Port</span></span>  
 <span data-ttu-id="1bc3b-127">當批次處理協調流程發佈交換時，會升級兩個屬性： ToBeBatched = False 和 DestinationPartyName = \< *PartyName*\>。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-127">When the batching orchestration publishes an interchange, it promotes two properties: ToBeBatched = False and DestinationPartyName = \<*PartyName*\>.</span></span> <span data-ttu-id="1bc3b-128">訂閱其中一個屬性或兩個屬性都訂閱的傳送埠可以取用這些批次交換。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-128">A send port subscribing to either or both of these properties can pick up these batched interchanges.</span></span> <span data-ttu-id="1bc3b-129">請確定已設定傳送埠的篩選條件，好讓傳送埠選取應該取用的批次交換。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-129">Make sure that a send port's filters are configured such that the send port picks up those batched interchanges that it is intended to pick up.</span></span>  
  
## <a name="a-batch-element-count-greater-than-the-required-number-of-transaction-sets-for-a-batch-may-not-prompt-batch-release"></a><span data-ttu-id="1bc3b-130">雖然批次項目計數大於批次所需的交易集數，仍可能不會提示批次釋放</span><span class="sxs-lookup"><span data-stu-id="1bc3b-130">A Batch Element Count Greater Than the Required Number of Transaction Sets for a Batch May Not Prompt Batch Release</span></span>  
 <span data-ttu-id="1bc3b-131">如果批次釋放準則是根據群組或交換的交易集數目為基礎，即使批次項目計數大於釋放批次所需的交易集數目，仍可能不會釋放批次。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-131">If the batch release criteria is based upon the number of transaction sets per group or interchange, a batch may not be released even though the batch element count is greater than the number of transaction sets required for a batch to be released.</span></span> <span data-ttu-id="1bc3b-132">如果您啟用通知，並設定批次篩選條件準則將這些通知加入批次，就可能會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-132">This can happen if you enable acknowledgments, and set the batch filter criteria to add those acknowledgments to the batch.</span></span> <span data-ttu-id="1bc3b-133">在這種情況下，群組 (或交換) 中的批次項目數目將大於群組 (或交換) 的交易集數目。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-133">In this instance, the number of batch elements in the group (or interchange) will be greater than the number of transaction sets per group (or interchange).</span></span> <span data-ttu-id="1bc3b-134">這時，如果群組 (或交換) 的交易集數目小於批次釋放所需的數目，但同時批次項目數目又可能大於批次釋放所需的交易集數目，那麼將不會釋放批次。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-134">In that instance, a batch will not be released if the number of transaction sets per group (or interchange) is smaller than the number required for batch release, but at the same time the number of batch elements could be greater than the number of transaction sets required for batch release.</span></span>  
  
## <a name="no-batch-elements-were-saved-when-start-was-clicked"></a><span data-ttu-id="1bc3b-135">按一下啟動時沒有儲存任何批次項目</span><span class="sxs-lookup"><span data-stu-id="1bc3b-135">No Batch Elements Were Saved When Start Was Clicked</span></span>  
 <span data-ttu-id="1bc3b-136">**徵兆**</span><span class="sxs-lookup"><span data-stu-id="1bc3b-136">**Symptom**</span></span>  
  
 <span data-ttu-id="1bc3b-137">當**啟動**按一下合作對象的批次 頁面中針對批次收集任何訊息。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-137">When **Start** was clicked in the Batches page for a party, no messages were collected for the batch.</span></span>  
  
 <span data-ttu-id="1bc3b-138">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="1bc3b-138">**Possible Cause**</span></span>  
  
 <span data-ttu-id="1bc3b-139">日期時間**開始**已按下早於輸入的日期時間**啟用**一節。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-139">The datetime at which **Start** was clicked was earlier than the datetime entered in the **Activation** section.</span></span> <span data-ttu-id="1bc3b-140">如此一來，協調流程執行個體已啟用，但針對批次收集任何訊息。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-140">As a result, the orchestration instance was activated, but no messages were collected for the batch.</span></span> <span data-ttu-id="1bc3b-141">如需詳細資訊，請參閱 <<c0> [ 設定外寄批次](../core/configuring-an-outgoing-batch.md)。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-141">For more information, see [Configuring an Outgoing Batch](../core/configuring-an-outgoing-batch.md).</span></span>  
  
 <span data-ttu-id="1bc3b-142">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="1bc3b-142">**Resolution**</span></span>  
  
 <span data-ttu-id="1bc3b-143">按一下 **停止**發生此問題的批次組態的批次頁面中。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-143">Click **Stop** in the Batches page for the batch configuration experiencing this problem.</span></span> <span data-ttu-id="1bc3b-144">設定**Activation**設為**立即開始**或輸入日期時間早於目前的時間，然後按一下**啟動**。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-144">Set the **Activation** to either **Start immediately** or enter a datetime earlier than the current time, and then click **Start**.</span></span> <span data-ttu-id="1bc3b-145">提示您時重設**開始**日期時間為目前的時間中，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-145">When you are prompted to reset the **Start** datetime to the current time, click **OK**.</span></span> <span data-ttu-id="1bc3b-146">BizTalk Server 這時便會開始收集批次的訊息。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-146">BizTalk Server will start to collect messages for a batch at that point.</span></span>  
  
## <a name="the-number-of-bytes-in-an-edifact-batch-may-depend-upon-the-character-set-used"></a><span data-ttu-id="1bc3b-147">EDIFACT 批次中的位元組數目可能會視使用的字元集而定</span><span class="sxs-lookup"><span data-stu-id="1bc3b-147">The Number of Bytes in an EDIFACT Batch May Depend Upon the Character Set Used</span></span>  
 <span data-ttu-id="1bc3b-148">某些 EDIFACT 字元集中的字元可能是雙位元組字元，而其他 EDIFACT 字元集中的字元則可能是單一位元組字元。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-148">Characters in some EDIFACT character sets may be double-byte characters, whereas in other EDIFACT character sets they may be single-byte characters.</span></span> <span data-ttu-id="1bc3b-149">因此，當您根據交換中的字元數來設定批次的釋放準則時，交換中的位元組數可能會根據使用的字元集而有所不同。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-149">Because of this, when you set the release criteria for batches based upon the number of characters in the interchange, the number of bytes in the interchange may differ depending on the character set used.</span></span>  
  
## <a name="the-characters--and--must-be-represented-in-their-encoded-form-in-the-envelope-of-a-batch"></a><span data-ttu-id="1bc3b-150">字元"<"和"&"必須以批次的信封中的其編碼格式表示</span><span class="sxs-lookup"><span data-stu-id="1bc3b-150">The Characters "<" and "&" Must be Represented in Their Encoded Form in the Envelope of a Batch</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="1bc3b-151"> 不支援下列字元常值格式建立批次 EDI 交換的信封欄位時:"<"和"&"。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-151"> does not support the following characters in their literal form when creating the envelope fields of a batched EDI interchange: "<" and "&".</span></span>  
  
 <span data-ttu-id="1bc3b-152">如果使用 EdiSend 管線序列化交換，則若在外寄批次交換的信封欄位中使用其中任一字元的常值，將會導致訊息遭擱置。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-152">Using either of these characters literally in the envelope fields of an outgoing batched interchange will result in a suspended message if the EdiSend pipeline is used to serialize the interchange.</span></span>  
  
 <span data-ttu-id="1bc3b-153">如果需要在批次的信封欄位中使用上述其中一個字元，當您在「BizTalk 系統管理員」中設定信封欄位時，可以使用下表中經過適當編碼的值：</span><span class="sxs-lookup"><span data-stu-id="1bc3b-153">If you need to use one of these characters in an envelope field of a batch, you can use the appropriate encoded value in the following table when you configure the envelope field in the BizTalk Administrator:</span></span>  
  
|<span data-ttu-id="1bc3b-154">字元</span><span class="sxs-lookup"><span data-stu-id="1bc3b-154">Character</span></span>|<span data-ttu-id="1bc3b-155">編碼方式</span><span class="sxs-lookup"><span data-stu-id="1bc3b-155">Encoding</span></span>|  
|---------------|--------------|  
|<|&lt;|  
|&|&amp;|  
  
 <span data-ttu-id="1bc3b-156">當您使用其中一種編碼的形式時，將編碼格式中的每個字元將會被視為個別的字元時 BizTalk Server 會驗證它的長度限制在夥伴協議管理員 (PAM) 畫面中，BizTalk Server 中的欄位管理主控台。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-156">When you use one of these encoded forms, each character in the encoded form will be counted as an individual character when BizTalk Server validates the field for its length restriction in the Partner Agreement Manager (PAM) screens in the BizTalk Server Administration console.</span></span> <span data-ttu-id="1bc3b-157">比方說，即使編碼"&lt;"代表單一字元"\<"在批次 EDI 交換，BizTalk Server 會視為四個字元時驗證是否符合特定的欄位長度限制.</span><span class="sxs-lookup"><span data-stu-id="1bc3b-157">For example, even though the encoding "&lt;" would represent a single character "\<" in the batched EDI interchange, BizTalk Server would count this as four characters when validating against the length restriction of the particular field.</span></span> <span data-ttu-id="1bc3b-158">只有 PAM 才會發生此問題，「EDI 組合器」則無此問題。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-158">This is an issue for PAM only, not for the EDI Assembler.</span></span>  
  
## <a name="an-exeption-occurs-during-the-execution-of-the-upgrade-batch-orchestration"></a><span data-ttu-id="1bc3b-159">在執行升級批次協調流程期間發生的例外狀況</span><span class="sxs-lookup"><span data-stu-id="1bc3b-159">An Exeption Occurs During the Execution of the Upgrade Batch Orchestration</span></span>  
 <span data-ttu-id="1bc3b-160">**徵兆**</span><span class="sxs-lookup"><span data-stu-id="1bc3b-160">**Symptom**</span></span>  
  
 <span data-ttu-id="1bc3b-161">使用自訂管線元件時，設定 EDI。內送文件上的 DestinationPartyId 屬性，您可能會收到升級批次協調流程執行期間發生例外狀況，在應用程式事件記錄檔指出錯誤。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-161">When using a custom pipeline component that sets the EDI.DestinationPartyId property on incoming documents, you may receive an error in the Application event log stating that an exception has occurred during the execution of the upgrade batch orchestration.</span></span>  
  
 <span data-ttu-id="1bc3b-162">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="1bc3b-162">**Possible Cause**</span></span>  
  
 <span data-ttu-id="1bc3b-163">如果 ErrorMessage =「找不到批次」，此錯誤表示升級批次協調流程無法成功識別內送文件的批次。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-163">If ErrorMessage = “The batch was not found”, this error indicates that the upgrade batch orchestration was not able to successfully identify a batch for the incoming document.</span></span>  
  
 <span data-ttu-id="1bc3b-164">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="1bc3b-164">**Resolution**</span></span>  
  
 <span data-ttu-id="1bc3b-165">升級批次協調流程會使用 EDI。Destinationpartyid 設定為查閱合作對象名稱。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-165">The upgrade batch orchestration uses the EDI.DestinationPartyId to look up the party name.</span></span> <span data-ttu-id="1bc3b-166">接著使用這個合作對象名稱、EDI.EncodingType 與字串 “Default” 建構一個字串，然後尋找具有相符批次名稱的批次組態。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-166">The orchestration then constructs a string using the party name, EDI.EncodingType and the string “Default”, and then looks for a batch configuration with a matching batch name.</span></span> <span data-ttu-id="1bc3b-167">如果不有使用此名稱的任何批次組態，應用程式事件記錄檔會記錄此錯誤，協調流程執行個體被擱置。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-167">If no batch configuration exists with this name, this error is logged to the Application event log and the orchestration instance is suspended.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bc3b-168">例如，如果合作對象名稱為 Contoso，EDI.EncodingType 為 X12，則協調流程會尋找名為 ‘ContosoX12Default’ 的批次。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-168">For example, if the party name is Contoso and the EDI.EncodingType is X12, the orchestration will look for a batch named ‘ContosoX12Default’.</span></span>  
  
 <span data-ttu-id="1bc3b-169">若要解決此問題，請確定批次有會比對升級批次協調流程所建構之字串的名稱。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-169">To resolve this problem, ensure that a batch exists with a name that will match the string constructed by the upgrade batch orchestration.</span></span>  
  
## <a name="messages-marked-with-editobebatched--true-and-edidestinationparties-are-suspended"></a><span data-ttu-id="1bc3b-170">標記為 EDI 訊息。ToBeBatched = True 和 EDI。DestinationParties 會暫停</span><span class="sxs-lookup"><span data-stu-id="1bc3b-170">Messages Marked with EDI.ToBeBatched = True and EDI.DestinationParties are Suspended</span></span>  
 <span data-ttu-id="1bc3b-171">**徵兆**</span><span class="sxs-lookup"><span data-stu-id="1bc3b-171">**Symptoms**</span></span>  
  
 <span data-ttu-id="1bc3b-172">在使用自訂管線元件將設定 EDI 批次處理的訊息。ToBeBatched = True 和 EDI。DestinationParties 清單的合作對象的識別碼，訊息將遭擱置，並指出沒有任何訂閱者的路由失敗。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-172">When using a custom pipeline component to mark messages for batching by setting EDI.ToBeBatched = True and EDI.DestinationParties to a list of party IDs, the message will be suspended with a routing failure stating that there are no subscribers.</span></span>  
  
 <span data-ttu-id="1bc3b-173">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="1bc3b-173">**Possible Cause**</span></span>  
  
 <span data-ttu-id="1bc3b-174">在舊版的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應該處理訊息時，由多個批次組態中，您會設定 EDI。DestinationParties 屬性，以空格分隔合作對象識別碼的清單。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-174">In previous versions of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], when a message should be processed by multiple batch configurations you would set the EDI.DestinationParties property to a space delimited list of party IDs.</span></span> <span data-ttu-id="1bc3b-175">路由協調流程會訂閱具有 EDI.ToBeBatched = True 與 EDI.DestinationParties 屬性的訊息，並使用 EDI.DestinationParties 屬性中包含的合作對象識別碼清單為每個識別碼建立訊息，然後將訊息傳遞給批次處理協調流程。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-175">The routing orchestration is subscribed to messages with the EDI.ToBeBatched = True and EDI.DestinationParties properties, and would use the list of party IDs contained in the EDI.DestinationParties property to create a message for each ID, and pass the messages to the batching orchestration.</span></span>  <span data-ttu-id="1bc3b-176">判斷使用合作對象的批次識別碼使用，因為每個合作對象組態可能有只有一個批次組態。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-176">Determining the batch by using the party ID was used because each party configuration could have only one batch configuration.</span></span>  
  
 <span data-ttu-id="1bc3b-177">在 BizTalk Server 中，每個合作對象可以有多個批次組態，因此不會再使用以判斷要使用的批次組態的合作對象識別碼。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-177">In BizTalk Server, each party can have multiple batch configurations, so it is no longer sufficient to use only the pary ID to determine the batch configuration to use.</span></span>  <span data-ttu-id="1bc3b-178">若要指出多個批次組態必須處理一則訊息，訊息必須 EDI。Batchid 屬性設定為一個空格分隔批次訊息應傳送至的識別碼的清單。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-178">To indicate that a message must be processed by multiple batch configurations, the message must have the EDI.BatchIDs property set to a space delimited list of batch IDs that the message should be sent to.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bc3b-179">當處理訊息標示為只有一個合作對象識別碼使用 EDI。DestinationPartyId 屬性升級批次處理協調流程會處理訊息。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-179">When processing messages marked with only a single party ID using the EDI.DestinationPartyId property, the message will be processed by the upgrade batching orchestration.</span></span> <span data-ttu-id="1bc3b-180">如需詳細資訊，請參閱 <<c0> [ 組合批次 EDI 交換](../core/assembling-a-batched-edi-interchange.md)。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-180">For more information, see [Assembling a Batched EDI Interchange](../core/assembling-a-batched-edi-interchange.md).</span></span>  
  
 <span data-ttu-id="1bc3b-181">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="1bc3b-181">**Resolution**</span></span>  
  
 <span data-ttu-id="1bc3b-182">升級自訂管線元件，以便將 EDI。Batchid 屬性，而不是 EDI。DestinationParties。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-182">Upgrade the custom pipeline component so that it sets the EDI.BatchIDs property instead of EDI.DestinationParties.</span></span>  <span data-ttu-id="1bc3b-183">特定批次的批次識別碼可以找到的 EDI 內容的批次設定 頁面上，針對每個合作對象。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-183">The batch ID for a specific batch can be found on the Batches settings page of EDI properties for each party.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bc3b-184">如果使用 BatchMarker 管線元件來批次處理訊息標記，則不會發生此問題。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-184">This problem does not occur if the BatchMarker pipeline component is used to mark the message for batching.</span></span>  
  
## <a name="batch-filter-refresh-timeout-is-hardcoded-to-fifteen-minutes"></a><span data-ttu-id="1bc3b-185">批次篩選條件重新整理逾時是硬式編碼為 15 分鐘</span><span class="sxs-lookup"><span data-stu-id="1bc3b-185">Batch Filter Refresh Timeout is Hardcoded to Fifteen Minutes</span></span>  
 <span data-ttu-id="1bc3b-186">當修改批次篩選條件準則，需要 15 分鐘的時間所做的變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-186">When modifying the batch filter criteria, it will take 15 minutes before the changes take effect.</span></span> <span data-ttu-id="1bc3b-187">無法修改此重新整理間隔。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-187">This refresh interval cannot be modified.</span></span> <span data-ttu-id="1bc3b-188">若要篩選器會立即生效，請重新啟動 BizTalk Server 主控件程序。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-188">To have the filter take effect immediately, restart the BizTalk Server host process.</span></span>  
  
## <a name="the-routingorchestration-suspends-after-reporting-an-uncaught-exception"></a><span data-ttu-id="1bc3b-189">RoutingOrchestration 暫停之後發生無法攔截的例外狀況</span><span class="sxs-lookup"><span data-stu-id="1bc3b-189">The RoutingOrchestration Suspends After Reporting an Uncaught Exception</span></span>  
 <span data-ttu-id="1bc3b-190">**徵兆**</span><span class="sxs-lookup"><span data-stu-id="1bc3b-190">**Symptoms**</span></span>  
  
 <span data-ttu-id="1bc3b-191">在處理目的地為多個批次組態的文件時，您可能會收到錯誤在應用程式事件記錄檔從 XLANG/s 開始 Microsoft.BizTalk.Edi.RoutingOrchestration.BatchRoutingService 失敗，因為無法攔截例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-191">When processing documents that are destined for multiple batch configurations, you may receive an error in the Application Event Log from XLANG/s starting that the Microsoft.BizTalk.Edi.RoutingOrchestration.BatchRoutingService failed due to an uncaught exception.</span></span>  
  
 <span data-ttu-id="1bc3b-192">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="1bc3b-192">**Possible Cause**</span></span>  
  
 <span data-ttu-id="1bc3b-193">RoutingOrchestration 嘗試傳送訊息至 BatchingOrchestration 和 BatchingOrchestration 執行個體未在啟動時，會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-193">This error can occur when the RoutingOrchestration attempts to send a message to the BatchingOrchestration and the BatchingOrchestration instance is not started.</span></span>  
  
 <span data-ttu-id="1bc3b-194">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="1bc3b-194">**Resolution**</span></span>  
  
 <span data-ttu-id="1bc3b-195">確定 BatchingOrchestration 執行個體正在執行才能提交要批次處理的文件。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-195">Ensure that the BatchingOrchestration instances are running before submitting documents to be batched.</span></span>  
  
## <a name="many-active-batches-may-cause-the-biztalkmsgboxdb-logfile-to-grow-large"></a><span data-ttu-id="1bc3b-196">許多作用中批次可能會導致 BizTalkMsgBoxDb 記錄檔變大</span><span class="sxs-lookup"><span data-stu-id="1bc3b-196">Many Active Batches May Cause the BizTalkMsgBoxDb Logfile to Grow Large</span></span>  
 <span data-ttu-id="1bc3b-197">**徵兆**</span><span class="sxs-lookup"><span data-stu-id="1bc3b-197">**Symptoms**</span></span>  
  
 <span data-ttu-id="1bc3b-198">啟動數個批次之後, 您可能會注意到 BizTalk message box 資料庫 (BizTalkMsgBoxDb) 的交易記錄增長到大型大小。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-198">After starting several batches, you may notice that the transaction log for the BizTalk message box database (BizTalkMsgBoxDb) has grown to a large size.</span></span>  
  
 <span data-ttu-id="1bc3b-199">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="1bc3b-199">**Possible Cause**</span></span>  
  
 <span data-ttu-id="1bc3b-200">如果您有大量的批次釋放準則以啟動會造成批次的版本 （例如，批次釋放每分鐘排定） 之間在短時間內，就會發生此問題。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-200">This problem can occur if you have a large number of batches started with release criteria that causes a short interval between batch releases (for example, a batch that is scheduled to release every minute).</span></span>  
  
 <span data-ttu-id="1bc3b-201">當您啟動批次時，會建立批次處理協調流程執行個體是長時間執行的程序會保存到資料庫之後釋放批次。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-201">The batching orchestration instance that is created when you start a batch is a long running process that persists to the database after releasing a batch.</span></span> <span data-ttu-id="1bc3b-202">協調流程持續發生，每次交易記錄檔將會成長因為交易而產生參與持續性。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-202">Each time the orchestration persists, the transaction log will grow due to the transactions involved in persistence.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1bc3b-203">批次處理協調流程將增加大約 30 kb 交易記錄檔，在保存期間。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-203">The batching orchestration will grow the transaction log by approximately 30kb during persistence.</span></span>  
  
 <span data-ttu-id="1bc3b-204">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="1bc3b-204">**Resolution**</span></span>  
  
 <span data-ttu-id="1bc3b-205">若要解決此問題，請修改釋放準則，以增加批次釋放之間的時間。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-205">To resolve this problem, modify the release criteria to increase the time between batch releases.</span></span> <span data-ttu-id="1bc3b-206">如需詳細資訊，請參閱 <<c0> [ 設定批次處理 (X12)](../core/configuring-batching-x12.md)。</span><span class="sxs-lookup"><span data-stu-id="1bc3b-206">For more information, see [Configuring Batching (X12)](../core/configuring-batching-x12.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bc3b-207">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bc3b-207">See Also</span></span>  
 <span data-ttu-id="1bc3b-208">[設定 EDI 通知](../core/configuring-edi-acknowledgments.md) </span><span class="sxs-lookup"><span data-stu-id="1bc3b-208">[Configuring EDI Acknowledgments](../core/configuring-edi-acknowledgments.md) </span></span>  
 <span data-ttu-id="1bc3b-209">[處理內送的批次](../core/processing-incoming-batches.md) </span><span class="sxs-lookup"><span data-stu-id="1bc3b-209">[Processing Incoming Batches](../core/processing-incoming-batches.md) </span></span>  
 <span data-ttu-id="1bc3b-210">[批次處理外寄 EDI 訊息](../core/batching-outgoing-edi-messages.md) </span><span class="sxs-lookup"><span data-stu-id="1bc3b-210">[Batching Outgoing EDI Messages](../core/batching-outgoing-edi-messages.md) </span></span>  
 [<span data-ttu-id="1bc3b-211">設定 EDI 批次</span><span class="sxs-lookup"><span data-stu-id="1bc3b-211">Configuring EDI Batches</span></span>](../core/configuring-edi-batches.md)