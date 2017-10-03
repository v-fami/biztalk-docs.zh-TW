---
title: "參考 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b916c55a-c84c-4008-8927-f8e584c36fe9
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3e32145e2340a4d86a6893db3e9209b79c2b5e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="reference"></a><span data-ttu-id="02bf8-102">參考</span><span class="sxs-lookup"><span data-stu-id="02bf8-102">Reference</span></span>
<span data-ttu-id="02bf8-103">**參考**項目可用來將一或多個關聯性加入至 BAM 活動。</span><span class="sxs-lookup"><span data-stu-id="02bf8-103">The **Reference** element can be used to add one or more relationships to a BAM activity.</span></span> <span data-ttu-id="02bf8-104">當您想要將指標如主索引鍵、識別碼或 URL 附加到相關訊息時，這十分有用。</span><span class="sxs-lookup"><span data-stu-id="02bf8-104">This is useful when you want to attach a pointer like a primary key, ID, or URL to a related message.</span></span> <span data-ttu-id="02bf8-105">例如，您可以在訂單活動中儲存出貨批次的參考。</span><span class="sxs-lookup"><span data-stu-id="02bf8-105">For example, you might store a reference to a Shipment Batch in a Purchase Order activity.</span></span>  
  
## <a name="format"></a><span data-ttu-id="02bf8-106">格式</span><span class="sxs-lookup"><span data-stu-id="02bf8-106">Format</span></span>  
 <span data-ttu-id="02bf8-107">`Reference`元素同時支援**資料**和**LongData**子項目包含一個運算式來指定要附加到 BAM 活動的資料。</span><span class="sxs-lookup"><span data-stu-id="02bf8-107">The `Reference` element supports both the **Data** and **LongData** child elements that contain an expression specifying the data to attach to the BAM activity.</span></span> <span data-ttu-id="02bf8-108">您可以使用的任何組合**資料**和**LongData**以符合追蹤需求。</span><span class="sxs-lookup"><span data-stu-id="02bf8-108">You can use any combination of **Data** and **LongData** to meet your tracking requirements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02bf8-109">屬性</span><span class="sxs-lookup"><span data-stu-id="02bf8-109">Attributes</span></span>  
  
|<span data-ttu-id="02bf8-110">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="02bf8-110">Attribute name</span></span>|<span data-ttu-id="02bf8-111">Description</span><span class="sxs-lookup"><span data-stu-id="02bf8-111">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="02bf8-112">名稱</span><span class="sxs-lookup"><span data-stu-id="02bf8-112">Name</span></span>|<span data-ttu-id="02bf8-113">將附加到 BAM 活動的關係名稱。</span><span class="sxs-lookup"><span data-stu-id="02bf8-113">Name of the relationship that will be attached to the BAM activity.</span></span>|  
|<span data-ttu-id="02bf8-114">類型</span><span class="sxs-lookup"><span data-stu-id="02bf8-114">Type</span></span>|<span data-ttu-id="02bf8-115">任意字串，指定將附加到 BAM 活動的關係類型。</span><span class="sxs-lookup"><span data-stu-id="02bf8-115">Arbitrary string specifying the type of relationship that will be attached to the BAM activity.</span></span> <span data-ttu-id="02bf8-116">支援任意字串和下列預先定義的 BAM 類型：</span><span class="sxs-lookup"><span data-stu-id="02bf8-116">Both arbitrary strings and the following predefined BAM types are supported:</span></span><br /><br /> <span data-ttu-id="02bf8-117">-BizTalkService</span><span class="sxs-lookup"><span data-stu-id="02bf8-117">-   BizTalkService</span></span><br /><span data-ttu-id="02bf8-118">-MessageID</span><span class="sxs-lookup"><span data-stu-id="02bf8-118">-   MessageID</span></span><br /><span data-ttu-id="02bf8-119">活動</span><span class="sxs-lookup"><span data-stu-id="02bf8-119">-   Activity</span></span><br /><span data-ttu-id="02bf8-120">-DocumentUrl</span><span class="sxs-lookup"><span data-stu-id="02bf8-120">-   DocumentUrl</span></span><br /><span data-ttu-id="02bf8-121">-執行個體識別碼</span><span class="sxs-lookup"><span data-stu-id="02bf8-121">-   InstanceID</span></span><br /><br /> <span data-ttu-id="02bf8-122">如需有關預先定義的 BAM 參考類型的詳細資訊，請參閱[參考屬性](http://go.microsoft.com/fwlink/?LinkId=119601)。</span><span class="sxs-lookup"><span data-stu-id="02bf8-122">For more information on predefined BAM reference types, see [Reference Properties](http://go.microsoft.com/fwlink/?LinkId=119601).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="02bf8-123">子元素</span><span class="sxs-lookup"><span data-stu-id="02bf8-123">Child Elements</span></span>  
  
|<span data-ttu-id="02bf8-124">執行狀態</span><span class="sxs-lookup"><span data-stu-id="02bf8-124">Execution status</span></span>|<span data-ttu-id="02bf8-125">Description</span><span class="sxs-lookup"><span data-stu-id="02bf8-125">Description</span></span>|  
|----------------------|-----------------|  
|<span data-ttu-id="02bf8-126">data</span><span class="sxs-lookup"><span data-stu-id="02bf8-126">Data</span></span>|<span data-ttu-id="02bf8-127">指定如何擷取將附加到 BAM 活動的字串資料 (最多 128 個字元)。</span><span class="sxs-lookup"><span data-stu-id="02bf8-127">Specifies how to extract string data up to 128 characters that will be attached to the BAM activity.</span></span>|  
|<span data-ttu-id="02bf8-128">LongData</span><span class="sxs-lookup"><span data-stu-id="02bf8-128">LongData</span></span>|<span data-ttu-id="02bf8-129">指定如何擷取將附加到 BAM 活動的任意長度字串資料。</span><span class="sxs-lookup"><span data-stu-id="02bf8-129">Specifies how to extract arbitrarily long string data that will be attached to the BAM activity.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="02bf8-130">A`Reference`項目可以結合一或多個**資料**和**LongData**視需要的項目子系。</span><span class="sxs-lookup"><span data-stu-id="02bf8-130">A `Reference` element can combine one or more **Data** and **LongData** child elements as needed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02bf8-131">備註</span><span class="sxs-lookup"><span data-stu-id="02bf8-131">Remarks</span></span>  
 <span data-ttu-id="02bf8-132">Reference 運算式中不允許執行下列常見的運算：</span><span class="sxs-lookup"><span data-stu-id="02bf8-132">The following common operations are not allowed in Reference expressions:</span></span>  
  
-   <span data-ttu-id="02bf8-133">And</span><span class="sxs-lookup"><span data-stu-id="02bf8-133">And</span></span>  
  
-   <span data-ttu-id="02bf8-134">等於</span><span class="sxs-lookup"><span data-stu-id="02bf8-134">Equals</span></span>  
  
## <a name="example"></a><span data-ttu-id="02bf8-135">範例</span><span class="sxs-lookup"><span data-stu-id="02bf8-135">Example</span></span>  
 <span data-ttu-id="02bf8-136">下列範例會使用 `GetUserData`，為工作流程建立 "DocumentUrl" 類型的 "Related Document" 參考。</span><span class="sxs-lookup"><span data-stu-id="02bf8-136">In the following sample, a reference named "Related Document" of type "DocumentUrl" is created using `GetUserData` for a workflow.</span></span> <span data-ttu-id="02bf8-137">因為使用者資料預期少於 1024 字元長度，所以會使用 `Data` 項目以取得 `Expression` 項目。</span><span class="sxs-lookup"><span data-stu-id="02bf8-137">Because the user data is expected to be fewer than 1024 characters in length, the `Data` element is used to contain the `Expression` element.</span></span>  
  
```  
<ic:Reference Name="Related Document" Type="DocumentUrl">  
  <ic:Data>  
    <ic:Expression>  
      <wf:Operation Name="GetUserData" />  
    </ic:Expression>  
  </ic:Data>  
</ic:Reference>  
```  
  
 <span data-ttu-id="02bf8-138">**參考**項目支援的混合`Data`和`LongData`項目。</span><span class="sxs-lookup"><span data-stu-id="02bf8-138">The **Reference** element supports a mix of `Data` and `LongData` elements.</span></span> <span data-ttu-id="02bf8-139">下列範例會從 WCF 服務擷取訂單中的 Country Name 和 Note 欄位，並寫入至 "Long and Short Data" 關係做為 "MyType" 類型。</span><span class="sxs-lookup"><span data-stu-id="02bf8-139">In the following sample, the country name and note fields from a purchase order are retrieved from a WCF service and written to the relationship "Long and Short Data" as type "MyType".</span></span> <span data-ttu-id="02bf8-140">因為 Note 欄位支援 1024 個字元以上，所以運算式會包含在 `LongData` 項目中。</span><span class="sxs-lookup"><span data-stu-id="02bf8-140">Because the note field supports more than 1024 characters, the expression is enclosed in a `LongData` element.</span></span>  
  
```  
<ic:Reference Name="Long and Short Data" Type="MyType">  
  <ic:Data>  
    <ic:Expression>  
      <ic:Operation Name="Constant">  
        <ic:Argument>Country: </ic:Argument>  
      </ic:Operation>  
      <wcf:Operation Name="XPath">  
        <wcf:Argument>//s:Body//po:Country</wcf:Argument>  
      </wcf:Operation>  
       <ic:Operation Name="Concatenate" />  
    </ic:Expression>  
  </ic:Data>  
  <ic:LongData>  
    <ic:Expression>  
      <ic:Operation Name="Constant">  
        <ic:Argument>Note: </ic:Argument>  
      </ic:Operation>  
      <wcf:Operation Name="XPath">  
        <wcf:Argument>//s:Body//po:Note</wcf:Argument>  
      </wcf:Operation>  
      <ic:Operation Name="Concatenate" />  
    </ic:Expression>  
  </ic:LongData>  
</ic:Reference>  
```  
  
## <a name="see-also"></a><span data-ttu-id="02bf8-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02bf8-141">See Also</span></span>  
 <span data-ttu-id="02bf8-142">[攔截器 OnEvent 項目](../core/interceptor-onevent-element.md) </span><span class="sxs-lookup"><span data-stu-id="02bf8-142">[Interceptor OnEvent Element](../core/interceptor-onevent-element.md) </span></span>  
 [<span data-ttu-id="02bf8-143">EventStream.AddRelatedActivity 方法</span><span class="sxs-lookup"><span data-stu-id="02bf8-143">EventStream.AddRelatedActivity Method</span></span>](http://go.microsoft.com/fwlink/?LinkId=119602)