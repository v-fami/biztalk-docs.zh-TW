---
title: 攔截器 OnEvent 項目 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d684ac8e-61bc-410b-97a2-6fd3549e0d97
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6fb70b2536dbf5db5b0abc03bc194de154b4317
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257606"
---
# <a name="interceptor-onevent-element"></a><span data-ttu-id="a3f20-102">攔截器 OnEvent 項目</span><span class="sxs-lookup"><span data-stu-id="a3f20-102">Interceptor OnEvent Element</span></span>
<span data-ttu-id="a3f20-103">**OnEvent**元素描述一個對應至封入 BAM 活動的真實事件。</span><span class="sxs-lookup"><span data-stu-id="a3f20-103">The **OnEvent** element describes one real event that is mapped to the enclosing BAM activity.</span></span>  
  
## <a name="format"></a><span data-ttu-id="a3f20-104">格式</span><span class="sxs-lookup"><span data-stu-id="a3f20-104">Format</span></span>  
 <span data-ttu-id="a3f20-105">`OnEvent` 項目所包含的子項目，則會指定事件篩選條件、相互關聯識別碼、選擇性指定要更新的資料、參考資料和接續 Token。</span><span class="sxs-lookup"><span data-stu-id="a3f20-105">The `OnEvent` element contains child elements that specify an event filter, the correlation ID and optionally which data to update, reference data, and a continuation token.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3f20-106">屬性</span><span class="sxs-lookup"><span data-stu-id="a3f20-106">Attributes</span></span>  
  
|<span data-ttu-id="a3f20-107">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="a3f20-107">Attribute name</span></span>|<span data-ttu-id="a3f20-108">Description</span><span class="sxs-lookup"><span data-stu-id="a3f20-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="a3f20-109">名稱</span><span class="sxs-lookup"><span data-stu-id="a3f20-109">Name</span></span>|<span data-ttu-id="a3f20-110">此事件的使用者定義名稱。</span><span class="sxs-lookup"><span data-stu-id="a3f20-110">User-defined name for this event.</span></span>|  
|<span data-ttu-id="a3f20-111">Source</span><span class="sxs-lookup"><span data-stu-id="a3f20-111">Source</span></span>|<span data-ttu-id="a3f20-112">事件的名稱出現在來源**EventSource**項目。</span><span class="sxs-lookup"><span data-stu-id="a3f20-112">Name of the event source as it appears in an **EventSource** element.</span></span>|  
|<span data-ttu-id="a3f20-113">IsBegin</span><span class="sxs-lookup"><span data-stu-id="a3f20-113">IsBegin</span></span>|<span data-ttu-id="a3f20-114">布林值，表示事件是 (`true`) 否 (`false`) 為新 BAM 活動的開始。</span><span class="sxs-lookup"><span data-stu-id="a3f20-114">Boolean value indicating whether the event is the beginning of a new BAM activity (`true`) or not (`false`).</span></span>|  
|<span data-ttu-id="a3f20-115">IsEnd</span><span class="sxs-lookup"><span data-stu-id="a3f20-115">IsEnd</span></span>|<span data-ttu-id="a3f20-116">布林值，表示事件是 (`true`) 否 (`false`) 為新 BAM 活動的結束。</span><span class="sxs-lookup"><span data-stu-id="a3f20-116">Boolean value indicating whether the event is the end of a BAM activity (`true`) or not (`false`).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3f20-117">子元素</span><span class="sxs-lookup"><span data-stu-id="a3f20-117">Child Elements</span></span>  
  
|<span data-ttu-id="a3f20-118">執行狀態</span><span class="sxs-lookup"><span data-stu-id="a3f20-118">Execution status</span></span>|<span data-ttu-id="a3f20-119">Description</span><span class="sxs-lookup"><span data-stu-id="a3f20-119">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="a3f20-120">篩選</span><span class="sxs-lookup"><span data-stu-id="a3f20-120">Filter</span></span>|<span data-ttu-id="a3f20-121">提供限制事件符合特定準則的方法。</span><span class="sxs-lookup"><span data-stu-id="a3f20-121">Provides a way to limit the event to specific criteria.</span></span>|  
|<span data-ttu-id="a3f20-122">CorrelationID</span><span class="sxs-lookup"><span data-stu-id="a3f20-122">CorrelationID</span></span>|<span data-ttu-id="a3f20-123">指定關聯識別碼 (活動執行個體識別碼)。</span><span class="sxs-lookup"><span data-stu-id="a3f20-123">Specifies the correlation ID (the activity instance ID).</span></span>|  
|<span data-ttu-id="a3f20-124">ContinuationToken</span><span class="sxs-lookup"><span data-stu-id="a3f20-124">ContinuationToken</span></span>|<span data-ttu-id="a3f20-125">指定接續 Token，也就是日後會導致相同活動執行個體的事件所使用的相互關聯識別碼。</span><span class="sxs-lookup"><span data-stu-id="a3f20-125">Specifies the continuation token, a correlation ID that is used by future events that will contribute to the same activity instance.</span></span>|  
|<span data-ttu-id="a3f20-126">Update</span><span class="sxs-lookup"><span data-stu-id="a3f20-126">Update</span></span>|<span data-ttu-id="a3f20-127">指定資料要從事件中加以擷取，並且匯入至 BAM 活動。</span><span class="sxs-lookup"><span data-stu-id="a3f20-127">Specifies the data to extract from the event and import into the BAM activity.</span></span>|  
|<span data-ttu-id="a3f20-128">參考</span><span class="sxs-lookup"><span data-stu-id="a3f20-128">Reference</span></span>|<span data-ttu-id="a3f20-129">將關係加入至 BAM 活動。</span><span class="sxs-lookup"><span data-stu-id="a3f20-129">Adds a relationship to a BAM activity.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3f20-130">備註</span><span class="sxs-lookup"><span data-stu-id="a3f20-130">Remarks</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3f20-131">範例</span><span class="sxs-lookup"><span data-stu-id="a3f20-131">Example</span></span>  
 <span data-ttu-id="a3f20-132">下列範例示範典型**OnEvent** WF 區塊：</span><span class="sxs-lookup"><span data-stu-id="a3f20-132">The following example shows a typical **OnEvent** block for WF:</span></span>  
  
```  
<ic:OnEvent Name="BeginAct" IsBegin="true" Source="ResWF">  
  <ic:Filter>  
    <ic:Expression>  
      <wf:Operation Name="GetActivityName"/>  
      <ic:Operation Name="Constant">  
        <ic:Argument>FoodAndDrinksPolicy</ic:Argument>  
      </ic:Operation>  
      <ic:Operation Name="Equals"/>  
      <wf:Operation Name="GetActivityEvent"/>  
      <ic:Operation Name="Constant">  
        <ic:Argument>Closed</ic:Argument>  
      </ic:Operation>  
      <ic:Operation Name="Equals"/>  
      <ic:Operation Name="And"/>  
    </ic:Expression>  
  </ic:Filter>  
  <ic:CorrelationID>  
    <ic:Expression>  
      <wf:Operation Name="GetContextProperty">  
        <wf:Argument>InstanceId</wf:Argument>  
      </wf:Operation>  
    </ic:Expression>  
  </ic:CorrelationID>  
  <ic:Update DataItemName="StartOrderProcessing" Type="DATETIME">  
    <ic:Expression>  
      <wf:Operation Name="GetContextProperty">  
        <wf:Argument>EventTime</wf:Argument>  
      </wf:Operation>  
    </ic:Expression>  
  </ic:Update>  
  <ic:Update DataItemName="FoodItem" Type="NVARCHAR">  
    <ic:Expression>  
      <wf:Operation Name="GetWorkflowProperty">  
        <wf:Argument>foodItem</wf:Argument>  
      </wf:Operation>  
    </ic:Expression>  
  </ic:Update>  
</ic:OnEvent>  
```  
  
 <span data-ttu-id="a3f20-133">這個範例示範典型**OnEvent** WCF 服務的區塊：</span><span class="sxs-lookup"><span data-stu-id="a3f20-133">This example shows a typical **OnEvent** block for WCF service:</span></span>  
  
```  
<ic:OnEvent IsBegin="true" IsEnd ="false" Name ="AuthorizationRequestService" Source="ESCreditCardService">  
  <ic:Filter>  
    <ic:Expression>  
      <wcf:Operation Name="GetServiceContractCallPoint"/>  
      <ic:Operation Name ="Constant">  
        <ic:Argument>ServiceRequest</ic:Argument>  
      </ic:Operation>  
      <ic:Operation Name ="Equals"/>  
      <wcf:Operation Name="GetOperationName" />  
      <ic:Operation Name="Constant">  
        <ic:Argument>AuthorizeWithDataContract</ic:Argument>  
      </ic:Operation>  
      <ic:Operation Name ="Equals" />  
      <ic:Operation Name ="And" />  
    </ic:Expression>  
  </ic:Filter>  
  <ic:CorrelationID>  
    <ic:Expression>  
      <ic:Operation Name="Constant">  
        <ic:Argument>ServiceRequest</ic:Argument>  
      </ic:Operation>  
    </ic:Expression>  
  </ic:CorrelationID>  
  <ic:Update DataItemName="Name" Type="NVARCHAR">  
    <ic:Expression>  
      <wcf:Operation Name="XPath">  
        <wcf:Argument>//s:Body/ccservice:*/ccservice:creditCard/creditcard:FirstName</wcf:Argument>  
      </wcf:Operation>  
      <wcf:Operation Name="XPath">  
        <wcf:Argument>//s:Body/ccservice:*/ccservice:creditCard/creditcard:LastName</wcf:Argument>  
      </wcf:Operation>  
      <ic:Operation Name ="Concatenate"/>  
    </ic:Expression>  
  </ic:Update>  
</ic:OnEvent>  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="a3f20-134">本節內容</span><span class="sxs-lookup"><span data-stu-id="a3f20-134">In This Section</span></span>  
  
-   [<span data-ttu-id="a3f20-135">篩選</span><span class="sxs-lookup"><span data-stu-id="a3f20-135">Filter</span></span>](../core/filter.md)  
  
-   [<span data-ttu-id="a3f20-136">相互關聯識別碼</span><span class="sxs-lookup"><span data-stu-id="a3f20-136">CorrelationID</span></span>](../core/correlationid.md)  
  
-   [<span data-ttu-id="a3f20-137">ContinuationToken</span><span class="sxs-lookup"><span data-stu-id="a3f20-137">ContinuationToken</span></span>](../core/continuationtoken.md)  
  
-   [<span data-ttu-id="a3f20-138">參考</span><span class="sxs-lookup"><span data-stu-id="a3f20-138">Reference</span></span>](../core/reference.md)  
  
-   [<span data-ttu-id="a3f20-139">Update</span><span class="sxs-lookup"><span data-stu-id="a3f20-139">Update</span></span>](../core/update2.md)  
  
## <a name="see-also"></a><span data-ttu-id="a3f20-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3f20-140">See Also</span></span>  
 [<span data-ttu-id="a3f20-141">攔截器組態檔的結構</span><span class="sxs-lookup"><span data-stu-id="a3f20-141">Structure of an Interceptor Configuration File</span></span>](../core/structure-of-an-interceptor-configuration-file.md)