---
title: "MQSeries 內容屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MQXQH_RemoteQName property [MQSeries adapters]
- MQCIH_TaskEndStatus property [MQSeries adapters]
- MQIIH_SecurityScope property [MQSeries adapters]
- MQCIH_AbendCode property [MQSeries adapters]
- filters, MQSeries adapters
- MQCIH_ReturnCode property [MQSeries adapters]
- MQCIH_TransactionId property [MQSeries adapters]
- MQCIH_ReplyToFormat property [MQSeries adapters]
- MQMD_ReplyToQ property [MQSeries adapters]
- MQMD_PutTime property [MQSeries adapters]
- configuring [MQSeries adapters], properties
- MQMD_PutApplName property [MQSeries adapters]
- configuring [MQSeries adapters], filtering
- MQCIH_UOWControl property [MQSeries adapters]
- MQCIH_ErrorOffset property [MQSeries adapters]
- MQMD_Priority property [MQSeries adapters]
- MQMD_MsgSeqNumber property [MQSeries adapters]
- MQMD_Format property [MQSeries adapters]
- MQCIH_ConversationalTask property [MQSeries adapters]
- Message Descriptor table [MQSeries adapters]
- MQMD_Feedback property [MQSeries adapters]
- MQCIH_Authenticator property [MQSeries adapters]
- MQIIH_TranState property [MQSeries adapters]
- MQCIH_AttentionId property [MQSeries adapters]
- MQMD_UserIdentifier property [MQSeries adapters]
- MQCIH_Flags property [MQSeries adapters]
- MQMD_CorrelId property [MQSeries adapters]
- MQIIH_Format property [MQSeries adapters]
- MQMD_Offset property [MQSeries adapters]
- MQMD_BackoutCount property [MQSeries adapters]
- MQMD_Report property [MQSeries adapters]
- MQMD_MsgFlags property [MQSeries adapters]
- MQSeries adapters, filtering
- MQMD_ApplIdentityData property [MQSeries adapters]
- MQIIH_Authenticator property [MQSeries adapters]
- MQIIH_MFSMapName property [MQSeries adapters]
- MQCIH_LinkType property [MQSeries adapters]
- MQMD_Persistence property [MQSeries adapters]
- MQCIH_CursorPosition property [MQSeries adapters]
- MQCIH_Format property [MQSeries adapters]
- MQCIH_Facility property [MQSeries adapters]
- MQCIH_CancelCode property [MQSeries adapters]
- MQMD_PutDate property [MQSeries adapters]
- MQCIH_NextTransactionId property [MQSeries adapters]
- MQIIH_CommitMode property [MQSeries adapters]
- MQIIH_ReplyToFormat property [MQSeries adapters]
- MQCIH_Function property [MQSeries adapters]
- MQMD_ReplyToQMgr property [MQSeries adapters]
- MQCIH_StartCode property [MQSeries adapters]
- MQMD_Expiry property [MQSeries adapters]
- MQMD_PutApplType property [MQSeries adapters]
- MQCIH_FacilityLike property [MQSeries adapters]
- MQIIH_Flags property [MQSeries adapters]
- MQCIH_CompCode property [MQSeries adapters]
- MQSeries adapters, properties
- MQCIH_FacilityKeepTime property [MQSeries adapters]
- MQMD_ApplOriginData property [MQSeries adapters]
- MQCIH_Reason property [MQSeries adapters]
- MQIIH_LTermOverride property [MQSeries adapters]
- MQMD_CodedCharSetId property [MQSeries adapters]
- MQMD_GroupID property [MQSeries adapters]
- MQXQH_RemoteQMgrName property [MQSeries adapters]
- MQMD_MsgType property [MQSeries adapters]
- MQMD_OriginalLength property [MQSeries adapters]
- MQMD_Encoding property [MQSeries adapters]
- MQMD_AccountingToken property [MQSeries adapters]
- MQCIH_OutputDataLength property [MQSeries adapters]
- MQIIH_TranInstanceId property [MQSeries adapters]
- MQCIH_GetWaitInterval property [MQSeries adapters]
- MQCIH_ADSDescriptor property [MQSeries adapters]
- MQMD_MsgId property [MQSeries adapters]
ms.assetid: 1b22b7d7-432b-4ec5-938c-c43077ce3e0f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d27309379fac2c4821251f27fd2aa5a6e9d59418
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="mqseries-context-properties"></a><span data-ttu-id="b29eb-102">MQSeries 內容屬性</span><span class="sxs-lookup"><span data-stu-id="b29eb-102">MQSeries Context Properties</span></span>
<span data-ttu-id="b29eb-103">MQSeries 配接器提供一組 MQSeries 專用的內容屬性，可在應用程式中使用。</span><span class="sxs-lookup"><span data-stu-id="b29eb-103">The MQSeries adapter provides a set of context properties, specific to MQSeries, for use in your applications.</span></span> <span data-ttu-id="b29eb-104">您可以在篩選運算式與協調流程中使用這些屬性。</span><span class="sxs-lookup"><span data-stu-id="b29eb-104">You can use these properties in filter expressions and in your orchestrations.</span></span>  
  
 <span data-ttu-id="b29eb-105">若要指派 MQSeries 內容屬性給要傳送到繫結至 MQSeries 配接器之傳送埠的訊息，請使用訊息設定運算子，然後在 MQSeries 命名空間中指定其中一個可用的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="b29eb-105">To assign MQSeries context properties to a message destined to a send port that is bound to the MQSeries adapter, use the message assignment operator and specify one of the available context properties in the MQSeries namespace.</span></span>  
  
 <span data-ttu-id="b29eb-106">以下是範例設定 MQSeries **MQMD_UserIdentifier**屬性：</span><span class="sxs-lookup"><span data-stu-id="b29eb-106">The following is an example of setting the MQSeries **MQMD_UserIdentifier** property:</span></span>  
  
```  
Message_2(MQSeries.MQMD_UserIdentifier) = "MeMyselfAndI";  
```  
  
 <span data-ttu-id="b29eb-107">您必須從 IBM MQSeries SDK 所含的 C 程式設計語言標頭檔中取得列舉值。</span><span class="sxs-lookup"><span data-stu-id="b29eb-107">You must obtain enumerated values from the C programming language header files included with the IBM MQSeries SDK.</span></span> <span data-ttu-id="b29eb-108">您可以在 Program Files\IBM\WebSphere MQ\Tools\c\include 資料夾中找到這些檔案。</span><span class="sxs-lookup"><span data-stu-id="b29eb-108">You can find these files in the Program Files\IBM\WebSphere MQ\Tools\c\include folder.</span></span> <span data-ttu-id="b29eb-109">這些檔案定義在設定或讀取 MQSeries 內容屬性值時所要使用的值。</span><span class="sxs-lookup"><span data-stu-id="b29eb-109">These files define the values to use when setting or reading MQSeries context property values.</span></span>  
  
 <span data-ttu-id="b29eb-110">十六進位字串值是代表二進位值的字元字串。</span><span class="sxs-lookup"><span data-stu-id="b29eb-110">Hexadecimal string values are character strings representing binary values.</span></span> <span data-ttu-id="b29eb-111">它們沒有諸如 0x 的前置詞。</span><span class="sxs-lookup"><span data-stu-id="b29eb-111">They do not have a prefix such as 0x.</span></span> <span data-ttu-id="b29eb-112">它們包含從 0 至 9 的數字，以及從 "a" 至 "f" 或 "A" 至 "F" 的字母。</span><span class="sxs-lookup"><span data-stu-id="b29eb-112">They contain digits from 0 through 9 and letters from "a" through "f" or "A" through "F".</span></span> <span data-ttu-id="b29eb-113">此配接器會忽略其中的空白。</span><span class="sxs-lookup"><span data-stu-id="b29eb-113">The adapter ignores white space in them.</span></span>  
  
 <span data-ttu-id="b29eb-114">如需有關這些屬性的詳細資訊，請參閱 IBM WebSphere MQ 文件。</span><span class="sxs-lookup"><span data-stu-id="b29eb-114">For more information about these properties, see the IBM WebSphere MQ documentation.</span></span>  
  
 <span data-ttu-id="b29eb-115">下表顯示一組完整、可用的「訊息描述元」(MQMD 結構)」屬性及其對應的類型與值。</span><span class="sxs-lookup"><span data-stu-id="b29eb-115">The following table shows the complete set of available Message Descriptor (MQMD structure) properties and their corresponding types and values.</span></span>  
  
|<span data-ttu-id="b29eb-116">名稱</span><span class="sxs-lookup"><span data-stu-id="b29eb-116">Name</span></span>|<span data-ttu-id="b29eb-117">類型</span><span class="sxs-lookup"><span data-stu-id="b29eb-117">Type</span></span>|<span data-ttu-id="b29eb-118">長度</span><span class="sxs-lookup"><span data-stu-id="b29eb-118">Length</span></span>|<span data-ttu-id="b29eb-119">值</span><span class="sxs-lookup"><span data-stu-id="b29eb-119">Value</span></span>|  
|----------|----------|------------|-----------|  
|<span data-ttu-id="b29eb-120">**MQMD_AccountingToken**</span><span class="sxs-lookup"><span data-stu-id="b29eb-120">**MQMD_AccountingToken**</span></span>|<span data-ttu-id="b29eb-121">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-121">string</span></span>|<span data-ttu-id="b29eb-122">64</span><span class="sxs-lookup"><span data-stu-id="b29eb-122">64</span></span>|<span data-ttu-id="b29eb-123">十六進位字串</span><span class="sxs-lookup"><span data-stu-id="b29eb-123">Hexadecimal string</span></span>|  
|<span data-ttu-id="b29eb-124">**MQMD_ApplIdentityData**</span><span class="sxs-lookup"><span data-stu-id="b29eb-124">**MQMD_ApplIdentityData**</span></span>|<span data-ttu-id="b29eb-125">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-125">string</span></span>|<span data-ttu-id="b29eb-126">32</span><span class="sxs-lookup"><span data-stu-id="b29eb-126">32</span></span>|<span data-ttu-id="b29eb-127">十六進位字串</span><span class="sxs-lookup"><span data-stu-id="b29eb-127">Hexadecimal string</span></span>|  
|<span data-ttu-id="b29eb-128">**MQMD_ApplOriginData**</span><span class="sxs-lookup"><span data-stu-id="b29eb-128">**MQMD_ApplOriginData**</span></span>|<span data-ttu-id="b29eb-129">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-129">string</span></span>|<span data-ttu-id="b29eb-130">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-130">4</span></span>|<span data-ttu-id="b29eb-131">字串</span><span class="sxs-lookup"><span data-stu-id="b29eb-131">String</span></span><br /><br /> <span data-ttu-id="b29eb-132">**預設值：**空間</span><span class="sxs-lookup"><span data-stu-id="b29eb-132">**Default:** space</span></span>|  
|<span data-ttu-id="b29eb-133">**MQMD_BackoutCount**</span><span class="sxs-lookup"><span data-stu-id="b29eb-133">**MQMD_BackoutCount**</span></span>|<span data-ttu-id="b29eb-134">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-134">unsigned int</span></span>|<span data-ttu-id="b29eb-135">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-135">4</span></span>|<span data-ttu-id="b29eb-136">Number</span><span class="sxs-lookup"><span data-stu-id="b29eb-136">Number</span></span><br /><br /> <span data-ttu-id="b29eb-137">唯讀</span><span class="sxs-lookup"><span data-stu-id="b29eb-137">Read only</span></span><br /><br /> <span data-ttu-id="b29eb-138">**預設值：** 0</span><span class="sxs-lookup"><span data-stu-id="b29eb-138">**Default:** 0</span></span>|  
|<span data-ttu-id="b29eb-139">**MQMD_CodedCharSetId**</span><span class="sxs-lookup"><span data-stu-id="b29eb-139">**MQMD_CodedCharSetId**</span></span>|<span data-ttu-id="b29eb-140">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-140">unsigned int</span></span>|<span data-ttu-id="b29eb-141">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-141">4</span></span>|<span data-ttu-id="b29eb-142">Number</span><span class="sxs-lookup"><span data-stu-id="b29eb-142">Number</span></span><br /><br /> <span data-ttu-id="b29eb-143">**預設值：** 0</span><span class="sxs-lookup"><span data-stu-id="b29eb-143">**Default:** 0</span></span>|  
|<span data-ttu-id="b29eb-144">**MQMD_CorrelId**</span><span class="sxs-lookup"><span data-stu-id="b29eb-144">**MQMD_CorrelId**</span></span>|<span data-ttu-id="b29eb-145">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-145">string</span></span>|<span data-ttu-id="b29eb-146">48</span><span class="sxs-lookup"><span data-stu-id="b29eb-146">48</span></span>|<span data-ttu-id="b29eb-147">十六進位字串</span><span class="sxs-lookup"><span data-stu-id="b29eb-147">Hexadecimal string</span></span>|  
|<span data-ttu-id="b29eb-148">**MQMD_Encoding**</span><span class="sxs-lookup"><span data-stu-id="b29eb-148">**MQMD_Encoding**</span></span>|<span data-ttu-id="b29eb-149">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-149">unsigned int</span></span>|<span data-ttu-id="b29eb-150">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-150">4</span></span>|<span data-ttu-id="b29eb-151">Number</span><span class="sxs-lookup"><span data-stu-id="b29eb-151">Number</span></span><br /><br /> <span data-ttu-id="b29eb-152">使用標頭檔值。</span><span class="sxs-lookup"><span data-stu-id="b29eb-152">Use header file value.</span></span> <span data-ttu-id="b29eb-153">**預設值：** 0</span><span class="sxs-lookup"><span data-stu-id="b29eb-153">**Default:** 0</span></span>|  
|<span data-ttu-id="b29eb-154">**MQMD_Expiry**</span><span class="sxs-lookup"><span data-stu-id="b29eb-154">**MQMD_Expiry**</span></span>|<span data-ttu-id="b29eb-155">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-155">unsigned int</span></span>|<span data-ttu-id="b29eb-156">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-156">4</span></span>|<span data-ttu-id="b29eb-157">Number</span><span class="sxs-lookup"><span data-stu-id="b29eb-157">Number</span></span>|  
|<span data-ttu-id="b29eb-158">**MQMD_Feedback**</span><span class="sxs-lookup"><span data-stu-id="b29eb-158">**MQMD_Feedback**</span></span>|<span data-ttu-id="b29eb-159">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-159">unsigned int</span></span>|<span data-ttu-id="b29eb-160">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-160">4</span></span>|<span data-ttu-id="b29eb-161">Number</span><span class="sxs-lookup"><span data-stu-id="b29eb-161">Number</span></span><br /><br /> <span data-ttu-id="b29eb-162">使用標頭檔值。</span><span class="sxs-lookup"><span data-stu-id="b29eb-162">Use header file value.</span></span> <span data-ttu-id="b29eb-163">**預設值：** 0</span><span class="sxs-lookup"><span data-stu-id="b29eb-163">**Default:** 0</span></span>|  
|<span data-ttu-id="b29eb-164">**MQMD_Format**</span><span class="sxs-lookup"><span data-stu-id="b29eb-164">**MQMD_Format**</span></span>|<span data-ttu-id="b29eb-165">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-165">string</span></span>|<span data-ttu-id="b29eb-166">8</span><span class="sxs-lookup"><span data-stu-id="b29eb-166">8</span></span>|<span data-ttu-id="b29eb-167">字串</span><span class="sxs-lookup"><span data-stu-id="b29eb-167">String</span></span><br /><br /> <span data-ttu-id="b29eb-168">若設為 MQXMIT，請確定 MQXQH 屬性有值。</span><span class="sxs-lookup"><span data-stu-id="b29eb-168">If set to MQXMIT, makes sure that the MQXQH properties have values.</span></span>|  
|<span data-ttu-id="b29eb-169">**MQMD_GroupID**</span><span class="sxs-lookup"><span data-stu-id="b29eb-169">**MQMD_GroupID**</span></span>|<span data-ttu-id="b29eb-170">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-170">string</span></span>|<span data-ttu-id="b29eb-171">48</span><span class="sxs-lookup"><span data-stu-id="b29eb-171">48</span></span>|<span data-ttu-id="b29eb-172">十六進位字串</span><span class="sxs-lookup"><span data-stu-id="b29eb-172">Hexadecimal string</span></span>|  
|<span data-ttu-id="b29eb-173">**MQMD_MsgFlags**</span><span class="sxs-lookup"><span data-stu-id="b29eb-173">**MQMD_MsgFlags**</span></span>|<span data-ttu-id="b29eb-174">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-174">unsigned int</span></span>|<span data-ttu-id="b29eb-175">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-175">4</span></span>|<span data-ttu-id="b29eb-176">Number</span><span class="sxs-lookup"><span data-stu-id="b29eb-176">Number</span></span><br /><br /> <span data-ttu-id="b29eb-177">使用標頭檔值。</span><span class="sxs-lookup"><span data-stu-id="b29eb-177">Use header file value.</span></span> <span data-ttu-id="b29eb-178">**預設值：** 0</span><span class="sxs-lookup"><span data-stu-id="b29eb-178">**Default:** 0</span></span>|  
|<span data-ttu-id="b29eb-179">**MQMD_MsgId**</span><span class="sxs-lookup"><span data-stu-id="b29eb-179">**MQMD_MsgId**</span></span>|<span data-ttu-id="b29eb-180">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-180">string</span></span>|<span data-ttu-id="b29eb-181">48</span><span class="sxs-lookup"><span data-stu-id="b29eb-181">48</span></span>|<span data-ttu-id="b29eb-182">十六進位字串</span><span class="sxs-lookup"><span data-stu-id="b29eb-182">Hexadecimal string</span></span>|  
|<span data-ttu-id="b29eb-183">**MQMD_MsgSeqNumber**</span><span class="sxs-lookup"><span data-stu-id="b29eb-183">**MQMD_MsgSeqNumber**</span></span>|<span data-ttu-id="b29eb-184">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-184">unsigned int</span></span>|<span data-ttu-id="b29eb-185">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-185">4</span></span>||  
|<span data-ttu-id="b29eb-186">**MQMD_MsgType**</span><span class="sxs-lookup"><span data-stu-id="b29eb-186">**MQMD_MsgType**</span></span>|<span data-ttu-id="b29eb-187">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-187">unsigned int</span></span>|<span data-ttu-id="b29eb-188">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-188">4</span></span>|<span data-ttu-id="b29eb-189">Number</span><span class="sxs-lookup"><span data-stu-id="b29eb-189">Number</span></span><br /><br /> <span data-ttu-id="b29eb-190">使用標頭檔值。</span><span class="sxs-lookup"><span data-stu-id="b29eb-190">Use header file value.</span></span>|  
|<span data-ttu-id="b29eb-191">**MQMD_Offset**</span><span class="sxs-lookup"><span data-stu-id="b29eb-191">**MQMD_Offset**</span></span>|<span data-ttu-id="b29eb-192">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-192">unsigned int</span></span>|<span data-ttu-id="b29eb-193">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-193">4</span></span>||  
|<span data-ttu-id="b29eb-194">**MQMD_OriginalLength**</span><span class="sxs-lookup"><span data-stu-id="b29eb-194">**MQMD_OriginalLength**</span></span>|<span data-ttu-id="b29eb-195">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-195">unsigned int</span></span>|<span data-ttu-id="b29eb-196">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-196">4</span></span>||  
|<span data-ttu-id="b29eb-197">**MQMD_Persistence**</span><span class="sxs-lookup"><span data-stu-id="b29eb-197">**MQMD_Persistence**</span></span>|<span data-ttu-id="b29eb-198">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-198">unsigned int</span></span>|<span data-ttu-id="b29eb-199">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-199">4</span></span>|<span data-ttu-id="b29eb-200">Number</span><span class="sxs-lookup"><span data-stu-id="b29eb-200">Number</span></span><br /><br /> <span data-ttu-id="b29eb-201">使用標頭檔值。</span><span class="sxs-lookup"><span data-stu-id="b29eb-201">Use header file value.</span></span>|  
|<span data-ttu-id="b29eb-202">**MQMD_Priority**</span><span class="sxs-lookup"><span data-stu-id="b29eb-202">**MQMD_Priority**</span></span>|<span data-ttu-id="b29eb-203">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-203">unsigned int</span></span>|<span data-ttu-id="b29eb-204">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-204">4</span></span>|<span data-ttu-id="b29eb-205">Number</span><span class="sxs-lookup"><span data-stu-id="b29eb-205">Number</span></span>|  
|<span data-ttu-id="b29eb-206">**MQMD_PutApplName**</span><span class="sxs-lookup"><span data-stu-id="b29eb-206">**MQMD_PutApplName**</span></span>|<span data-ttu-id="b29eb-207">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-207">string</span></span>|<span data-ttu-id="b29eb-208">28</span><span class="sxs-lookup"><span data-stu-id="b29eb-208">28</span></span>|<span data-ttu-id="b29eb-209">字串</span><span class="sxs-lookup"><span data-stu-id="b29eb-209">String</span></span><br /><br /> <span data-ttu-id="b29eb-210">**預設值：**空間</span><span class="sxs-lookup"><span data-stu-id="b29eb-210">**Default:** space</span></span>|  
|<span data-ttu-id="b29eb-211">**MQMD_PutApplType**</span><span class="sxs-lookup"><span data-stu-id="b29eb-211">**MQMD_PutApplType**</span></span>|<span data-ttu-id="b29eb-212">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-212">unsigned int</span></span>|<span data-ttu-id="b29eb-213">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-213">4</span></span>|<span data-ttu-id="b29eb-214">Number</span><span class="sxs-lookup"><span data-stu-id="b29eb-214">Number</span></span><br /><br /> <span data-ttu-id="b29eb-215">使用標頭檔值。</span><span class="sxs-lookup"><span data-stu-id="b29eb-215">Use header file value.</span></span> <span data-ttu-id="b29eb-216">**預設值：** 0</span><span class="sxs-lookup"><span data-stu-id="b29eb-216">**Default:** 0</span></span>|  
|<span data-ttu-id="b29eb-217">**MQMD_PutDate**</span><span class="sxs-lookup"><span data-stu-id="b29eb-217">**MQMD_PutDate**</span></span>|<span data-ttu-id="b29eb-218">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-218">string</span></span>|<span data-ttu-id="b29eb-219">8</span><span class="sxs-lookup"><span data-stu-id="b29eb-219">8</span></span>|<span data-ttu-id="b29eb-220">日期</span><span class="sxs-lookup"><span data-stu-id="b29eb-220">Date</span></span>|  
|<span data-ttu-id="b29eb-221">**MQMD_PutTime**</span><span class="sxs-lookup"><span data-stu-id="b29eb-221">**MQMD_PutTime**</span></span>|<span data-ttu-id="b29eb-222">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-222">string</span></span>|<span data-ttu-id="b29eb-223">8</span><span class="sxs-lookup"><span data-stu-id="b29eb-223">8</span></span>|<span data-ttu-id="b29eb-224">Time</span><span class="sxs-lookup"><span data-stu-id="b29eb-224">Time</span></span>|  
|<span data-ttu-id="b29eb-225">**MQMD_ReplyToQ**</span><span class="sxs-lookup"><span data-stu-id="b29eb-225">**MQMD_ReplyToQ**</span></span>|<span data-ttu-id="b29eb-226">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-226">string</span></span>|<span data-ttu-id="b29eb-227">48</span><span class="sxs-lookup"><span data-stu-id="b29eb-227">48</span></span>|<span data-ttu-id="b29eb-228">字串</span><span class="sxs-lookup"><span data-stu-id="b29eb-228">String</span></span><br /><br /> <span data-ttu-id="b29eb-229">**預設值：**空間</span><span class="sxs-lookup"><span data-stu-id="b29eb-229">**Default:** space</span></span>|  
|<span data-ttu-id="b29eb-230">**MQMD_ReplyToQMgr**</span><span class="sxs-lookup"><span data-stu-id="b29eb-230">**MQMD_ReplyToQMgr**</span></span>|<span data-ttu-id="b29eb-231">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-231">string</span></span>|<span data-ttu-id="b29eb-232">48</span><span class="sxs-lookup"><span data-stu-id="b29eb-232">48</span></span>|<span data-ttu-id="b29eb-233">字串</span><span class="sxs-lookup"><span data-stu-id="b29eb-233">String</span></span><br /><br /> <span data-ttu-id="b29eb-234">**預設值：**空間</span><span class="sxs-lookup"><span data-stu-id="b29eb-234">**Default:** space</span></span>|  
|<span data-ttu-id="b29eb-235">**MQMD_Report**</span><span class="sxs-lookup"><span data-stu-id="b29eb-235">**MQMD_Report**</span></span>|<span data-ttu-id="b29eb-236">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-236">unsigned int</span></span>|<span data-ttu-id="b29eb-237">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-237">4</span></span>|<span data-ttu-id="b29eb-238">Number</span><span class="sxs-lookup"><span data-stu-id="b29eb-238">Number</span></span><br /><br /> <span data-ttu-id="b29eb-239">使用標頭檔值。</span><span class="sxs-lookup"><span data-stu-id="b29eb-239">Use header file value.</span></span>|  
|<span data-ttu-id="b29eb-240">**MQMD_UserIdentifier**</span><span class="sxs-lookup"><span data-stu-id="b29eb-240">**MQMD_UserIdentifier**</span></span>|<span data-ttu-id="b29eb-241">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-241">string</span></span>|<span data-ttu-id="b29eb-242">12</span><span class="sxs-lookup"><span data-stu-id="b29eb-242">12</span></span>|<span data-ttu-id="b29eb-243">字串</span><span class="sxs-lookup"><span data-stu-id="b29eb-243">String</span></span><br /><br /> <span data-ttu-id="b29eb-244">當您使用包含使用者識別碼**SSOAffiliateApplication**屬性。</span><span class="sxs-lookup"><span data-stu-id="b29eb-244">Contains the user identifier when you use the **SSOAffiliateApplication** property.</span></span>|  
  
 <span data-ttu-id="b29eb-245">直接從 MQSeries 傳輸佇列接收訊息時，MQSeries 配接器會將傳輸佇列標頭屬性 (MQXQH 資料結構) 格式化，然後放在對應的內容屬性中。</span><span class="sxs-lookup"><span data-stu-id="b29eb-245">When receiving messages directly from MQSeries transmission queues, the MQSeries adapter formats the transmission queue header properties (the MQXQH data structure) and places them in their corresponding context properties.</span></span> <span data-ttu-id="b29eb-246">標頭屬性時直接傳送訊息至 MQSeries 傳輸佇列，來格式化和指派值給對應的內容屬性只有當從**MQMD_Format**屬性的值為 MQXMIT。</span><span class="sxs-lookup"><span data-stu-id="b29eb-246">When sending messages directly to MQSeries transmission queues, the header properties are formatted and assigned values from the corresponding context properties only if the **MQMD_Format** property has a value of MQXMIT.</span></span> <span data-ttu-id="b29eb-247">下表描述這些屬性。</span><span class="sxs-lookup"><span data-stu-id="b29eb-247">The following table describes the properties.</span></span>  
  
|<span data-ttu-id="b29eb-248">名稱</span><span class="sxs-lookup"><span data-stu-id="b29eb-248">Name</span></span>|<span data-ttu-id="b29eb-249">類型</span><span class="sxs-lookup"><span data-stu-id="b29eb-249">Type</span></span>|<span data-ttu-id="b29eb-250">長度</span><span class="sxs-lookup"><span data-stu-id="b29eb-250">Length</span></span>|<span data-ttu-id="b29eb-251">值</span><span class="sxs-lookup"><span data-stu-id="b29eb-251">Value</span></span>|  
|----------|----------|------------|-----------|  
|<span data-ttu-id="b29eb-252">**MQXQH_RemoteQMgrName**</span><span class="sxs-lookup"><span data-stu-id="b29eb-252">**MQXQH_RemoteQMgrName**</span></span>|<span data-ttu-id="b29eb-253">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-253">string</span></span>|<span data-ttu-id="b29eb-254">48</span><span class="sxs-lookup"><span data-stu-id="b29eb-254">48</span></span>|<span data-ttu-id="b29eb-255">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-255">string</span></span>|  
|<span data-ttu-id="b29eb-256">**MQXQH_RemoteQName**</span><span class="sxs-lookup"><span data-stu-id="b29eb-256">**MQXQH_RemoteQName**</span></span>|<span data-ttu-id="b29eb-257">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-257">string</span></span>|<span data-ttu-id="b29eb-258">48</span><span class="sxs-lookup"><span data-stu-id="b29eb-258">48</span></span>|<span data-ttu-id="b29eb-259">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-259">string</span></span>|  
  
 <span data-ttu-id="b29eb-260">此配接器會根據相同規則將本主題稍早所列的屬性一起填入下列「訊息描述元」值中。</span><span class="sxs-lookup"><span data-stu-id="b29eb-260">Together with the properties listed earlier in this topic, the adapter populates the following Message Descriptor values following the same rules.</span></span> <span data-ttu-id="b29eb-261">此配接器會在這些屬性名稱之前加上 MQXQH_ 而不是 MQMD_，否則它們會直接對應至「訊息描述元」表格中所定義的那些屬性：</span><span class="sxs-lookup"><span data-stu-id="b29eb-261">The adapter prefixes these property names with MQXQH_ instead of MQMD_, but otherwise they map directly to those properties defined in the Message Descriptor table:</span></span>  
  
-   <span data-ttu-id="b29eb-262">**MQXQH_MsgDesc_AccountingToken**</span><span class="sxs-lookup"><span data-stu-id="b29eb-262">**MQXQH_MsgDesc_AccountingToken**</span></span>  
  
-   <span data-ttu-id="b29eb-263">**MQXQH_MsgDesc_ApplIdentityData**</span><span class="sxs-lookup"><span data-stu-id="b29eb-263">**MQXQH_MsgDesc_ApplIdentityData**</span></span>  
  
-   <span data-ttu-id="b29eb-264">**MQXQH_MsgDesc_ApplOriginData**</span><span class="sxs-lookup"><span data-stu-id="b29eb-264">**MQXQH_MsgDesc_ApplOriginData**</span></span>  
  
-   <span data-ttu-id="b29eb-265">**MQXQH_MsgDesc_BackoutCount**</span><span class="sxs-lookup"><span data-stu-id="b29eb-265">**MQXQH_MsgDesc_BackoutCount**</span></span>  
  
-   <span data-ttu-id="b29eb-266">**MQXQH_MsgDesc_CodedCharSetId**</span><span class="sxs-lookup"><span data-stu-id="b29eb-266">**MQXQH_MsgDesc_CodedCharSetId**</span></span>  
  
-   <span data-ttu-id="b29eb-267">**MQXQH_MsgDesc_CorrelId**</span><span class="sxs-lookup"><span data-stu-id="b29eb-267">**MQXQH_MsgDesc_CorrelId**</span></span>  
  
-   <span data-ttu-id="b29eb-268">**MQXQH_MsgDesc_Encoding**</span><span class="sxs-lookup"><span data-stu-id="b29eb-268">**MQXQH_MsgDesc_Encoding**</span></span>  
  
-   <span data-ttu-id="b29eb-269">**MQXQH_MsgDesc_Expiry**</span><span class="sxs-lookup"><span data-stu-id="b29eb-269">**MQXQH_MsgDesc_Expiry**</span></span>  
  
-   <span data-ttu-id="b29eb-270">**MQXQH_MsgDesc_Feedback**</span><span class="sxs-lookup"><span data-stu-id="b29eb-270">**MQXQH_MsgDesc_Feedback**</span></span>  
  
-   <span data-ttu-id="b29eb-271">**MQXQH_MsgDesc_Format**</span><span class="sxs-lookup"><span data-stu-id="b29eb-271">**MQXQH_MsgDesc_Format**</span></span>  
  
-   <span data-ttu-id="b29eb-272">**MQXQH_MsgDesc_MsgId**</span><span class="sxs-lookup"><span data-stu-id="b29eb-272">**MQXQH_MsgDesc_MsgId**</span></span>  
  
-   <span data-ttu-id="b29eb-273">**MQXQH_MsgDesc_MsgType**</span><span class="sxs-lookup"><span data-stu-id="b29eb-273">**MQXQH_MsgDesc_MsgType**</span></span>  
  
-   <span data-ttu-id="b29eb-274">**MQXQH_MsgDesc_Persistence**</span><span class="sxs-lookup"><span data-stu-id="b29eb-274">**MQXQH_MsgDesc_Persistence**</span></span>  
  
-   <span data-ttu-id="b29eb-275">**MQXQH_MsgDesc_Priority**</span><span class="sxs-lookup"><span data-stu-id="b29eb-275">**MQXQH_MsgDesc_Priority**</span></span>  
  
-   <span data-ttu-id="b29eb-276">**MQXQH_MsgDesc_PutApplName**</span><span class="sxs-lookup"><span data-stu-id="b29eb-276">**MQXQH_MsgDesc_PutApplName**</span></span>  
  
-   <span data-ttu-id="b29eb-277">**MQXQH_MsgDesc_PutApplType**</span><span class="sxs-lookup"><span data-stu-id="b29eb-277">**MQXQH_MsgDesc_PutApplType**</span></span>  
  
-   <span data-ttu-id="b29eb-278">**MQXQH_MsgDesc_PutDate**</span><span class="sxs-lookup"><span data-stu-id="b29eb-278">**MQXQH_MsgDesc_PutDate**</span></span>  
  
-   <span data-ttu-id="b29eb-279">**MQXQH_MsgDesc_PutTime**</span><span class="sxs-lookup"><span data-stu-id="b29eb-279">**MQXQH_MsgDesc_PutTime**</span></span>  
  
-   <span data-ttu-id="b29eb-280">**MQXQH_MsgDesc_ReplyToQ**</span><span class="sxs-lookup"><span data-stu-id="b29eb-280">**MQXQH_MsgDesc_ReplyToQ**</span></span>  
  
-   <span data-ttu-id="b29eb-281">**MQXQH_MsgDesc_ReplyToQMgr**</span><span class="sxs-lookup"><span data-stu-id="b29eb-281">**MQXQH_MsgDesc_ReplyToQMgr**</span></span>  
  
-   <span data-ttu-id="b29eb-282">**MQXQH_MsgDesc_Report**</span><span class="sxs-lookup"><span data-stu-id="b29eb-282">**MQXQH_MsgDesc_Report**</span></span>  
  
-   <span data-ttu-id="b29eb-283">**MQXQH_MsgDesc_UserIdentifier**</span><span class="sxs-lookup"><span data-stu-id="b29eb-283">**MQXQH_MsgDesc_UserIdentifier**</span></span>  
  
 <span data-ttu-id="b29eb-284">在屬性結構描述中還包含其他與 MQSeries 相關的屬性，並可用於篩選運算式中。</span><span class="sxs-lookup"><span data-stu-id="b29eb-284">There are additional MQSeries-related properties included in the property schema and available for use in filtering expressions.</span></span> <span data-ttu-id="b29eb-285">下表列出這些屬性。</span><span class="sxs-lookup"><span data-stu-id="b29eb-285">The following table lists these properties.</span></span>  
  
|<span data-ttu-id="b29eb-286">名稱</span><span class="sxs-lookup"><span data-stu-id="b29eb-286">Name</span></span>|<span data-ttu-id="b29eb-287">類型</span><span class="sxs-lookup"><span data-stu-id="b29eb-287">Type</span></span>|<span data-ttu-id="b29eb-288">長度</span><span class="sxs-lookup"><span data-stu-id="b29eb-288">Length</span></span>|<span data-ttu-id="b29eb-289">值</span><span class="sxs-lookup"><span data-stu-id="b29eb-289">Value</span></span>|  
|----------|----------|------------|-----------|  
|<span data-ttu-id="b29eb-290">**MQCIH_AbendCode**</span><span class="sxs-lookup"><span data-stu-id="b29eb-290">**MQCIH_AbendCode**</span></span>|<span data-ttu-id="b29eb-291">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-291">string</span></span>|<span data-ttu-id="b29eb-292">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-292">4</span></span>||  
|<span data-ttu-id="b29eb-293">**MQCIH_ADSDescriptor**</span><span class="sxs-lookup"><span data-stu-id="b29eb-293">**MQCIH_ADSDescriptor**</span></span>|<span data-ttu-id="b29eb-294">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-294">unsigned int</span></span>|<span data-ttu-id="b29eb-295">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-295">4</span></span>||  
|<span data-ttu-id="b29eb-296">**MQCIH_AttentionId**</span><span class="sxs-lookup"><span data-stu-id="b29eb-296">**MQCIH_AttentionId**</span></span>|<span data-ttu-id="b29eb-297">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-297">string</span></span>|<span data-ttu-id="b29eb-298">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-298">4</span></span>||  
|<span data-ttu-id="b29eb-299">**MQCIH_Authenticator**</span><span class="sxs-lookup"><span data-stu-id="b29eb-299">**MQCIH_Authenticator**</span></span>|<span data-ttu-id="b29eb-300">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-300">string</span></span>|<span data-ttu-id="b29eb-301">8</span><span class="sxs-lookup"><span data-stu-id="b29eb-301">8</span></span>|<span data-ttu-id="b29eb-302">當您使用設定為 SSO 密碼**SSOAffiliateApplication**屬性。</span><span class="sxs-lookup"><span data-stu-id="b29eb-302">Set to the SSO password when you use the **SSOAffiliateApplication** property.</span></span> <span data-ttu-id="b29eb-303">**注意：**這個值會設為空白，MQSeries 配接器，如果 SSO 密碼的長度超過 8 個字元。</span><span class="sxs-lookup"><span data-stu-id="b29eb-303">**Note:**  This value will be set to blank by the MQSeries adapter if length of the SSO password exceeds 8 characters.</span></span>|  
|<span data-ttu-id="b29eb-304">**MQCIH_CancelCode**</span><span class="sxs-lookup"><span data-stu-id="b29eb-304">**MQCIH_CancelCode**</span></span>|<span data-ttu-id="b29eb-305">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-305">string</span></span>|<span data-ttu-id="b29eb-306">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-306">4</span></span>||  
|<span data-ttu-id="b29eb-307">**MQCIH_CompCode**</span><span class="sxs-lookup"><span data-stu-id="b29eb-307">**MQCIH_CompCode**</span></span>|<span data-ttu-id="b29eb-308">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-308">unsigned int</span></span>|<span data-ttu-id="b29eb-309">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-309">4</span></span>||  
|<span data-ttu-id="b29eb-310">**MQCIH_ConversationalTask**</span><span class="sxs-lookup"><span data-stu-id="b29eb-310">**MQCIH_ConversationalTask**</span></span>|<span data-ttu-id="b29eb-311">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-311">unsigned int</span></span>|<span data-ttu-id="b29eb-312">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-312">4</span></span>||  
|<span data-ttu-id="b29eb-313">**MQCIH_CursorPosition**</span><span class="sxs-lookup"><span data-stu-id="b29eb-313">**MQCIH_CursorPosition**</span></span>|<span data-ttu-id="b29eb-314">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-314">unsigned int</span></span>|<span data-ttu-id="b29eb-315">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-315">4</span></span>||  
|<span data-ttu-id="b29eb-316">**MQCIH_ErrorOffset**</span><span class="sxs-lookup"><span data-stu-id="b29eb-316">**MQCIH_ErrorOffset**</span></span>|<span data-ttu-id="b29eb-317">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-317">unsigned int</span></span>|<span data-ttu-id="b29eb-318">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-318">4</span></span>||  
|<span data-ttu-id="b29eb-319">**MQCIH_Facility**</span><span class="sxs-lookup"><span data-stu-id="b29eb-319">**MQCIH_Facility**</span></span>|<span data-ttu-id="b29eb-320">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-320">string</span></span>|<span data-ttu-id="b29eb-321">16</span><span class="sxs-lookup"><span data-stu-id="b29eb-321">16</span></span>|<span data-ttu-id="b29eb-322">十六進位字串</span><span class="sxs-lookup"><span data-stu-id="b29eb-322">Hexadecimal string</span></span>|  
|<span data-ttu-id="b29eb-323">**MQCIH_FacilityKeepTime**</span><span class="sxs-lookup"><span data-stu-id="b29eb-323">**MQCIH_FacilityKeepTime**</span></span>|<span data-ttu-id="b29eb-324">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-324">unsigned int</span></span>|<span data-ttu-id="b29eb-325">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-325">4</span></span>||  
|<span data-ttu-id="b29eb-326">**MQCIH_FacilityLike**</span><span class="sxs-lookup"><span data-stu-id="b29eb-326">**MQCIH_FacilityLike**</span></span>|<span data-ttu-id="b29eb-327">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-327">string</span></span>|<span data-ttu-id="b29eb-328">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-328">4</span></span>||  
|<span data-ttu-id="b29eb-329">**MQCIH_Flags**</span><span class="sxs-lookup"><span data-stu-id="b29eb-329">**MQCIH_Flags**</span></span>|<span data-ttu-id="b29eb-330">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-330">unsigned int</span></span>|<span data-ttu-id="b29eb-331">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-331">4</span></span>||  
|<span data-ttu-id="b29eb-332">**MQCIH_Format**</span><span class="sxs-lookup"><span data-stu-id="b29eb-332">**MQCIH_Format**</span></span>|<span data-ttu-id="b29eb-333">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-333">string</span></span>|||  
|<span data-ttu-id="b29eb-334">**MQCIH_Function**</span><span class="sxs-lookup"><span data-stu-id="b29eb-334">**MQCIH_Function**</span></span>|<span data-ttu-id="b29eb-335">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-335">string</span></span>|<span data-ttu-id="b29eb-336">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-336">4</span></span>||  
|<span data-ttu-id="b29eb-337">**MQCIH_GetWaitInterval**</span><span class="sxs-lookup"><span data-stu-id="b29eb-337">**MQCIH_GetWaitInterval**</span></span>|<span data-ttu-id="b29eb-338">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-338">unsigned int</span></span>|<span data-ttu-id="b29eb-339">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-339">4</span></span>||  
|<span data-ttu-id="b29eb-340">**MQCIH_LinkType**</span><span class="sxs-lookup"><span data-stu-id="b29eb-340">**MQCIH_LinkType**</span></span>|<span data-ttu-id="b29eb-341">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-341">unsigned int</span></span>|<span data-ttu-id="b29eb-342">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-342">4</span></span>||  
|<span data-ttu-id="b29eb-343">**MQCIH_NextTransactionId**</span><span class="sxs-lookup"><span data-stu-id="b29eb-343">**MQCIH_NextTransactionId**</span></span>|<span data-ttu-id="b29eb-344">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-344">string</span></span>|<span data-ttu-id="b29eb-345">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-345">4</span></span>||  
|<span data-ttu-id="b29eb-346">**MQCIH_OutputDataLength**</span><span class="sxs-lookup"><span data-stu-id="b29eb-346">**MQCIH_OutputDataLength**</span></span>|<span data-ttu-id="b29eb-347">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-347">unsigned int</span></span>|<span data-ttu-id="b29eb-348">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-348">4</span></span>||  
|<span data-ttu-id="b29eb-349">**MQCIH_Reason**</span><span class="sxs-lookup"><span data-stu-id="b29eb-349">**MQCIH_Reason**</span></span>|<span data-ttu-id="b29eb-350">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-350">unsigned int</span></span>|<span data-ttu-id="b29eb-351">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-351">4</span></span>||  
|<span data-ttu-id="b29eb-352">**MQCIH_ReplyToFormat**</span><span class="sxs-lookup"><span data-stu-id="b29eb-352">**MQCIH_ReplyToFormat**</span></span>|<span data-ttu-id="b29eb-353">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-353">string</span></span>|||  
|<span data-ttu-id="b29eb-354">**MQCIH_ReturnCode**</span><span class="sxs-lookup"><span data-stu-id="b29eb-354">**MQCIH_ReturnCode**</span></span>|<span data-ttu-id="b29eb-355">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-355">unsigned int</span></span>|<span data-ttu-id="b29eb-356">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-356">4</span></span>||  
|<span data-ttu-id="b29eb-357">**MQCIH_StartCode**</span><span class="sxs-lookup"><span data-stu-id="b29eb-357">**MQCIH_StartCode**</span></span>|<span data-ttu-id="b29eb-358">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-358">string</span></span>|<span data-ttu-id="b29eb-359">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-359">4</span></span>||  
|<span data-ttu-id="b29eb-360">**MQCIH_TaskEndStatus**</span><span class="sxs-lookup"><span data-stu-id="b29eb-360">**MQCIH_TaskEndStatus**</span></span>|<span data-ttu-id="b29eb-361">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-361">unsigned int</span></span>|<span data-ttu-id="b29eb-362">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-362">4</span></span>||  
|<span data-ttu-id="b29eb-363">**MQCIH_TransactionId**</span><span class="sxs-lookup"><span data-stu-id="b29eb-363">**MQCIH_TransactionId**</span></span>|<span data-ttu-id="b29eb-364">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-364">string</span></span>|<span data-ttu-id="b29eb-365">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-365">4</span></span>||  
|<span data-ttu-id="b29eb-366">**MQCIH_UOWControl**</span><span class="sxs-lookup"><span data-stu-id="b29eb-366">**MQCIH_UOWControl**</span></span>|<span data-ttu-id="b29eb-367">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-367">unsigned int</span></span>|<span data-ttu-id="b29eb-368">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-368">4</span></span>||  
|<span data-ttu-id="b29eb-369">**MQIIH_Authenticator**</span><span class="sxs-lookup"><span data-stu-id="b29eb-369">**MQIIH_Authenticator**</span></span>|<span data-ttu-id="b29eb-370">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-370">string</span></span>|<span data-ttu-id="b29eb-371">8</span><span class="sxs-lookup"><span data-stu-id="b29eb-371">8</span></span>|<span data-ttu-id="b29eb-372">當您使用設定為 SSO 密碼**SSOAffiliateApplication**屬性。</span><span class="sxs-lookup"><span data-stu-id="b29eb-372">Set to the SSO password when you use the **SSOAffiliateApplication** property.</span></span> <span data-ttu-id="b29eb-373">**注意：**這個值會設為空白，MQSeries 配接器，如果 SSO 密碼的長度超過 8 個字元。</span><span class="sxs-lookup"><span data-stu-id="b29eb-373">**Note:**  This value will be set to blank by the MQSeries adapter if length of the SSO password exceeds 8 characters.</span></span>|  
|<span data-ttu-id="b29eb-374">**MQIIH_CommitMode**</span><span class="sxs-lookup"><span data-stu-id="b29eb-374">**MQIIH_CommitMode**</span></span>|<span data-ttu-id="b29eb-375">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-375">string</span></span>|||  
|<span data-ttu-id="b29eb-376">**MQIIH_Flags**</span><span class="sxs-lookup"><span data-stu-id="b29eb-376">**MQIIH_Flags**</span></span>|<span data-ttu-id="b29eb-377">不帶正負號的整數</span><span class="sxs-lookup"><span data-stu-id="b29eb-377">unsigned int</span></span>|<span data-ttu-id="b29eb-378">4</span><span class="sxs-lookup"><span data-stu-id="b29eb-378">4</span></span>||  
|<span data-ttu-id="b29eb-379">**MQIIH_Format**</span><span class="sxs-lookup"><span data-stu-id="b29eb-379">**MQIIH_Format**</span></span>|<span data-ttu-id="b29eb-380">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-380">string</span></span>|||  
|<span data-ttu-id="b29eb-381">**MQIIH_LTermOverride**</span><span class="sxs-lookup"><span data-stu-id="b29eb-381">**MQIIH_LTermOverride**</span></span>|<span data-ttu-id="b29eb-382">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-382">string</span></span>|<span data-ttu-id="b29eb-383">8</span><span class="sxs-lookup"><span data-stu-id="b29eb-383">8</span></span>||  
|<span data-ttu-id="b29eb-384">**MQIIH_MFSMapName**</span><span class="sxs-lookup"><span data-stu-id="b29eb-384">**MQIIH_MFSMapName**</span></span>|<span data-ttu-id="b29eb-385">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-385">string</span></span>|<span data-ttu-id="b29eb-386">8</span><span class="sxs-lookup"><span data-stu-id="b29eb-386">8</span></span>||  
|<span data-ttu-id="b29eb-387">**MQIIH_ReplyToFormat**</span><span class="sxs-lookup"><span data-stu-id="b29eb-387">**MQIIH_ReplyToFormat**</span></span>|<span data-ttu-id="b29eb-388">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-388">string</span></span>|||  
|<span data-ttu-id="b29eb-389">**MQIIH_SecurityScope**</span><span class="sxs-lookup"><span data-stu-id="b29eb-389">**MQIIH_SecurityScope**</span></span>|<span data-ttu-id="b29eb-390">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-390">string</span></span>|||  
|<span data-ttu-id="b29eb-391">**MQIIH_TranInstanceId**</span><span class="sxs-lookup"><span data-stu-id="b29eb-391">**MQIIH_TranInstanceId**</span></span>|<span data-ttu-id="b29eb-392">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-392">string</span></span>|<span data-ttu-id="b29eb-393">32</span><span class="sxs-lookup"><span data-stu-id="b29eb-393">32</span></span>|<span data-ttu-id="b29eb-394">十六進位字串</span><span class="sxs-lookup"><span data-stu-id="b29eb-394">Hexadecimal string</span></span>|  
|<span data-ttu-id="b29eb-395">**MQIIH_TranState**</span><span class="sxs-lookup"><span data-stu-id="b29eb-395">**MQIIH_TranState**</span></span>|<span data-ttu-id="b29eb-396">string</span><span class="sxs-lookup"><span data-stu-id="b29eb-396">string</span></span>|||  
  
## <a name="see-also"></a><span data-ttu-id="b29eb-397">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b29eb-397">See Also</span></span>  
 <span data-ttu-id="b29eb-398">[MQSeries 配接器屬性](../core/mqseries-adapter-properties.md) </span><span class="sxs-lookup"><span data-stu-id="b29eb-398">[MQSeries Adapter Properties](../core/mqseries-adapter-properties.md) </span></span>  
 <span data-ttu-id="b29eb-399">[與 BizTalk Server 相關的屬性](../core/properties-related-to-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="b29eb-399">[Properties Related to BizTalk Server](../core/properties-related-to-biztalk-server.md) </span></span>  
 [<span data-ttu-id="b29eb-400">屬性的資料類型轉換</span><span class="sxs-lookup"><span data-stu-id="b29eb-400">Data Type Conversion of Properties</span></span>](../core/data-type-conversion-of-properties.md)