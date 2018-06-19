---
title: 覆寫 EDI 標頭 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 16c19d3d-eab2-4d44-8752-25aeadb537a4
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 510a3817d0fd99d43b6da9462c74dd8bc7c1bdf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22265438"
---
# <a name="overriding-edi-headers"></a><span data-ttu-id="4b536-102">覆寫 EDI 標頭</span><span class="sxs-lookup"><span data-stu-id="4b536-102">Overriding EDI Headers</span></span>
<span data-ttu-id="4b536-103">傳送 EDI 編碼交換時，套用至訊息的 EDI 信封通常是根據接收端協議的 EDI 屬性，或是後援協議屬性。</span><span class="sxs-lookup"><span data-stu-id="4b536-103">When sending an EDI-encoded interchange, the EDI envelope applied to the message is normally based upon the EDI properties of the receiving agreement, or the fallback agreement properties.</span></span> <span data-ttu-id="4b536-104">不過，根據執行階段產生的值來設定 EDI 信封屬性通常會很有用。</span><span class="sxs-lookup"><span data-stu-id="4b536-104">However it is often useful to set the EDI envelope properties based on runtime generated values.</span></span>  
  
 <span data-ttu-id="4b536-105">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中，您可以使用 EdiOverride 內容屬性來指定針對輸出文件產生 EDI 信封所用的值。</span><span class="sxs-lookup"><span data-stu-id="4b536-105">In [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you can use the EdiOverride context properties to specify the values used to generate the EDI envelope on outbound documents.</span></span>  
  
## <a name="using-edioverride-context-properties"></a><span data-ttu-id="4b536-106">使用 EdiOverride 內容屬性</span><span class="sxs-lookup"><span data-stu-id="4b536-106">Using EdiOverride Context Properties</span></span>  
 <span data-ttu-id="4b536-107">EdiOverride 內容屬性可讓您覆寫用來產生 EDI 信封的所有或部分值。</span><span class="sxs-lookup"><span data-stu-id="4b536-107">The EdiOverride context properties provide a way to override all, or part, of the values used to generate the EDI envelope.</span></span> <span data-ttu-id="4b536-108">EDI 傳送管線將使用包含有效值的 EdiOverride 內容屬性來建構信封。</span><span class="sxs-lookup"><span data-stu-id="4b536-108">The EDI send pipeline will use EdiOverride context property that contains a valid value to construct the envelope.</span></span> <span data-ttu-id="4b536-109">如果沒有填入某個屬性，此管線將會使用協議屬性或後援協議屬性 (如果沒有定義協議的話) 中指定的值。</span><span class="sxs-lookup"><span data-stu-id="4b536-109">If a property is not populated, the pipeline will use the value specified in agreement properties or fallback agreement properties, if an agreement is not defined.</span></span> <span data-ttu-id="4b536-110">如果某個屬性包含無效的值，此管線將會擱置訊息並回報驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="4b536-110">If a property contains an invalid value, the pipeline will suspend the message and report a validation error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b536-111">只有當 `EdiOverride.OverrideEdiHeader` 屬性已寫入訊息的內容而且包含 “True” 值時，才會使用 EdiOverride 集合中指定的值。</span><span class="sxs-lookup"><span data-stu-id="4b536-111">The values specified in the EdiOverride collection are only used if the `EdiOverride.OverrideEdiHeader` property is written into the context of a message and contains a value of “True”.</span></span>  
>   
>  <span data-ttu-id="4b536-112">系統不會設定預設值。</span><span class="sxs-lookup"><span data-stu-id="4b536-112">The default value is not set.</span></span>  
  
### <a name="edioverride-properties-for-x12-envelope-values"></a><span data-ttu-id="4b536-113">X12 信封值的 EdiOverride 屬性</span><span class="sxs-lookup"><span data-stu-id="4b536-113">EdiOverride properties for X12 Envelope Values</span></span>  
 <span data-ttu-id="4b536-114">下表顯示 EdiOverride 內容屬性以及對應的 X12 信封標頭：</span><span class="sxs-lookup"><span data-stu-id="4b536-114">The following table shows the EdiOverride context properties and the corresponding X12 envelope header:</span></span>  
  
|<span data-ttu-id="4b536-115">標頭</span><span class="sxs-lookup"><span data-stu-id="4b536-115">Header</span></span>|<span data-ttu-id="4b536-116">屬性</span><span class="sxs-lookup"><span data-stu-id="4b536-116">Properties</span></span>|  
|------------|----------------|  
|<span data-ttu-id="4b536-117">交換控制標頭 (ISA)</span><span class="sxs-lookup"><span data-stu-id="4b536-117">Interchange Control Header (ISA)</span></span>|<span data-ttu-id="4b536-118">ISA01、ISA02、ISA03、ISA04、ISA05、ISA06、ISA07、ISA08、ISA09、ISA10、ISA11、ISA12、ISA13、ISA14、ISA15、ISA16</span><span class="sxs-lookup"><span data-stu-id="4b536-118">ISA01, ISA02, ISA03, ISA04, ISA05, ISA06, ISA07, ISA08, ISA09, ISA10, ISA11, ISA12, ISA13, ISA14, ISA15, ISA16</span></span>|  
|<span data-ttu-id="4b536-119">功能群組標頭 (GS)</span><span class="sxs-lookup"><span data-stu-id="4b536-119">Functional Group Headers (GS)</span></span>|<span data-ttu-id="4b536-120">GS01、GS02、GS03、GS04、GS05、GS06、GS07、GS08</span><span class="sxs-lookup"><span data-stu-id="4b536-120">GS01, GS02, GS03, GS04, GS05, GS06, GS07, GS08</span></span>|  
|<span data-ttu-id="4b536-121">交易集標頭</span><span class="sxs-lookup"><span data-stu-id="4b536-121">Transaction Set Header</span></span>|<span data-ttu-id="4b536-122">ST02</span><span class="sxs-lookup"><span data-stu-id="4b536-122">ST02</span></span>|  
  
### <a name="edioverride-properties-for-edifact-envelope-values"></a><span data-ttu-id="4b536-123">EDIFACT 信封值的 EdiOverride 屬性</span><span class="sxs-lookup"><span data-stu-id="4b536-123">EdiOverride properties for EDIFACT Envelope Values</span></span>  
 <span data-ttu-id="4b536-124">下表顯示 EdiOverride 內容屬性以及對應的 EDIFACT 信封區段：</span><span class="sxs-lookup"><span data-stu-id="4b536-124">The following table shows the EdiOverride context properties and the corresponding EDIFACT envelope segment:</span></span>  
  
|<span data-ttu-id="4b536-125">區段</span><span class="sxs-lookup"><span data-stu-id="4b536-125">Segment</span></span>|<span data-ttu-id="4b536-126">屬性</span><span class="sxs-lookup"><span data-stu-id="4b536-126">Properties</span></span>|  
|-------------|----------------|  
|<span data-ttu-id="4b536-127">字串服務建議 (UNA)</span><span class="sxs-lookup"><span data-stu-id="4b536-127">Service String Advice (UNA)</span></span>|<span data-ttu-id="4b536-128">UNA1、UNA2、UNA3、UNA4、UNA5、UNA6、UNA6Suffix</span><span class="sxs-lookup"><span data-stu-id="4b536-128">UNA1, UNA2, UNA3, UNA4, UNA5, UNA6, UNA6Suffix</span></span>|  
|<span data-ttu-id="4b536-129">交換控制標頭 (UNB)</span><span class="sxs-lookup"><span data-stu-id="4b536-129">Interchange Control Header (UNB)</span></span>|<span data-ttu-id="4b536-130">UNB1_1、UNB1_2、UNB2_1、UNB2_2、UNB2_3、UNB3_1、UNB3_2、UNB3_3、UNB4_1、UNB4_2、UNB5、UNB6_1、UNB7、UNB8、UNB9、UNB10、UNB11</span><span class="sxs-lookup"><span data-stu-id="4b536-130">UNB1_1, UNB1_2, UNB2_1, UNB2_2, UNB2_3, UNB3_1, UNB3_2, UNB3_3, UNB4_1, UNB4_2, UNB5, UNB6_1, UNB7, UNB8, UNB9, UNB10, UNB11</span></span>|  
|<span data-ttu-id="4b536-131">功能群組標頭 (UNG)</span><span class="sxs-lookup"><span data-stu-id="4b536-131">Functional Group Headers (UNG)</span></span>|<span data-ttu-id="4b536-132">UNG1、UNG2_1、UNG2_2、UNG3_1、UNG3_2、UNG4_1、UNG4_2、UNG5、UNG6、UNG7_1、UNG7_2、UNG7_3、UNG8</span><span class="sxs-lookup"><span data-stu-id="4b536-132">UNG1, UNG2_1, UNG2_2, UNG3_1, UNG3_2, UNG4_1, UNG4_2, UNG5, UNG6, UNG7_1, UNG7_2, UNG7_3, UNG8</span></span>|  
|<span data-ttu-id="4b536-133">訊息標頭 (UNH)</span><span class="sxs-lookup"><span data-stu-id="4b536-133">Message Header (UNH)</span></span>|<span data-ttu-id="4b536-134">UNH1</span><span class="sxs-lookup"><span data-stu-id="4b536-134">UNH1</span></span>|  
  
 <span data-ttu-id="4b536-135">因為 UNA 和 UNG EDIFACT 區段是選擇性的所以 GenerateUNA 和 GenerateUNG 屬性可用來判斷這些標頭是否產生，而不論**套用 UNA 區段**協議設定。</span><span class="sxs-lookup"><span data-stu-id="4b536-135">Since the UNA and UNG EDIFACT segments are optional, the GenerateUNA and GenerateUNG properties can be used to determine if these headers are generated, regardless of the **Apply UNA segment** agreement setting.</span></span> <span data-ttu-id="4b536-136">下列表格顯示導致產生這些區段的值：</span><span class="sxs-lookup"><span data-stu-id="4b536-136">The following tables show the values that result in generation of these segments:</span></span>  
  
|<span data-ttu-id="4b536-137">GenerateUNA 內容屬性</span><span class="sxs-lookup"><span data-stu-id="4b536-137">GenerateUNA context property</span></span>|<span data-ttu-id="4b536-138">套用 UNA 區段協議設定</span><span class="sxs-lookup"><span data-stu-id="4b536-138">Apply UNA segment agreement setting</span></span>|<span data-ttu-id="4b536-139">引擎行為</span><span class="sxs-lookup"><span data-stu-id="4b536-139">Engine behavior</span></span>|  
|----------------------------------|-----------------------------------------|---------------------|  
|<span data-ttu-id="4b536-140">TRUE</span><span class="sxs-lookup"><span data-stu-id="4b536-140">TRUE</span></span>|<span data-ttu-id="4b536-141">CHECKED</span><span class="sxs-lookup"><span data-stu-id="4b536-141">CHECKED</span></span>|<span data-ttu-id="4b536-142">產生 UNA</span><span class="sxs-lookup"><span data-stu-id="4b536-142">Generate UNA</span></span>|  
|<span data-ttu-id="4b536-143">TRUE</span><span class="sxs-lookup"><span data-stu-id="4b536-143">TRUE</span></span>|<span data-ttu-id="4b536-144">UNCHECKED</span><span class="sxs-lookup"><span data-stu-id="4b536-144">UNCHECKED</span></span>|<span data-ttu-id="4b536-145">產生 UNA</span><span class="sxs-lookup"><span data-stu-id="4b536-145">Generate UNA</span></span>|  
|<span data-ttu-id="4b536-146">FALSE</span><span class="sxs-lookup"><span data-stu-id="4b536-146">FALSE</span></span>|<span data-ttu-id="4b536-147">CHECKED</span><span class="sxs-lookup"><span data-stu-id="4b536-147">CHECKED</span></span>|<span data-ttu-id="4b536-148">不產生 UNA</span><span class="sxs-lookup"><span data-stu-id="4b536-148">Do not generate UNA</span></span>|  
|<span data-ttu-id="4b536-149">FALSE</span><span class="sxs-lookup"><span data-stu-id="4b536-149">FALSE</span></span>|<span data-ttu-id="4b536-150">UNCHECKED</span><span class="sxs-lookup"><span data-stu-id="4b536-150">UNCHECKED</span></span>|<span data-ttu-id="4b536-151">不產生 UNA</span><span class="sxs-lookup"><span data-stu-id="4b536-151">Do not generate UNA</span></span>|  
|<span data-ttu-id="4b536-152">不存在 (OverrideEDIHeader 為 false)</span><span class="sxs-lookup"><span data-stu-id="4b536-152">Not present (OverrideEDIHeader is false)</span></span>|<span data-ttu-id="4b536-153">CHECKED</span><span class="sxs-lookup"><span data-stu-id="4b536-153">CHECKED</span></span>|<span data-ttu-id="4b536-154">產生 UNA</span><span class="sxs-lookup"><span data-stu-id="4b536-154">Generate UNA</span></span>|  
|<span data-ttu-id="4b536-155">不存在 (OverrideEDIHeader 為 false)</span><span class="sxs-lookup"><span data-stu-id="4b536-155">Not present (OverrideEDIHeader is false)</span></span>|<span data-ttu-id="4b536-156">UNCHECKED</span><span class="sxs-lookup"><span data-stu-id="4b536-156">UNCHECKED</span></span>|<span data-ttu-id="4b536-157">不產生 UNA</span><span class="sxs-lookup"><span data-stu-id="4b536-157">Do not generate UNA</span></span>|  
  
|<span data-ttu-id="4b536-158">GenerateUNG 內容屬性</span><span class="sxs-lookup"><span data-stu-id="4b536-158">GenerateUNG context property</span></span>|<span data-ttu-id="4b536-159">套用 UNG 區段協議設定</span><span class="sxs-lookup"><span data-stu-id="4b536-159">Apply UNG segments agreement setting</span></span>|<span data-ttu-id="4b536-160">引擎行為</span><span class="sxs-lookup"><span data-stu-id="4b536-160">Engine behavior</span></span>|  
|----------------------------------|------------------------------------------|---------------------|  
|<span data-ttu-id="4b536-161">TRUE</span><span class="sxs-lookup"><span data-stu-id="4b536-161">TRUE</span></span>|<span data-ttu-id="4b536-162">CHECKED</span><span class="sxs-lookup"><span data-stu-id="4b536-162">CHECKED</span></span>|<span data-ttu-id="4b536-163">產生 UNG</span><span class="sxs-lookup"><span data-stu-id="4b536-163">Generate UNG</span></span>|  
|<span data-ttu-id="4b536-164">TRUE</span><span class="sxs-lookup"><span data-stu-id="4b536-164">TRUE</span></span>|<span data-ttu-id="4b536-165">UNCHECKED</span><span class="sxs-lookup"><span data-stu-id="4b536-165">UNCHECKED</span></span>|<span data-ttu-id="4b536-166">產生 UNG</span><span class="sxs-lookup"><span data-stu-id="4b536-166">Generate UNG</span></span>|  
|<span data-ttu-id="4b536-167">FALSE</span><span class="sxs-lookup"><span data-stu-id="4b536-167">FALSE</span></span>|<span data-ttu-id="4b536-168">CHECKED</span><span class="sxs-lookup"><span data-stu-id="4b536-168">CHECKED</span></span>|<span data-ttu-id="4b536-169">不產生 UNG</span><span class="sxs-lookup"><span data-stu-id="4b536-169">Do not generate UNG</span></span>|  
|<span data-ttu-id="4b536-170">FALSE</span><span class="sxs-lookup"><span data-stu-id="4b536-170">FALSE</span></span>|<span data-ttu-id="4b536-171">UNCHECKED</span><span class="sxs-lookup"><span data-stu-id="4b536-171">UNCHECKED</span></span>|<span data-ttu-id="4b536-172">不產生 UNG</span><span class="sxs-lookup"><span data-stu-id="4b536-172">Do not generate UNG</span></span>|  
|<span data-ttu-id="4b536-173">不存在 (OverrideEDIHeader 為 false)</span><span class="sxs-lookup"><span data-stu-id="4b536-173">Not present (OverrideEDIHeader is false)</span></span>|<span data-ttu-id="4b536-174">CHECKED</span><span class="sxs-lookup"><span data-stu-id="4b536-174">CHECKED</span></span>|<span data-ttu-id="4b536-175">產生 UNG</span><span class="sxs-lookup"><span data-stu-id="4b536-175">Generate UNG</span></span>|  
|<span data-ttu-id="4b536-176">不存在 (OverrideEDIHeader 為 false)</span><span class="sxs-lookup"><span data-stu-id="4b536-176">Not present (OverrideEDIHeader is false)</span></span>|<span data-ttu-id="4b536-177">UNCHECKED</span><span class="sxs-lookup"><span data-stu-id="4b536-177">UNCHECKED</span></span>|<span data-ttu-id="4b536-178">不產生 UNG</span><span class="sxs-lookup"><span data-stu-id="4b536-178">Do not generate UNG</span></span>|  
  
### <a name="group-envelopes"></a><span data-ttu-id="4b536-179">群組信封</span><span class="sxs-lookup"><span data-stu-id="4b536-179">Group envelopes</span></span>  
 <span data-ttu-id="4b536-180">群組信封會提出一項特殊挑戰，因為交換可能會存在多個群組。</span><span class="sxs-lookup"><span data-stu-id="4b536-180">Group envelopes present a special challenge, as the interchange can have more than one group present.</span></span> <span data-ttu-id="4b536-181">為了處理這項挑戰，EDI 傳送管線可以將信封套用至交換中的所有群組，或將信封套用至交換中的唯一群組。</span><span class="sxs-lookup"><span data-stu-id="4b536-181">To address this, the EDI send pipeline can either apply the envelope to all groups in the interchange, or apply the envelope to the only group in the interchange.</span></span>  
  
 <span data-ttu-id="4b536-182">若為單一交易，可以覆寫所有 GS 或 UNG 欄位。若為批次交換，就只能覆寫下列欄位：</span><span class="sxs-lookup"><span data-stu-id="4b536-182">For single transactions, all GS or UNG fields can be overridden, for batch interchanges only the following fields can be overridden:</span></span>  
  
-   <span data-ttu-id="4b536-183">GS04</span><span class="sxs-lookup"><span data-stu-id="4b536-183">GS04</span></span>  
  
-   <span data-ttu-id="4b536-184">GS05</span><span class="sxs-lookup"><span data-stu-id="4b536-184">GS05</span></span>  
  
-   <span data-ttu-id="4b536-185">UNG4_1</span><span class="sxs-lookup"><span data-stu-id="4b536-185">UNG4_1</span></span>  
  
-   <span data-ttu-id="4b536-186">UNG4_2</span><span class="sxs-lookup"><span data-stu-id="4b536-186">UNG4_2</span></span>  
  
### <a name="batching"></a><span data-ttu-id="4b536-187">批次處理</span><span class="sxs-lookup"><span data-stu-id="4b536-187">Batching</span></span>  
 <span data-ttu-id="4b536-188">覆寫批次訊息的交易集控制編號是由批次處理協調流程所處理。</span><span class="sxs-lookup"><span data-stu-id="4b536-188">Overriding the transaction set control number for batched messages is handled by the Batching orchestration.</span></span> <span data-ttu-id="4b536-189">下列屬性可以寫入動作會覆寫進行批次處理的任何訊息內容的交易集控制編號：</span><span class="sxs-lookup"><span data-stu-id="4b536-189">The following properties can be written to the context of any message that will be batched to override the transaction set control number:</span></span>  
  
-   <span data-ttu-id="4b536-190">ST02 (適用於 X12 訊息)</span><span class="sxs-lookup"><span data-stu-id="4b536-190">ST02 (for X12 messages)</span></span>  
  
-   <span data-ttu-id="4b536-191">UNH1 (適用於 EDIFACT 訊息)</span><span class="sxs-lookup"><span data-stu-id="4b536-191">UNH1 (For EDIFACT messages</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b536-192">如果多個內送訊息包含相同群組中的相同控制編號，系統將擱置含有重複編號的訊息。</span><span class="sxs-lookup"><span data-stu-id="4b536-192">If multiple incoming messages contain the same control number in the same group, messages with duplicate numbers will be suspended.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4b536-193">請勿針對即將進行批次處理的訊息升級 EdiOverride 內容屬性 ISA、UNA、GS 或 UNG。</span><span class="sxs-lookup"><span data-stu-id="4b536-193">Do not promote the EdiOverride context properties ISA, UNA, GS, or UNG for messages that are to be batched.</span></span> <span data-ttu-id="4b536-194">如果您需要覆寫這些屬性，請先針對批次協調流程的輸出訊息升級這些屬性，然後再傳送至 EDI 傳送管線。</span><span class="sxs-lookup"><span data-stu-id="4b536-194">If you need to override these properties, promote them on the output message of the batch orchestration before sending to the EDI send pipeline.</span></span>  
  
### <a name="delimiter-collision"></a><span data-ttu-id="4b536-195">分隔符號衝突</span><span class="sxs-lookup"><span data-stu-id="4b536-195">Delimiter collision</span></span>  
 <span data-ttu-id="4b536-196">每個欄位的分隔符號 (例如 UNA 標頭) 都必須包含唯一值。</span><span class="sxs-lookup"><span data-stu-id="4b536-196">Delimiters, such as the UNA headers, must contain a unique value for each field.</span></span> <span data-ttu-id="4b536-197">覆寫分隔符號值 (例如 UNA 標頭) 時，您必須確定每個分隔符號值不僅在您所覆寫的值內部是唯一的，而且在根據協議或後援協議設定所使用的任何分隔符號值之間也是唯一的。</span><span class="sxs-lookup"><span data-stu-id="4b536-197">When overriding delimiter values, such as the UNA headers, you must ensure that each delimiter value is unique not only within the values you override, but also among any delimiter values used from the agreement or fallback agreement settings.</span></span>  
  
 <span data-ttu-id="4b536-198">例如，如果您覆寫了 UNA1、UNA2 和 UNA4，而且 UNA3、UNA5、UNA6 和 UNA6Suffix 來自協議屬性，則每個屬性都必須包含唯一值 (相較於其他屬性而言)。</span><span class="sxs-lookup"><span data-stu-id="4b536-198">For example, if you override UNA1, UNA2, and UNA4, and UNA3, UNA5, UNA6 and UNA6Suffix come from agreement properties, each property must contain a unique value compared to the others.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b536-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4b536-199">See Also</span></span>  
 [<span data-ttu-id="4b536-200">BizTalk Server 如何傳送 EDI 訊息</span><span class="sxs-lookup"><span data-stu-id="4b536-200">How BizTalk Server Sends EDI Messages</span></span>](../core/how-biztalk-server-sends-edi-messages.md)