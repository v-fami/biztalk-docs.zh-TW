---
title: 更新程式 2 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 770c9ebb-df3a-428f-be18-b36535352f8d
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4376cae94e91f462974c626a57170b80b0117ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22286758"
---
# <a name="update"></a><span data-ttu-id="24a04-102">Update</span><span class="sxs-lookup"><span data-stu-id="24a04-102">Update</span></span>
<span data-ttu-id="24a04-103">`Update` 項目可用來從事件中擷取資料，並將該資料匯入相關的 BAM 活動。</span><span class="sxs-lookup"><span data-stu-id="24a04-103">The `Update` element is used to extract data from an event and import it into the related BAM activity.</span></span>  
  
## <a name="format"></a><span data-ttu-id="24a04-104">格式</span><span class="sxs-lookup"><span data-stu-id="24a04-104">Format</span></span>  
 <span data-ttu-id="24a04-105">若要使用`Update`項目，您必須提供資料行名稱和型別和**運算式**包含一或多個項目**作業**評估成單一字串值的項目。</span><span class="sxs-lookup"><span data-stu-id="24a04-105">To use the `Update` element, you must provide both a column name and type and an **Expression** element containing one or more **Operation** elements that evaluate to a single string value.</span></span>  
  
```  
<ic:Update DataItemName="Name" Type="Type">  
  <ic:Expression>  
    <!-- one or more Operation elements -->  
  </ic:Expression>  
</ic:Update>  
```  
  
### <a name="attributes"></a><span data-ttu-id="24a04-106">屬性</span><span class="sxs-lookup"><span data-stu-id="24a04-106">Attributes</span></span>  
  
|<span data-ttu-id="24a04-107">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="24a04-107">Attribute name</span></span>|<span data-ttu-id="24a04-108">Description</span><span class="sxs-lookup"><span data-stu-id="24a04-108">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="24a04-109">ColumnName</span><span class="sxs-lookup"><span data-stu-id="24a04-109">ColumnName</span></span>|<span data-ttu-id="24a04-110">BAM 活動檢查點名稱。</span><span class="sxs-lookup"><span data-stu-id="24a04-110">BAM activity checkpoint name.</span></span> <span data-ttu-id="24a04-111">這是會跟著已擷取資料更新的檢查點。</span><span class="sxs-lookup"><span data-stu-id="24a04-111">This is the checkpoint that will be updated with the extracted data.</span></span>|  
|<span data-ttu-id="24a04-112">類型</span><span class="sxs-lookup"><span data-stu-id="24a04-112">Type</span></span>|<span data-ttu-id="24a04-113">此檢查點的 BAM 資料型別必須是下列其中一種：</span><span class="sxs-lookup"><span data-stu-id="24a04-113">BAM data type of the checkpoint; must be one of the following:</span></span><br /><br /> <span data-ttu-id="24a04-114">-NVARCHAR</span><span class="sxs-lookup"><span data-stu-id="24a04-114">-   NVARCHAR</span></span><br /><span data-ttu-id="24a04-115">日期時間</span><span class="sxs-lookup"><span data-stu-id="24a04-115">-   DATETIME</span></span><br /><span data-ttu-id="24a04-116">-INT</span><span class="sxs-lookup"><span data-stu-id="24a04-116">-   INT</span></span><br /><span data-ttu-id="24a04-117">浮點數</span><span class="sxs-lookup"><span data-stu-id="24a04-117">-   FLOAT</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24a04-118">備註</span><span class="sxs-lookup"><span data-stu-id="24a04-118">Remarks</span></span>  
 <span data-ttu-id="24a04-119">下面列出 `Update` 運算式不支援的運算：</span><span class="sxs-lookup"><span data-stu-id="24a04-119">The following operations are not supported in the `Update` expression:</span></span>  
  
-   <span data-ttu-id="24a04-120">And</span><span class="sxs-lookup"><span data-stu-id="24a04-120">And</span></span>  
  
-   <span data-ttu-id="24a04-121">等於</span><span class="sxs-lookup"><span data-stu-id="24a04-121">Equals</span></span>  
  
## <a name="example"></a><span data-ttu-id="24a04-122">範例</span><span class="sxs-lookup"><span data-stu-id="24a04-122">Example</span></span>  
 <span data-ttu-id="24a04-123">在下列範例中， **GetContextProperty** WF 作業用來擷取**EventTime**屬性。</span><span class="sxs-lookup"><span data-stu-id="24a04-123">In the following example, the **GetContextProperty** WF operation is used to retrieve the **EventTime** property.</span></span> <span data-ttu-id="24a04-124">這個值會儲存為**DATETIME** "StartOrderProcessing"資料項目的 BAM 活動的型別。</span><span class="sxs-lookup"><span data-stu-id="24a04-124">This value will be stored as a **DATETIME** type for the "StartOrderProcessing" data item for the BAM activity.</span></span>  
  
```  
<ic:Update DataItemName="StartOrderProcessing" Type="DATETIME">  
  <ic:Expression>  
    <wf:Operation Name="GetContextProperty">  
      <wf:Argument>EventTime</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:Update>  
```  
  
## <a name="see-also"></a><span data-ttu-id="24a04-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24a04-125">See Also</span></span>  
 [<span data-ttu-id="24a04-126">攔截器 OnEvent 項目</span><span class="sxs-lookup"><span data-stu-id="24a04-126">Interceptor OnEvent Element</span></span>](../core/interceptor-onevent-element.md)