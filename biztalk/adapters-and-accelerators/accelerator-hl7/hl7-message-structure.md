---
title: HL7 訊息結構 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, segments
- messages, fields
- trigger events
- messages, trigger events
- segments, messages
- messages, message structure
ms.assetid: 4dbef56d-97ae-466d-bc8a-dc96c40896f6
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a298a21b7df2605cdb8dc181898808c94cf40b33
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996951"
---
# <a name="hl7-message-structure"></a><span data-ttu-id="0db3e-102">HL7 訊息結構</span><span class="sxs-lookup"><span data-stu-id="0db3e-102">HL7 Message Structure</span></span>
<span data-ttu-id="0db3e-103">HL7 訊息是觸發程序事件相關聯的階層式結構。</span><span class="sxs-lookup"><span data-stu-id="0db3e-103">An HL7 message is a hierarchical structure associated with a trigger event.</span></span> <span data-ttu-id="0db3e-104">標準 HL7 定義 」 （，），會建立資料流各系統間需要美國衛生保健真實世界中的事件 」 觸發程序事件。</span><span class="sxs-lookup"><span data-stu-id="0db3e-104">The HL7 standard defines trigger event as "an event in the real world of health care (that) creates the need for data to flow among systems".</span></span> <span data-ttu-id="0db3e-105">每個觸發程序事件是與定義的訊息需要支援觸發程序事件的資料類型的抽象訊息相關聯。</span><span class="sxs-lookup"><span data-stu-id="0db3e-105">Each trigger event is associated with an abstract message that defines the type of data that the message needs to support the trigger event.</span></span> <span data-ttu-id="0db3e-106">抽象訊息區段的集合，而且包含重複的這些區段包含的規則。</span><span class="sxs-lookup"><span data-stu-id="0db3e-106">The abstract message is a collection of segments, and includes the rules of repetition and inclusion for those segments.</span></span> <span data-ttu-id="0db3e-107">下表顯示與觸發程序事件 A04 – 註冊病患相關聯的抽象訊息的範例。</span><span class="sxs-lookup"><span data-stu-id="0db3e-107">The following table shows an example of an abstract message associated with the trigger event A04 – Register Patient.</span></span>  
  
|<span data-ttu-id="0db3e-108">觸發程序事件</span><span class="sxs-lookup"><span data-stu-id="0db3e-108">Trigger event</span></span>|<span data-ttu-id="0db3e-109">抽象訊息</span><span class="sxs-lookup"><span data-stu-id="0db3e-109">Abstract message</span></span>|  
|-------------------|----------------------|  
|<span data-ttu-id="0db3e-110">ADT ^ A04 ^ ADT_A01</span><span class="sxs-lookup"><span data-stu-id="0db3e-110">ADT^A04^ADT_A01</span></span>|<span data-ttu-id="0db3e-111">許可、 放電和傳輸</span><span class="sxs-lookup"><span data-stu-id="0db3e-111">Admissions, Discharge, and Transfer</span></span>|  
|<span data-ttu-id="0db3e-112">MSH</span><span class="sxs-lookup"><span data-stu-id="0db3e-112">MSH</span></span>|<span data-ttu-id="0db3e-113">訊息標頭</span><span class="sxs-lookup"><span data-stu-id="0db3e-113">Message Header</span></span>|  
|<span data-ttu-id="0db3e-114">EVN</span><span class="sxs-lookup"><span data-stu-id="0db3e-114">EVN</span></span>|<span data-ttu-id="0db3e-115">事件類型</span><span class="sxs-lookup"><span data-stu-id="0db3e-115">Event Type</span></span>|  
|<span data-ttu-id="0db3e-116">PID</span><span class="sxs-lookup"><span data-stu-id="0db3e-116">PID</span></span>|<span data-ttu-id="0db3e-117">病患識別碼</span><span class="sxs-lookup"><span data-stu-id="0db3e-117">Patient Identification</span></span>|  
|<span data-ttu-id="0db3e-118">[PD1]</span><span class="sxs-lookup"><span data-stu-id="0db3e-118">[  PD1  ]</span></span>|<span data-ttu-id="0db3e-119">其他的人口統計資料</span><span class="sxs-lookup"><span data-stu-id="0db3e-119">Additional Demographics</span></span>|  
|<span data-ttu-id="0db3e-120">[{ROL}]</span><span class="sxs-lookup"><span data-stu-id="0db3e-120">[{ ROL }]</span></span>|<span data-ttu-id="0db3e-121">角色</span><span class="sxs-lookup"><span data-stu-id="0db3e-121">Role</span></span>|  
|<span data-ttu-id="0db3e-122">[{NK1}]</span><span class="sxs-lookup"><span data-stu-id="0db3e-122">[{ NK1 }]</span></span>|<span data-ttu-id="0db3e-123">家族相互交換 / 相關聯的合作對象的下一步</span><span class="sxs-lookup"><span data-stu-id="0db3e-123">Next of Kin / Associated Parties</span></span>|  
|<span data-ttu-id="0db3e-124">PV1</span><span class="sxs-lookup"><span data-stu-id="0db3e-124">PV1</span></span>|<span data-ttu-id="0db3e-125">瀏覽病患</span><span class="sxs-lookup"><span data-stu-id="0db3e-125">Patient Visit</span></span>|  
|<span data-ttu-id="0db3e-126">[PV2]</span><span class="sxs-lookup"><span data-stu-id="0db3e-126">[  PV2  ]</span></span>|<span data-ttu-id="0db3e-127">病患造訪-其他資訊</span><span class="sxs-lookup"><span data-stu-id="0db3e-127">Patient Visit - Additional Information</span></span>|  
|<span data-ttu-id="0db3e-128">[{ROL}]</span><span class="sxs-lookup"><span data-stu-id="0db3e-128">[{ ROL }]</span></span>|<span data-ttu-id="0db3e-129">角色</span><span class="sxs-lookup"><span data-stu-id="0db3e-129">Role</span></span>|  
|<span data-ttu-id="0db3e-130">[{DB1}]</span><span class="sxs-lookup"><span data-stu-id="0db3e-130">[{ DB1 }]</span></span>|<span data-ttu-id="0db3e-131">傷殘保險資訊</span><span class="sxs-lookup"><span data-stu-id="0db3e-131">Disability Information</span></span>|  
|<span data-ttu-id="0db3e-132">[{OBX}]</span><span class="sxs-lookup"><span data-stu-id="0db3e-132">[{ OBX }]</span></span>|<span data-ttu-id="0db3e-133">觀察/結果</span><span class="sxs-lookup"><span data-stu-id="0db3e-133">Observation/Result</span></span>|  
|<span data-ttu-id="0db3e-134">[{AL1}]</span><span class="sxs-lookup"><span data-stu-id="0db3e-134">[{ AL1 }]</span></span>|<span data-ttu-id="0db3e-135">Allergy 資訊</span><span class="sxs-lookup"><span data-stu-id="0db3e-135">Allergy Information</span></span>|  
|<span data-ttu-id="0db3e-136">[{DG1}]</span><span class="sxs-lookup"><span data-stu-id="0db3e-136">[{ DG1 }]</span></span>|<span data-ttu-id="0db3e-137">診斷資訊</span><span class="sxs-lookup"><span data-stu-id="0db3e-137">Diagnosis Information</span></span>|  
|<span data-ttu-id="0db3e-138">[DRG]</span><span class="sxs-lookup"><span data-stu-id="0db3e-138">[  DRG  ]</span></span>|<span data-ttu-id="0db3e-139">診斷相關的群組</span><span class="sxs-lookup"><span data-stu-id="0db3e-139">Diagnosis Related Group</span></span>|  
|<span data-ttu-id="0db3e-140">[{</span><span class="sxs-lookup"><span data-stu-id="0db3e-140">[{</span></span>||  
|<span data-ttu-id="0db3e-141">PR1</span><span class="sxs-lookup"><span data-stu-id="0db3e-141">PR1</span></span>|<span data-ttu-id="0db3e-142">程序</span><span class="sxs-lookup"><span data-stu-id="0db3e-142">Procedures</span></span>|  
|<span data-ttu-id="0db3e-143">[{ROL}]</span><span class="sxs-lookup"><span data-stu-id="0db3e-143">[{ ROL }]</span></span>|<span data-ttu-id="0db3e-144">角色</span><span class="sxs-lookup"><span data-stu-id="0db3e-144">Role</span></span>|  
|<span data-ttu-id="0db3e-145">}]</span><span class="sxs-lookup"><span data-stu-id="0db3e-145">}]</span></span>||  
|<span data-ttu-id="0db3e-146">[{GT1}]</span><span class="sxs-lookup"><span data-stu-id="0db3e-146">[{ GT1 } ]</span></span>|<span data-ttu-id="0db3e-147">保證人角色</span><span class="sxs-lookup"><span data-stu-id="0db3e-147">Guarantor</span></span>|  
|<span data-ttu-id="0db3e-148">[{</span><span class="sxs-lookup"><span data-stu-id="0db3e-148">[{</span></span>||  
|<span data-ttu-id="0db3e-149">入 1</span><span class="sxs-lookup"><span data-stu-id="0db3e-149">IN1</span></span>|<span data-ttu-id="0db3e-150">Insurance</span><span class="sxs-lookup"><span data-stu-id="0db3e-150">Insurance</span></span>|  
|<span data-ttu-id="0db3e-151">[入 2]</span><span class="sxs-lookup"><span data-stu-id="0db3e-151">[  IN2 ]</span></span>|<span data-ttu-id="0db3e-152">保險的其他資訊</span><span class="sxs-lookup"><span data-stu-id="0db3e-152">Insurance Additional Information</span></span>|  
|<span data-ttu-id="0db3e-153">[{入 3}]</span><span class="sxs-lookup"><span data-stu-id="0db3e-153">[{ IN3 }]</span></span>|<span data-ttu-id="0db3e-154">保險的其他資訊的憑證。</span><span class="sxs-lookup"><span data-stu-id="0db3e-154">Insurance Additional Information - Cert.</span></span>|  
|<span data-ttu-id="0db3e-155">[{ROL}]</span><span class="sxs-lookup"><span data-stu-id="0db3e-155">[{ ROL }]</span></span>|<span data-ttu-id="0db3e-156">角色</span><span class="sxs-lookup"><span data-stu-id="0db3e-156">Role</span></span>|  
|<span data-ttu-id="0db3e-157">}]</span><span class="sxs-lookup"><span data-stu-id="0db3e-157">}]</span></span>||  
|<span data-ttu-id="0db3e-158">[帳戶]</span><span class="sxs-lookup"><span data-stu-id="0db3e-158">[  ACC  ]</span></span>|<span data-ttu-id="0db3e-159">意外的資訊</span><span class="sxs-lookup"><span data-stu-id="0db3e-159">Accident Information</span></span>|  
|<span data-ttu-id="0db3e-160">[UB1]</span><span class="sxs-lookup"><span data-stu-id="0db3e-160">[  UB1  ]</span></span>|<span data-ttu-id="0db3e-161">通用的帳單資訊</span><span class="sxs-lookup"><span data-stu-id="0db3e-161">Universal Bill Information</span></span>|  
|<span data-ttu-id="0db3e-162">[UB2]</span><span class="sxs-lookup"><span data-stu-id="0db3e-162">[  UB2  ]</span></span>|<span data-ttu-id="0db3e-163">通用的帳單 92年資訊</span><span class="sxs-lookup"><span data-stu-id="0db3e-163">Universal Bill 92 Information</span></span>|  
|<span data-ttu-id="0db3e-164">[PDA]</span><span class="sxs-lookup"><span data-stu-id="0db3e-164">[  PDA  ]</span></span>|<span data-ttu-id="0db3e-165">病患死了 Autopsy</span><span class="sxs-lookup"><span data-stu-id="0db3e-165">Patient Death and Autopsy</span></span>|  
  
 <span data-ttu-id="0db3e-166">上述在方括號"["，"]"表示區段或群組的區段是選擇性的在大括號時"{"，"}"表示的區段或重複的區段群組。</span><span class="sxs-lookup"><span data-stu-id="0db3e-166">The brackets above "[", "]" indicate that a segment or group of segments is optional, while braces "{", "}" indicate the segment or group of segments repeat.</span></span>  
  
 <span data-ttu-id="0db3e-167">區段是的群組欄位的每一個都符合特定資料型別。</span><span class="sxs-lookup"><span data-stu-id="0db3e-167">A segment is a group of fields each of which conforms to a particular data type.</span></span> <span data-ttu-id="0db3e-168">欄位可以有一個簡單或複雜的結構。</span><span class="sxs-lookup"><span data-stu-id="0db3e-168">Fields can have a simple or complex structure.</span></span> <span data-ttu-id="0db3e-169">根據其資料型別定義中定義的規則的元件所組成。</span><span class="sxs-lookup"><span data-stu-id="0db3e-169">They consist of components according to the rules defined in their data-type definition.</span></span> <span data-ttu-id="0db3e-170">為了支援更複雜的資料類型，某些元件可能包含子元件。</span><span class="sxs-lookup"><span data-stu-id="0db3e-170">In order to support the more complex data types, some components may consist of subcomponents.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0db3e-171">HL7 訊息編碼會使用指定的分隔符號的事實會限制開發人員能夠帶來了新的細分資料的方式。</span><span class="sxs-lookup"><span data-stu-id="0db3e-171">The fact that HL7 message encoding uses specified delimiters limits the ability of a developer to introduce new ways of subdividing the data.</span></span> <span data-ttu-id="0db3e-172">由於這項作業需要創造新的分隔符號類型時，則可以是任何子子元件。</span><span class="sxs-lookup"><span data-stu-id="0db3e-172">There can be no sub-subcomponent, since this would require invention of a new delimiter type.</span></span>  
  
 <span data-ttu-id="0db3e-173">第一個 HL7 規格並不會定義抽象的訊息。</span><span class="sxs-lookup"><span data-stu-id="0db3e-173">The first HL7 specifications did not define the abstract message.</span></span> <span data-ttu-id="0db3e-174">抽象訊息是區段與觸發程序事件相關聯的模式。</span><span class="sxs-lookup"><span data-stu-id="0db3e-174">The abstract message is the pattern of segments associated with a trigger event.</span></span> <span data-ttu-id="0db3e-175">同樣地，HL7 訊息包含的區段放在一起，重複或區段群組的集合。</span><span class="sxs-lookup"><span data-stu-id="0db3e-175">Similarly, HL7 messages contain collections of segments that repeat together, or segment groups.</span></span> <span data-ttu-id="0db3e-176">第一個 HL7 規格並不會定義區段群組。</span><span class="sxs-lookup"><span data-stu-id="0db3e-176">The first HL7 specifications did not define segment groups.</span></span> <span data-ttu-id="0db3e-177">V2.3.1，從繼續在後續版本中，此變更的原因需要支援 XML 編碼方式。</span><span class="sxs-lookup"><span data-stu-id="0db3e-177">Starting with V2.3.1, and continuing in the subsequent versions, this changed due to the need to support XML encoding.</span></span> <span data-ttu-id="0db3e-178">例如，觸發程序事件上表中，訊息結構的名稱是"ADT_A01 」。</span><span class="sxs-lookup"><span data-stu-id="0db3e-178">For example, in the Trigger Event table above, the name of the message structure is "ADT_A01".</span></span> <span data-ttu-id="0db3e-179">這是用來支援管理 A01 – 承認病患的區段相同模式。</span><span class="sxs-lookup"><span data-stu-id="0db3e-179">This is the same pattern of segments used to support A01 – Admit Patient.</span></span> <span data-ttu-id="0db3e-180">為了方便起見，訊息結構的名稱會對應到 （依據 HL7 文件中的位置） 的第一個觸發程序會使用它們的事件。</span><span class="sxs-lookup"><span data-stu-id="0db3e-180">For convenience, the names of message structures correspond to the first (in terms of placement within the HL7 document) trigger event that uses them.</span></span> <span data-ttu-id="0db3e-181">同樣地，觸發程序事件上表開頭入 1，包括入 2、 入 3 和 ROL 中的區段群組重複做為群組。</span><span class="sxs-lookup"><span data-stu-id="0db3e-181">Similarly, the group of segments in the Trigger Event table above that starts with IN1, including IN2, IN3, and ROL, repeats as a group.</span></span> <span data-ttu-id="0db3e-182">它的名稱，開頭為 2.5 版是 「 保險 」 的群組。</span><span class="sxs-lookup"><span data-stu-id="0db3e-182">Its name—starting with Version 2.5 is "Insurance" group.</span></span>  
  
 <span data-ttu-id="0db3e-183">第 2 版間的版本相容性規則支援介面的發展需要標準的後續版本不包含結構使先前的版本。</span><span class="sxs-lookup"><span data-stu-id="0db3e-183">In Version 2, the inter-version compatibility rules support evolution of interfaces by requiring that subsequent versions of the standard not include structures that invalidate prior versions.</span></span> <span data-ttu-id="0db3e-184">這需要您沒有移除觸發程序事件，且您執行使用觸發程序事件針對不同用途，或使用不同的抽象訊息比原本預期。</span><span class="sxs-lookup"><span data-stu-id="0db3e-184">This requires that you do not remove a trigger event and that you do not use a trigger event for a different purpose or with a different abstract message than originally intended.</span></span> <span data-ttu-id="0db3e-185">抽象訊息，這表示您無法移除訊息中的區段，也可以您讓選擇性的必要區段，或重複區段不重複。</span><span class="sxs-lookup"><span data-stu-id="0db3e-185">For abstract messages, this implies that you cannot remove a segment from a message, nor can you make a mandatory segment optional or a repeating segment non-repeating.</span></span> <span data-ttu-id="0db3e-186">如果您新增的區段時，您必須進行訊息結尾處，或在訊息中重複群組結尾處。</span><span class="sxs-lookup"><span data-stu-id="0db3e-186">If you add a segment, you must do so at the end of a message or at the end of a repeating group within a message.</span></span>  
  
 <span data-ttu-id="0db3e-187">Microsoft BizTalk Accelerator for HL7 的下列函式 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 支援這些需求：</span><span class="sxs-lookup"><span data-stu-id="0db3e-187">The following functions of Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) support these requirements:</span></span>  
  
-   <span data-ttu-id="0db3e-188">支援的所有觸發程序事件與訊息結構 v2.1 將分別從開始，一直持續到 V2.5。</span><span class="sxs-lookup"><span data-stu-id="0db3e-188">Support of all trigger events and message structures starting with V2.1 and continuing through V2.5.</span></span>  
  
-   <span data-ttu-id="0db3e-189">透過加入區段和量身訂做區段選擇性和重複的本地化的支援。</span><span class="sxs-lookup"><span data-stu-id="0db3e-189">Support of localization through adding segments and tailoring segment optionally and repetition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0db3e-190">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0db3e-190">See Also</span></span>  
 <span data-ttu-id="0db3e-191">[處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="0db3e-191">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 <span data-ttu-id="0db3e-192">[訊息處理](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span><span class="sxs-lookup"><span data-stu-id="0db3e-192">[Message Processing](../../adapters-and-accelerators/accelerator-hl7/message-processing.md) </span></span>  
 [<span data-ttu-id="0db3e-193">使用 HL7 2.X 結構描述</span><span class="sxs-lookup"><span data-stu-id="0db3e-193">Using HL7 2.X Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)