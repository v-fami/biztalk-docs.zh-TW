---
title: "交叉驗證欄位區段 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e757b4f-71fe-44d5-9580-c8b1c8eb2366
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eafa1831d6f99ef925a79ab7276caea005c2380f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="cross-field-segment-validation"></a><span data-ttu-id="e3589-102">交叉驗證欄位區段</span><span class="sxs-lookup"><span data-stu-id="e3589-102">Cross Field-Segment Validation</span></span>
<span data-ttu-id="e3589-103">EDI 接收管線和 EDI 傳送管線，可以對 X12 編碼訊息中的交易集資料元素執行欄位/區段交互驗證。</span><span class="sxs-lookup"><span data-stu-id="e3589-103">The EDI receive pipeline and EDI send pipeline can perform cross field/segment validation on transaction-set data elements in X12-encoded messages.</span></span> <span data-ttu-id="e3589-104">這種驗證就稱為 X12 中的關係條件。</span><span class="sxs-lookup"><span data-stu-id="e3589-104">This validation is called relational conditions in X12.</span></span> <span data-ttu-id="e3589-105">欄位交互驗證是以註解表示，因此與 EDI 驗證相關。</span><span class="sxs-lookup"><span data-stu-id="e3589-105">Cross field validation is expressed through annotations, and as a result, it is related to EDI validation.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e3589-106"> 不支援 EDIFACT 相依性規則。</span><span class="sxs-lookup"><span data-stu-id="e3589-106"> does not support EDIFACT dependency rules.</span></span>  
  
 <span data-ttu-id="e3589-107">對於 X12 編碼訊息，您可以將訊息結構描述中的 X12ConditionDesignator_Check 旗標設為 "Yes"，便可啟用這項驗證功能。</span><span class="sxs-lookup"><span data-stu-id="e3589-107">For X12-encoded messages, you enable this validation by setting the X12ConditionDesignator_Check flag in the message schema to "Yes".</span></span> <span data-ttu-id="e3589-108">這個旗標位在結構描述 “appinfo” 區段的註解中。</span><span class="sxs-lookup"><span data-stu-id="e3589-108">This flag is in an annotation in the “appinfo” section of the schema.</span></span> <span data-ttu-id="e3589-109">這個旗標預設是設為 "No"，表示 X12 結構描述的欄位/區段交互驗證尚未啟用。</span><span class="sxs-lookup"><span data-stu-id="e3589-109">By default this flag is set to "No" and cross field\segment validation is not enabled for X12 schemas.</span></span> <span data-ttu-id="e3589-110">若是 HIPAA 結構描述，預設是設為 “Yes”，表示欄位/區段交互驗證已啟用。</span><span class="sxs-lookup"><span data-stu-id="e3589-110">For HIPAA schemas the default is set to “Yes” and cross field\segment validation is enabled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3589-111">欄位/區段交互驗證完全不同於 EDI 資料元素驗證和擴充 (BTS-XSD) 驗證。</span><span class="sxs-lookup"><span data-stu-id="e3589-111">Cross-field/segment validation is distinct from both EDI data element validation and extended (BTS-XSD) validation.</span></span> <span data-ttu-id="e3589-112">EDI 資料元素驗證和/或擴充驗證可以在不執行欄位/區段交互驗證情況下執行，而欄位/區段交互驗證可以在不執行 EDI 資料元素驗證和/或擴充驗證的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="e3589-112">EDI data element validation and/or extended validation can be performed without performing cross-field/segment validation, and cross-field/segment validation can be performed without performing EDI data element validation and/or extended validation.</span></span>  
  
 <span data-ttu-id="e3589-113">X12 的選用性包括「強制性」(M)、「選擇性」(O) 和「關係性」(R) (欄位交互驗證)。</span><span class="sxs-lookup"><span data-stu-id="e3589-113">Optionality in X12 consists of Mandatory (M), Optional (O), and Relational (R) (cross field validation).</span></span> <span data-ttu-id="e3589-114">若是選擇「強制性」，表示至少要指定綜合類型中的一個元件資料元素做為值。</span><span class="sxs-lookup"><span data-stu-id="e3589-114">When the optionality is Mandatory, at least one component data element in composite types must be valued.</span></span>  
  
## <a name="x12-optionality"></a><span data-ttu-id="e3589-115">X12 選用性</span><span class="sxs-lookup"><span data-stu-id="e3589-115">X12 Optionality</span></span>  
 <span data-ttu-id="e3589-116">在 X12 中，關係性選用性的欄位/區段交互驗證包括列為結構描述中規則的一系列檢查。</span><span class="sxs-lookup"><span data-stu-id="e3589-116">In X12, cross field/segment validation for Relational optionality includes a series of checks listed in rules in the schema.</span></span> <span data-ttu-id="e3589-117">每個規則由下列項目中\<xs:annotation > 項目：</span><span class="sxs-lookup"><span data-stu-id="e3589-117">Each rule is identified by the following element in an \<xs:annotation> element:</span></span>  
  
```  
<b:Rule subjects="X12ConditionDesignatorX_<relational_condition>"…>  
```  
  
 <span data-ttu-id="e3589-118">在「規則」項目中的關係條件，表示該規則將驗證的內容。</span><span class="sxs-lookup"><span data-stu-id="e3589-118">The relational condition in the “Rule” element indicates what is being validated by that rule.</span></span> <span data-ttu-id="e3589-119">這個項目包括欄位交互驗證將針對其執行的主旨清單。</span><span class="sxs-lookup"><span data-stu-id="e3589-119">This element includes a list of subjects upon which the cross field validation is executed.</span></span> <span data-ttu-id="e3589-120">下面節點中含有這些主旨：</span><span class="sxs-lookup"><span data-stu-id="e3589-120">The subjects are included in the following node:</span></span>  
  
```  
<b:Subject name="<subject>"/>  
```  
  
 <span data-ttu-id="e3589-121">下表將列出這些 X12 關係條件：</span><span class="sxs-lookup"><span data-stu-id="e3589-121">The following table shows the X12 relational conditions:</span></span>  
  
|<span data-ttu-id="e3589-122">子類別</span><span class="sxs-lookup"><span data-stu-id="e3589-122">Subclassification</span></span>|<span data-ttu-id="e3589-123">關係條件</span><span class="sxs-lookup"><span data-stu-id="e3589-123">Relational Condition</span></span>|<span data-ttu-id="e3589-124">Description</span><span class="sxs-lookup"><span data-stu-id="e3589-124">Description</span></span>|  
|-----------------------|--------------------------|-----------------|  
|<span data-ttu-id="e3589-125">Paired</span><span class="sxs-lookup"><span data-stu-id="e3589-125">Paired</span></span>|<span data-ttu-id="e3589-126">X12ConditionDesignatorX_Paired</span><span class="sxs-lookup"><span data-stu-id="e3589-126">X12ConditionDesignatorX_Paired</span></span>|<span data-ttu-id="e3589-127">如果有存在指定於關係條件中的任何一個主旨項目，表示一定會存在所有已指定的主旨項目。</span><span class="sxs-lookup"><span data-stu-id="e3589-127">If any of the subject elements specified in the relational condition is present, then all of the subject elements specified must be present.</span></span>|  
|<span data-ttu-id="e3589-128">Required</span><span class="sxs-lookup"><span data-stu-id="e3589-128">Required</span></span>|<span data-ttu-id="e3589-129">X12ConditionDesignatorX_Required</span><span class="sxs-lookup"><span data-stu-id="e3589-129">X12ConditionDesignatorX_Required</span></span>|<span data-ttu-id="e3589-130">至少一定會存在一個已指定於關係條件中的主旨項目。</span><span class="sxs-lookup"><span data-stu-id="e3589-130">At least one of the subject elements specified in the relational condition must be present.</span></span>|  
|<span data-ttu-id="e3589-131">Exclusion</span><span class="sxs-lookup"><span data-stu-id="e3589-131">Exclusion</span></span>|<span data-ttu-id="e3589-132">X12ConditionDesignatorX_Exclusion</span><span class="sxs-lookup"><span data-stu-id="e3589-132">X12ConditionDesignatorX_Exclusion</span></span>|<span data-ttu-id="e3589-133">可能會存在最多一個已指定於關係條件中的主旨項目。</span><span class="sxs-lookup"><span data-stu-id="e3589-133">Not more than one of the subject elements specified in the relational condition may be present.</span></span>|  
|<span data-ttu-id="e3589-134">條件式</span><span class="sxs-lookup"><span data-stu-id="e3589-134">Conditional</span></span>|<span data-ttu-id="e3589-135">X12ConditionDesignatorX_Conditional</span><span class="sxs-lookup"><span data-stu-id="e3589-135">X12ConditionDesignatorX_Conditional</span></span>|<span data-ttu-id="e3589-136">如果有存在指定於關係條件中的第一個主旨項目，表示一定會存在其他所有的主旨項目。</span><span class="sxs-lookup"><span data-stu-id="e3589-136">If the first subject element specified in the relational condition is present, then all other subject elements must be present.</span></span> <span data-ttu-id="e3589-137">未指定成為此條件中第一個項目的任何或全部的項目，不需要等到第一個項目存在就可存在。</span><span class="sxs-lookup"><span data-stu-id="e3589-137">Any or all of the elements not specified as the first element in the condition may appear without requiring that the first element be present.</span></span> <span data-ttu-id="e3589-138">在此條件中的項目順序，不一定要與資料區段中的資料元素順序相同。</span><span class="sxs-lookup"><span data-stu-id="e3589-138">The order of the elements in the condition does not have to be the same as the order of the data elements in the data segments.</span></span>|  
|<span data-ttu-id="e3589-139">List Conditional</span><span class="sxs-lookup"><span data-stu-id="e3589-139">List Conditional</span></span>|<span data-ttu-id="e3589-140">X12ConditionDesignatorX_List Conditional</span><span class="sxs-lookup"><span data-stu-id="e3589-140">X12ConditionDesignatorX_List Conditional</span></span>|<span data-ttu-id="e3589-141">如果有存在指定於關係條件中的第一個主旨項目，表示至少會存在其餘的一個主旨項目。</span><span class="sxs-lookup"><span data-stu-id="e3589-141">If the first subject element specified in the relational condition is present, then at least one of the remaining subject elements must be present.</span></span> <span data-ttu-id="e3589-142">未指定成為此條件中第一個項目的任何或全部的項目，不需要等到第一個項目存在就可存在。</span><span class="sxs-lookup"><span data-stu-id="e3589-142">Any or all of the elements not specified as the first element in the condition may appear without requiring that the first element be present.</span></span> <span data-ttu-id="e3589-143">在此條件中的項目順序，不一定要與資料區段中的資料元素順序相同。</span><span class="sxs-lookup"><span data-stu-id="e3589-143">The order of the elements in the condition does not have to be the same as the order of the data elements in the data segments.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3589-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3589-144">See Also</span></span>  
 [<span data-ttu-id="e3589-145">EDI 訊息驗證</span><span class="sxs-lookup"><span data-stu-id="e3589-145">EDI Message Validation</span></span>](../core/edi-message-validation.md)