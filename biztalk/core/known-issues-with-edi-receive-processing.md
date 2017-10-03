---
title: "已知問題的 EDI 接收處理 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbb3fd6a-381b-479e-a9f2-7b6371fac39e
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 75ab2769ab4a6eacf885dbf675a6bd3fda371007
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-edi-receive-processing"></a><span data-ttu-id="7b4b1-102">EDI 接收處理的已知問題</span><span class="sxs-lookup"><span data-stu-id="7b4b1-102">Known Issues with EDI Receive Processing</span></span>
<span data-ttu-id="7b4b1-103">本主題說明 EDI 接收管線中已知的處理問題。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-103">This topic describes known issues with processing in the EDI receive pipeline.</span></span>  
  
## <a name="receive-side-processing-of-trailing-separators-fails"></a><span data-ttu-id="7b4b1-104">接收端處理尾端分隔符號失敗</span><span class="sxs-lookup"><span data-stu-id="7b4b1-104">Receive-Side Processing of Trailing Separators Fails</span></span>  
 <span data-ttu-id="7b4b1-105">**徵兆**</span><span class="sxs-lookup"><span data-stu-id="7b4b1-105">**Symptom**</span></span>  
  
 <span data-ttu-id="7b4b1-106">具有尾端分隔符號的交易集會失敗，並針對 X12 編碼訊息會顯示錯誤碼 AK403= 6，針對 EDIFACT 編碼訊息則會顯示錯誤碼 UCM3=4/UCD1=45。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-106">A transaction set with a trailing separator fails with error code AK403= 6 for an X12-encoded message or error codes UCM3=4/UCD1=45 for an EDIFACT-encoded message.</span></span>  
  
 <span data-ttu-id="7b4b1-107">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="7b4b1-107">**Possible Cause**</span></span>  
  
 <span data-ttu-id="7b4b1-108">尾端分隔符號的處理功能未啟用。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-108">Processing of trailing separators is not enabled.</span></span>  
  
 <span data-ttu-id="7b4b1-109">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="7b4b1-109">**Resolution**</span></span>  
  
 <span data-ttu-id="7b4b1-110">開啟傳送訊息之合作對象的 [EDI 屬性]。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-110">Open the EDI Properties for the party that sent the message.</span></span> <span data-ttu-id="7b4b1-111">在 [EDI 屬性] 對話方塊的 [驗證和通知產生] 頁面中 (針對 X12 或 EDIFACT)，選取 [允許尾端分隔符號]。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-111">In the Validation and ACK Generation page of the EDI Properties dialog box (for either X12 or EDIFACT), select "Allow trailing delimiter/separators".</span></span> <span data-ttu-id="7b4b1-112">按一下這個核取方塊之後，您可以再按一下 [針對尾端分隔符號建立空的 XML 標記]，指定針對中繼 XML 內的尾端分隔符號建立空的 XML 標記。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-112">After clicking this checkbox, you can specify that empty XML tags are created for trailing separators in the intermediate XML by clicking "Create empty XML tags for trailing separators".</span></span>  
  
## <a name="contrl-ack-is-enabled-but-not-generated"></a><span data-ttu-id="7b4b1-113">CONTRL 通知已啟用，但無法產生</span><span class="sxs-lookup"><span data-stu-id="7b4b1-113">CONTRL ACK is enabled, but not generated</span></span>  
 <span data-ttu-id="7b4b1-114">**徵兆**</span><span class="sxs-lookup"><span data-stu-id="7b4b1-114">**Symptom**</span></span>  
  
 <span data-ttu-id="7b4b1-115">已核取傳送方合作對象的 [驗證和通知產生] 中的 [產生功能通知] 核取方塊，但 EDI 接收管線未產生 CONTRL 通知。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-115">The Generate Functional ACK checkbox in the Validation and ACK Generation for the sending party is checked, but the EDI receive pipeline has not generated a CONTRL acknowledgment.</span></span>  
  
 <span data-ttu-id="7b4b1-116">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="7b4b1-116">**Possible Cause**</span></span>  
  
 <span data-ttu-id="7b4b1-117">CONTRL 訊息包含數個必須從交換複製過來的必要資料元素。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-117">The CONTRL message contains several mandatory data elements that must be copied from the interchange.</span></span> <span data-ttu-id="7b4b1-118">如果交換中的資料元素遺失或語法無效，則接收管線無法產生語法有效的 CONTRL 訊息。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-118">If the data element in the interchange is missing or is syntactically invalid, the receive pipeline cannot generate a syntactically valid CONTRL message.</span></span>  
  
 <span data-ttu-id="7b4b1-119">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="7b4b1-119">**Resolution**</span></span>  
  
 <span data-ttu-id="7b4b1-120">以 CONTRL 通知以外的其他方式報告錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-120">Report the error condition by some other means than a CONTRL acknowledgment.</span></span>  
  
## <a name="there-was-a-failure-executing-the-receive-pipeline-error-message"></a><span data-ttu-id="7b4b1-121">「 沒有執行接收管線失敗 」</span><span class="sxs-lookup"><span data-stu-id="7b4b1-121">"There Was a Failure Executing the Receive Pipeline…"</span></span> <span data-ttu-id="7b4b1-122">錯誤訊息</span><span class="sxs-lookup"><span data-stu-id="7b4b1-122">Error Message</span></span>  
 <span data-ttu-id="7b4b1-123">**徵兆**</span><span class="sxs-lookup"><span data-stu-id="7b4b1-123">**Symptom**</span></span>  
  
 <span data-ttu-id="7b4b1-124">嘗試執行 AS2 接收管線會產生 80040154 錯誤。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-124">Attempting to run an AS2 receive pipeline results in an 80040154 error.</span></span>  
  
 <span data-ttu-id="7b4b1-125">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="7b4b1-125">**Possible Cause**</span></span>  
  
 <span data-ttu-id="7b4b1-126">64 位元主控件執行個體不支援管線。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-126">Pipelines are not supported on 64-bit host instances.</span></span>  
  
 <span data-ttu-id="7b4b1-127">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="7b4b1-127">**Resolution**</span></span>  
  
 <span data-ttu-id="7b4b1-128">請將管線與 32 位元主控件產生關聯。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-128">Associate the pipeline with a 32-bit host.</span></span>  
  
## <a name="an-x12-encoded-message-is-suspended-if-port-based-authentication-is-enabled-and-biztalk-server-does-not-have-access-to-the-authorization-and-security-information"></a><span data-ttu-id="7b4b1-129">若以連接埠為基礎的驗證已啟用，且 BizTalk Server 無法存取授權和安全性資訊，X12 編碼訊息會遭擱置</span><span class="sxs-lookup"><span data-stu-id="7b4b1-129">An X12-Encoded Message Is Suspended If Port-Based Authentication Is Enabled and BizTalk Server Does Not Have Access to the Authorization and Security Information</span></span>  
 <span data-ttu-id="7b4b1-130">**徵兆**</span><span class="sxs-lookup"><span data-stu-id="7b4b1-130">**Symptom**</span></span>  
  
 <span data-ttu-id="7b4b1-131">已透過接收埠 (已啟用驗證) 接收訊息，卻無法判斷傳送訊息的合作對象時，BizTalk Server 會擱置該訊息。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-131">When a message is received over a receive port for which authentication is enabled, and the party that sent the message cannot be determined, BizTalk Server will suspend the message.</span></span>  
  
 <span data-ttu-id="7b4b1-132">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="7b4b1-132">**Possible Cause**</span></span>  
  
 <span data-ttu-id="7b4b1-133">若接收埠已啟用驗證 (已清除接收埠的 [沒有驗證] 屬性)，則 BizTalk Server 需要 "ISA1-2" (授權辨識符號和資訊) 和 "ISA3-4" (安全性辨識符號和資訊) 屬性的設定，才能處理交換。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-133">If authentication is enabled for a receive port (the "No Authentication" property for the receive port is cleared), BizTalk Server requires settings for the "ISA1-2 (Authorization qualifier and information)" and "ISA3-4 (Security qualifier and information)" properties in order to process the interchange.</span></span> <span data-ttu-id="7b4b1-134">合作對象的這些屬性，已經在 [合作對象做為交換傳送者] 的 [X12 交換處理屬性] 頁面中設定。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-134">These properties are set for a party in the X12 Interchange Processing Properties page for the party as an interchange sender.</span></span> <span data-ttu-id="7b4b1-135">若 BizTalk Server 無法判斷這些屬性的值，就會擱置該訊息。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-135">If BizTalk Server cannot determine the values of these properties, it will suspend the message.</span></span>  
  
 <span data-ttu-id="7b4b1-136">發生的情形有兩種。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-136">This can occur in two ways.</span></span> <span data-ttu-id="7b4b1-137">其一，若 BizTalk Server 無法判斷傳送訊息的合作對象，就會使用 EDI 全域屬性，且無法存取授權和安全性設定，</span><span class="sxs-lookup"><span data-stu-id="7b4b1-137">In the first case, if BizTalk Server cannot determine the party that sent the message, it will use the EDI global properties and will not have access to the authorization and security settings.</span></span> <span data-ttu-id="7b4b1-138">因此就會擱置該訊息。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-138">As a result, it will suspend the message.</span></span> <span data-ttu-id="7b4b1-139">其二，若 BizTalk Server 可判斷合作對象，但該合作對象的 ISA1-2 和 ISA3-4 屬性並未設定，BizTalk Server 便無法存取授權和安全性資訊，因此會擱置該訊息。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-139">In the second case, if BizTalk Server determines the party, but the ISA1-2 and ISA3-4 properties for the party are not configured, BizTalk Server will again not have access to authorization and security information and will suspend the message.</span></span>  
  
 <span data-ttu-id="7b4b1-140">**解決方式**</span><span class="sxs-lookup"><span data-stu-id="7b4b1-140">**Resolution**</span></span>  
  
 <span data-ttu-id="7b4b1-141">確保訊息的傳送合作對象一定要可辨識，且合作對象協議內務必定義 ISA1-2 和 ISA3-4 屬性。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-141">Make sure that the sending party for the message can be identified and that the ISA1-2 and ISA3-4 properties are defined in the party agreement.</span></span>  
  
## <a name="incorrect-se01-in-a-split-hipaa-subdocument"></a><span data-ttu-id="7b4b1-142">分割的 HIPAA 子文件中有不正確的 SE01</span><span class="sxs-lookup"><span data-stu-id="7b4b1-142">Incorrect SE01 in a split HIPAA subdocument</span></span>  
 <span data-ttu-id="7b4b1-143">**徵兆**</span><span class="sxs-lookup"><span data-stu-id="7b4b1-143">**Symptom**</span></span>  
  
 <span data-ttu-id="7b4b1-144">交易集結尾 (SE01 欄位) 會提供資料區段 (包括 X12/HIPAA 文件的標頭和結尾區段) 的計數。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-144">The transaction set trailer (SE01 field) provides a count of the data segments, including the header and trailer segments of an X12/HIPAA document.</span></span> <span data-ttu-id="7b4b1-145">然而對於分割的 HIPAA 子文件，EDI 接收管線會套用和原始文件相同的 SE01 值，而非重新計算。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-145">However, for a split HIPAA sub document, the EDI receive pipeline applies the same SE01 value as the original document, instead of re-computing it.</span></span>  
  
 <span data-ttu-id="7b4b1-146">**可能的原因**</span><span class="sxs-lookup"><span data-stu-id="7b4b1-146">**Cause**</span></span>  
  
 <span data-ttu-id="7b4b1-147">EDI 接收管線會將原始 HIPAA 文件中的 SE01 值複製到分割的子文件中。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-147">The EDI receive pipeline copies the value of SE01 from the original HIPAA document to a split sub document.</span></span>  
  
## <a name="error-message-for-duplicate-unb5-or-unh1-is-not-descriptive"></a><span data-ttu-id="7b4b1-148">重複 UNB5 或 UNH1 的錯誤訊息不具描述性</span><span class="sxs-lookup"><span data-stu-id="7b4b1-148">Error Message for Duplicate UNB5 or UNH1 Is Not Descriptive</span></span>  
 <span data-ttu-id="7b4b1-149">如果 BizTalk Server 收到的訊息內含重複 UNB5 (交換控制編號) 或 UNH1 (交易集參考編號)，它傳送的錯誤碼和描述不會清楚指出問題本質。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-149">If BizTalk Server receives a message that has a duplicate UNB5 (interchange control number) or UNH1 (transaction set reference number), the error code and description that it posts will not clearly indicate the nature of the problem.</span></span>  
  
## <a name="biztalk-server-will-suspend-a-very-large-interchange-if-it-runs-out-of-memory"></a><span data-ttu-id="7b4b1-150">如果記憶體不足，BizTalk Server 會擱置非常大的交換</span><span class="sxs-lookup"><span data-stu-id="7b4b1-150">BizTalk Server Will Suspend a Very Large Interchange If It Runs Out of Memory</span></span>  
 <span data-ttu-id="7b4b1-151">BizTalk Server 在剖析非常大的交換時，可能會耗盡記憶體。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-151">BizTalk Server may run out of memory when it parses a very large interchange.</span></span> <span data-ttu-id="7b4b1-152">因此，它會傳送錯誤並擱置交換。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-152">If it does, it will post an error and suspend the interchange.</span></span> <span data-ttu-id="7b4b1-153">在 [群組中樞] 頁面中，您將無法檢視此已擱置、非常大之交換的所有內容。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-153">In the Group Hub page, you will not be able to see all of the contents of a very large interchange that has been suspended.</span></span> <span data-ttu-id="7b4b1-154">您將能夠看到訊息的初始部分，但 BizTalk Server 會受限於它可以顯示的已擱置交換的資料量。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-154">You will be able to see the initial part of the message, but BizTalk Server is limited in the amount of data from a suspended interchange that it can display.</span></span>  
  
## <a name="korean-characters-added-to-an-enumeration-in-a-kedifact-schema-must-be-in-unicode"></a><span data-ttu-id="7b4b1-155">加入 KEDIFACT 結構描述中之列舉的韓文字元必須是 UNICODE 格式</span><span class="sxs-lookup"><span data-stu-id="7b4b1-155">Korean Characters Added to an Enumeration in a KEDIFACT Schema Must Be in UNICODE</span></span>  
 <span data-ttu-id="7b4b1-156">當 BizTalk Server 接收內含韓文字元的 KEDIFACT 編碼交換時，它會使用 UNB2 欄位中的字碼頁/字元集值來處理交換。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-156">When BizTalk Server receives a KEDIFACT-encoded interchange with Korean characters, it will use the code page/character set value in the UNB2 field to process the interchange.</span></span> <span data-ttu-id="7b4b1-157">不過，如果您將具有 ID 資料類型的韓文字元加入列舉以修改 KEDIFACT 結構描述，則必須以 UTF-16 UNICODE 格式加入此值，如結構描述頂端所指定。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-157">However, if you modify a KEDIFACT schema by adding a Korean character with an ID data type to an enumeration, you must add the value in UTF-16 UNICODE, as specified at the top of the schema.</span></span>  
  
## <a name="executing-an-edi-receive-pipeline-from-within-an-orchestration-is-not-supported"></a><span data-ttu-id="7b4b1-158">不支援從協調流程內執行 EDI 接收管線</span><span class="sxs-lookup"><span data-stu-id="7b4b1-158">Executing an EDI Receive Pipeline from within an Orchestration Is Not Supported</span></span>  
 <span data-ttu-id="7b4b1-159">在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您通常可以執行的協調流程中接收 「 運算式 」 圖形內的管線。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-159">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can typically execute receive pipelines within an Expression shape in an orchestration.</span></span> <span data-ttu-id="7b4b1-160">這個功能尚未針對 EDIReceive 管線或 AS2EdiReceive 管線進行測試，因此不受支援。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-160">This functionality has not been tested for the EDIReceive pipeline or the AS2EdiReceive pipeline, so is not supported.</span></span>  
  
## <a name="biztalk-edi-application-must-not-be-modified"></a><span data-ttu-id="7b4b1-161">不得修改 BizTalk EDI 應用程式</span><span class="sxs-lookup"><span data-stu-id="7b4b1-161">BizTalk EDI Application Must Not Be Modified</span></span>  
 <span data-ttu-id="7b4b1-162">不得修改或刪除 BizTalk EDI 應用程式內的成品。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-162">Artifacts in the BizTalk EDI Application must not be modified or deleted.</span></span> <span data-ttu-id="7b4b1-163">應用程式一經修改就無法還原，取消設定和重新設定 EDI 與 AS2 的功能也不行。</span><span class="sxs-lookup"><span data-stu-id="7b4b1-163">If this application is modified, there is no way for you to revert to the original application by unconfiguring and reconfiguring the EDI and AS2 features.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b4b1-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b4b1-164">See Also</span></span>  
 <span data-ttu-id="7b4b1-165">[EDI 處理的已知的問題](../core/known-issues-with-edi-processing.md) </span><span class="sxs-lookup"><span data-stu-id="7b4b1-165">[Known Issues with EDI Processing](../core/known-issues-with-edi-processing.md) </span></span>  
 <span data-ttu-id="7b4b1-166">[BizTalk Server 如何接收 EDI 訊息](../core/how-biztalk-server-receives-edi-messages.md) </span><span class="sxs-lookup"><span data-stu-id="7b4b1-166">[How BizTalk Server Receives EDI Messages](../core/how-biztalk-server-receives-edi-messages.md) </span></span>  
 [<span data-ttu-id="7b4b1-167">逐步解說 (X12)： 接收 EDI 交換並傳回通知</span><span class="sxs-lookup"><span data-stu-id="7b4b1-167">Walkthrough (X12): Receiving EDI Interchanges and Sending Back an Acknowledgement</span></span>](../core/walkthrough-x12--receive-edi-interchanges-and-send-back-an-acknowledgement.md)