---
title: "使用辨別的欄位和屬性欄位 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, distinquished fields
- messages, properties
ms.assetid: 264ee15e-be9a-4ba2-9c61-a1570b20378e
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa0f969be7dfdd7cca991be134c9a25329f559a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-distinguished-fields-and-property-fields"></a><span data-ttu-id="4cf17-102">使用辨別的欄位和屬性欄位</span><span class="sxs-lookup"><span data-stu-id="4cf17-102">Using Distinguished Fields and Property Fields</span></span>
<span data-ttu-id="4cf17-103">辨別欄位是您在協調流程中制定決策或是操控資料時，主要所使用的有用訊息資料。</span><span class="sxs-lookup"><span data-stu-id="4cf17-103">Distinguished fields are message data of special interest that you use primarily to make decisions or to manipulate data in your orchestration.</span></span>  
  
 <span data-ttu-id="4cf17-104">訊息屬性是資料 (訊息本身的內容) 或「中繼資料」(訊息相關資訊的內容，例如時間戳記或路由資訊)。</span><span class="sxs-lookup"><span data-stu-id="4cf17-104">Message properties are either data—contents of the message itself—or "metadata"—context information about the message such as time stamps or routing information.</span></span> <span data-ttu-id="4cf17-105">您可以使用系統定義的訊息內容屬性或傳輸內容屬性，也可以從屬性結構描述中參考結構描述欄位來定義自己的屬性。</span><span class="sxs-lookup"><span data-stu-id="4cf17-105">You can use system-defined message context properties or transport context properties, or you can define your own properties by making reference to schema fields from within a property schema.</span></span> <span data-ttu-id="4cf17-106">屬性會用於訂閱和相互關聯。</span><span class="sxs-lookup"><span data-stu-id="4cf17-106">Properties are used in subscriptions and correlations.</span></span>  
  
-   <span data-ttu-id="4cf17-107">您可以將結構描述中的欄位指定為辨別的欄位或屬性欄位使用**升級屬性**對話方塊編輯器中的。</span><span class="sxs-lookup"><span data-stu-id="4cf17-107">You can designate a field in a schema as a distinguished field or property field by using the **Promote Properties** dialog box from within the Editor.</span></span> <span data-ttu-id="4cf17-108">如需詳細資訊，請參閱[升級屬性](../core/promoting-properties.md)</span><span class="sxs-lookup"><span data-stu-id="4cf17-108">For more information, see [Promoting Properties](../core/promoting-properties.md)</span></span>  
  
-   <span data-ttu-id="4cf17-109">您可以使用 DistinguishedField 屬性 (Attribute) 裝飾 .NET 類型中的欄位，將它指定為辨別欄位；或者以 Property 屬性來裝飾，將它指定為屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="4cf17-109">You can designate a field in a .NET type as a distinguished field by decorating it with the DistinguishedField attribute, or as a property by the Property attribute.</span></span>  
  
## <a name="using-distinguished-fields"></a><span data-ttu-id="4cf17-110">使用辨別欄位</span><span class="sxs-lookup"><span data-stu-id="4cf17-110">Using Distinguished Fields</span></span>  
 <span data-ttu-id="4cf17-111">辨別欄位是由訊息中欄位的路徑所參考，並使用句號來分隔訊息名稱、任何包含欄位之記錄的名稱與欄位名稱本身：</span><span class="sxs-lookup"><span data-stu-id="4cf17-111">Distinguished fields are referred to by the path to the field in the message, using periods to separate the message name, the names of any records that enclose the field, and the name of the field itself:</span></span>  
  
```  
MyMessage.MyRecord.MySubrecord.MyDistinguishedField  
```  
  
## <a name="using-property-fields"></a><span data-ttu-id="4cf17-112">使用屬性欄位</span><span class="sxs-lookup"><span data-stu-id="4cf17-112">Using Property Fields</span></span>  
 <span data-ttu-id="4cf17-113">將某個欄位加入至屬性結構描述之後，您就可以利用程式碼和篩選條件運算式，在協調流程中存取其值。</span><span class="sxs-lookup"><span data-stu-id="4cf17-113">Once you have added a field to a property schema, its value can be accessed in the orchestration with code and in filter expressions.</span></span> <span data-ttu-id="4cf17-114">如需屬性結構描述的詳細資訊，請參閱[屬性結構描述](../core/property-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="4cf17-114">For more information about property schemas, see [Property Schemas](../core/property-schemas.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4cf17-115">訊息內容或資料屬性是基本上是基礎資料的捷徑： 如果您修改屬性時，資料會被修改，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="4cf17-115">Message content or data properties are essentially shortcuts to the underlying data: if you modify the property, the data will be modified, and vice versa.</span></span>  
  
 <span data-ttu-id="4cf17-116">訊息屬性是由訊息名稱所參考，此名稱後面跟隨著以括號包住的命名空間 (結構描述) 及屬性名稱：</span><span class="sxs-lookup"><span data-stu-id="4cf17-116">Message properties are referred to by the name of the message followed by the namespace (the schema) and property name in parentheses:</span></span>  
  
```  
MyMessage(Invoice.PropertySchema.InvoiceID)  
```  
  
> [!NOTE]
>  <span data-ttu-id="4cf17-117">當您使用保留的關鍵字做為結構描述中的欄位名稱和您選取 [快速升級] 升級欄位時，欄位的屬性名稱變更為 __\<保留關鍵字 >。</span><span class="sxs-lookup"><span data-stu-id="4cf17-117">When you use a reserved keyword as the name of a field in a schema, and you promote the field by selecting Quick Promotion, the property name of the field is changed to __\<Reserved Keyword>.</span></span> <span data-ttu-id="4cf17-118">(屬性名稱前會加上兩個底線)。不過，如果在協調流程運算式中使用這個屬性名稱，您將會在建置協調流程時收到編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="4cf17-118">(The double underscore is added before the property name.) However, if you use this property name in an orchestration expression, you will receive a compiler error when building the orchestration.</span></span>  <span data-ttu-id="4cf17-119">若要解決此錯誤，您必須以手動方式，在雙底線前面加上 @。</span><span class="sxs-lookup"><span data-stu-id="4cf17-119">To work around this error, you need to manually add @ before the double underscore.</span></span> <span data-ttu-id="4cf17-120">例如，</span><span class="sxs-lookup"><span data-stu-id="4cf17-120">For example,</span></span>  
>   
>  `MyMessage(Invoice.PropertySchema.@__Name) = "Product Name";`  
  
## <a name="property-sets"></a><span data-ttu-id="4cf17-121">屬性集</span><span class="sxs-lookup"><span data-stu-id="4cf17-121">Property Sets</span></span>  
 <span data-ttu-id="4cf17-122">您也可以將一個訊息的所有內容屬性 (屬性集) 指派給另一個訊息的內容屬性。</span><span class="sxs-lookup"><span data-stu-id="4cf17-122">You can also assign all of the context properties of one message (a property set) to the context properties of another message.</span></span> <span data-ttu-id="4cf17-123">若要指派屬性集，只需在兩個訊息名稱之後的括號中放置星號，就和您將屬性放在括號中一樣：</span><span class="sxs-lookup"><span data-stu-id="4cf17-123">To assign a property set, you simply place an asterisk in parentheses after both message names, in the same way you would put a property in parentheses:</span></span>  
  
```  
MyMessage2(*)=MyMessage1(*);  
```  
  
 <span data-ttu-id="4cf17-124">將屬性集指派給範例中的 MyMessage2 之後，MyMessage2 中的所有屬性都會包含與 MyMessage1 之屬性相同的值。</span><span class="sxs-lookup"><span data-stu-id="4cf17-124">After the property set has been assigned to MyMessage2 in the example, all of the properties in MyMessage2 contain the same values as the properties in MyMessage1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cf17-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4cf17-125">See Also</span></span>  
 <span data-ttu-id="4cf17-126">[升級屬性](../core/promoting-properties.md) </span><span class="sxs-lookup"><span data-stu-id="4cf17-126">[Promoting Properties](../core/promoting-properties.md) </span></span>  
 <span data-ttu-id="4cf17-127">[使用篩選器與接收訊息 」 圖形](../core/using-filters-with-the-receive-message-shape.md) </span><span class="sxs-lookup"><span data-stu-id="4cf17-127">[Using Filters With the Receive Message Shape](../core/using-filters-with-the-receive-message-shape.md) </span></span>  
 <span data-ttu-id="4cf17-128">[協調流程中使用訊息](../core/using-messages-in-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="4cf17-128">[Using Messages in Orchestrations](../core/using-messages-in-orchestrations.md) </span></span>  
 [<span data-ttu-id="4cf17-129">關於 BizTalk 訊息內容屬性</span><span class="sxs-lookup"><span data-stu-id="4cf17-129">About BizTalk Message Context Properties</span></span>](../core/about-biztalk-message-context-properties.md)