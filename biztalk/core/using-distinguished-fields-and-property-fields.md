---
title: 使用辨別的欄位和屬性欄位 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, distinquished fields
- messages, properties
ms.assetid: 264ee15e-be9a-4ba2-9c61-a1570b20378e
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18b5d5ee3b29c068b3a37d248b9fb20f07bdfbb2
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="using-distinguished-fields-and-property-fields"></a><span data-ttu-id="c7395-102">使用辨別的欄位和屬性欄位</span><span class="sxs-lookup"><span data-stu-id="c7395-102">Using Distinguished Fields and Property Fields</span></span>
<span data-ttu-id="c7395-103">고유 필드는 오케스트레이션에서 데이터를 조작하거나 판단하기 위해 기본적으로 사용하는 특별한 메시지 데이터입니다.</span><span class="sxs-lookup"><span data-stu-id="c7395-103">Distinguished fields are message data of special interest that you use primarily to make decisions or to manipulate data in your orchestration.</span></span>  
  
 <span data-ttu-id="c7395-104">메시지 속성은 메시지 자체의 내용인 데이터이거나 타임스탬프 또는 라우팅 정보와 같은 메시지에 대한 컨텍스트 정보인 "메타데이터"입니다.</span><span class="sxs-lookup"><span data-stu-id="c7395-104">Message properties are either data—contents of the message itself—or "metadata"—context information about the message such as time stamps or routing information.</span></span> <span data-ttu-id="c7395-105">속성 스키마에서 스키마 필드에 대한 참조를 만들어 사용자 고유의 속성을 정의하거나 시스템에서 정의한 메시지 컨텍스트 속성 또는 전송 컨텍스트 속성을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7395-105">You can use system-defined message context properties or transport context properties, or you can define your own properties by making reference to schema fields from within a property schema.</span></span> <span data-ttu-id="c7395-106">속성은 등록 및 상관 관계에 사용됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7395-106">Properties are used in subscriptions and correlations.</span></span>  
  
-   <span data-ttu-id="c7395-107">您可以將結構描述中的欄位指定為辨別的欄位或屬性欄位使用 **升級屬性** 從對話方塊編輯器中的。</span><span class="sxs-lookup"><span data-stu-id="c7395-107">You can designate a field in a schema as a distinguished field or property field by using the **Promote Properties** dialog box from within the Editor.</span></span> <span data-ttu-id="c7395-108">如需詳細資訊，請參閱[升級屬性](../core/promoting-properties.md)</span><span class="sxs-lookup"><span data-stu-id="c7395-108">For more information, see [Promoting Properties](../core/promoting-properties.md)</span></span>  
  
-   <span data-ttu-id="c7395-109">.NET 유형의 필드를 DistinguishedField 특성으로 데코레이팅하여 고유 필드로 지정하거나 Property 특성을 사용하여 속성으로 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7395-109">You can designate a field in a .NET type as a distinguished field by decorating it with the DistinguishedField attribute, or as a property by the Property attribute.</span></span>  
  
## <a name="using-distinguished-fields"></a><span data-ttu-id="c7395-110">고유 필드 사용</span><span class="sxs-lookup"><span data-stu-id="c7395-110">Using Distinguished Fields</span></span>  
 <span data-ttu-id="c7395-111">고유 필드는 메시지에 있는 필드에 대한 경로에서 참조하며 다음과 같이 마침표를 사용하여 메시지 이름, 필드를 둘러싸고 있는 모든 레코드의 이름, 필드 자체의 이름을 구분합니다.</span><span class="sxs-lookup"><span data-stu-id="c7395-111">Distinguished fields are referred to by the path to the field in the message, using periods to separate the message name, the names of any records that enclose the field, and the name of the field itself:</span></span>  
  
```  
MyMessage.MyRecord.MySubrecord.MyDistinguishedField  
```  
  
## <a name="using-property-fields"></a><span data-ttu-id="c7395-112">속성 필드 사용</span><span class="sxs-lookup"><span data-stu-id="c7395-112">Using Property Fields</span></span>  
 <span data-ttu-id="c7395-113">속성 스키마에 필드를 추가하면 코드가 있는 오케스트레이션 및 필터 식에서 해당 값에 액세스할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7395-113">Once you have added a field to a property schema, its value can be accessed in the orchestration with code and in filter expressions.</span></span> <span data-ttu-id="c7395-114">如需屬性結構描述的詳細資訊，請參閱[屬性結構描述](../core/property-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="c7395-114">For more information about property schemas, see [Property Schemas](../core/property-schemas.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7395-115">訊息內容或資料屬性是基本上是基礎資料的捷徑︰ 如果您修改屬性，將會修改資料，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="c7395-115">Message content or data properties are essentially shortcuts to the underlying data: if you modify the property, the data will be modified, and vice versa.</span></span>  
  
 <span data-ttu-id="c7395-116">메시지 속성은 다음과 같이 괄호로 묶인 네임스페이스(스키마)와 속성 이름의 앞에 나오는 메시지 이름에 의해 참조됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7395-116">Message properties are referred to by the name of the message followed by the namespace (the schema) and property name in parentheses:</span></span>  
  
```  
MyMessage(Invoice.PropertySchema.InvoiceID)  
```  
  
> [!NOTE]
>  <span data-ttu-id="c7395-117">當您使用保留的關鍵字做為結構描述中的欄位名稱和您選取 [快速升級] 升級欄位時，欄位的屬性名稱變更為 __\<保留的關鍵字\>。</span><span class="sxs-lookup"><span data-stu-id="c7395-117">When you use a reserved keyword as the name of a field in a schema, and you promote the field by selecting Quick Promotion, the property name of the field is changed to __\<Reserved Keyword\>.</span></span> <span data-ttu-id="c7395-118">여기서 이중 밑줄이 속성 이름 앞에 추가됩니다.그러나 이 속성 이름을 오케스트레이션 Expression에서 사용하면 오케스트레이션을 빌드할 때 컴파일러 오류가 발생합니다.</span><span class="sxs-lookup"><span data-stu-id="c7395-118">(The double underscore is added before the property name.) However, if you use this property name in an orchestration expression, you will receive a compiler error when building the orchestration.</span></span>  <span data-ttu-id="c7395-119">若要解決此錯誤，您必須以手動方式，在雙底線前面加上 @。</span><span class="sxs-lookup"><span data-stu-id="c7395-119">To work around this error, you need to manually add @ before the double underscore.</span></span> <span data-ttu-id="c7395-120">예:</span><span class="sxs-lookup"><span data-stu-id="c7395-120">For example,</span></span>  
>   
>  `MyMessage(Invoice.PropertySchema.@__Name) = "Product Name";`  
  
## <a name="property-sets"></a><span data-ttu-id="c7395-121">속성 집합</span><span class="sxs-lookup"><span data-stu-id="c7395-121">Property Sets</span></span>  
 <span data-ttu-id="c7395-122">또한 한 메시지의 모든 컨텍스트 속성(속성 집합)을 다른 메시지의 컨텍스트 속성에 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="c7395-122">You can also assign all of the context properties of one message (a property set) to the context properties of another message.</span></span> <span data-ttu-id="c7395-123">속성 집합을 할당하려면 속성을 괄호로 묶는 방식처럼 다음과 같이 두 메시지 이름 뒤에 괄호로 묶인 별표를 입력합니다.</span><span class="sxs-lookup"><span data-stu-id="c7395-123">To assign a property set, you simply place an asterisk in parentheses after both message names, in the same way you would put a property in parentheses:</span></span>  
  
```  
MyMessage2(*)=MyMessage1(*);  
```  
  
 <span data-ttu-id="c7395-124">이 예에서 속성 집합을 MyMessage2에 할당하면 MyMessage2의 모든 속성 값은 MyMessage1의 속성 값과 동일하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="c7395-124">After the property set has been assigned to MyMessage2 in the example, all of the properties in MyMessage2 contain the same values as the properties in MyMessage1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7395-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7395-125">See Also</span></span>  
 <span data-ttu-id="c7395-126">[升級屬性](../core/promoting-properties.md) </span><span class="sxs-lookup"><span data-stu-id="c7395-126">[Promoting Properties](../core/promoting-properties.md) </span></span>  
 <span data-ttu-id="c7395-127">[使用篩選器與接收訊息 」 圖形](../core/using-filters-with-the-receive-message-shape.md) </span><span class="sxs-lookup"><span data-stu-id="c7395-127">[Using Filters With the Receive Message Shape](../core/using-filters-with-the-receive-message-shape.md) </span></span>  
 <span data-ttu-id="c7395-128">[協調流程中使用訊息](../core/using-messages-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="c7395-128">[Using Messages in Orchestrations](../core/using-messages-in-orchestrations.md) </span></span>  
 [<span data-ttu-id="c7395-129">關於 BizTalk 訊息內容屬性</span><span class="sxs-lookup"><span data-stu-id="c7395-129">About BizTalk Message Context Properties</span></span>](../core/about-biztalk-message-context-properties.md)