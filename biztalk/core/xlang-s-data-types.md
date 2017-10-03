---
title: "XLANG 的資料型別 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, expressions
- Orchestration Designer, managing data
- Orchestration Designer, variables
- orchestrations, variables
- Orchestration Designer, expressions
ms.assetid: 5b08aaa6-1533-4bac-a76d-f9162e39bf4f
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c21ed77c5fdd56485514d17ed75e921c63a56212
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="xlang-s-data-types"></a><span data-ttu-id="b7ba0-102">XLANG 的資料型別</span><span class="sxs-lookup"><span data-stu-id="b7ba0-102">XLANG-s Data Types</span></span>
<span data-ttu-id="b7ba0-103">XLANG/s 會定義標準數值型別，這些型別為其 C# 對應型別的反映，</span><span class="sxs-lookup"><span data-stu-id="b7ba0-103">XLANG/s defines standard value types that are reflections of their C# counterparts.</span></span> <span data-ttu-id="b7ba0-104">這些包括**布林**，**位元組**， **Char**，**十進位**， **Double**， **Int16**， **Int32**， **Int64**， **SByte**，**單一**，**字串**， **UInt16**， **UInt32**，和**UInt64**。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-104">These include **Boolean**, **Byte**, **Char**, **Decimal**, **Double**, **Int16**, **Int32**, **Int64**, **SByte**, **Single**, **String**, **UInt16**, **UInt32**, and **UInt64**.</span></span> <span data-ttu-id="b7ba0-105">XLANG/s 支援單一維度陣列，但不支援陣列常值。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-105">XLANG/s supports single-dimensional arrays, but does not support array literals.</span></span>  
  
 <span data-ttu-id="b7ba0-106">XLANG/s 也支援許多種訊息處理方式。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-106">XLANG/s also has rich support for message handling.</span></span> <span data-ttu-id="b7ba0-107">訊息可以基於結構描述、.NET 類別、Web 訊息類型 (WSDL) 或複雜的訊息類型。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-107">Messages can be based on schemas, .NET classes, Web message types (WSDL), or complex message types.</span></span> <span data-ttu-id="b7ba0-108">XLANG/s 支援下列複雜的資料型別：</span><span class="sxs-lookup"><span data-stu-id="b7ba0-108">XLANG/s supports the following complex data types:</span></span>  
  
-   <span data-ttu-id="b7ba0-109">**messagetype。**</span><span class="sxs-lookup"><span data-stu-id="b7ba0-109">**messagetype.**</span></span> <span data-ttu-id="b7ba0-110">此資料型別定義其定義的資料元素，以 XSD 為基礎的訊息組合為多部分訊息類型和方法訊息類型 （符合的類別或介面的方法簽章格式的訊息）。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-110">This data type defines multipart message types which are defined as combinations of data elements and XSD-based messages and Method-Message types (messages that match the signature format of a method of a class or interface).</span></span>  
  
-   <span data-ttu-id="b7ba0-111">**連接埠類型。**</span><span class="sxs-lookup"><span data-stu-id="b7ba0-111">**porttype.**</span></span> <span data-ttu-id="b7ba0-112">這種資料型別會定義該類型之連接埠執行個體可執行的連接埠作業集合。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-112">This data type defines a collection of port operations that a port instance of that type can act upon.</span></span>  
  
-   <span data-ttu-id="b7ba0-113">**correlationsettype。**</span><span class="sxs-lookup"><span data-stu-id="b7ba0-113">**correlationsettype.**</span></span> <span data-ttu-id="b7ba0-114">這種資料型別會定義將用於任何相互關聯集合變數執行個體中的資料。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-114">This data type defines the data that will be used in any instance of a correlation set variable.</span></span> <span data-ttu-id="b7ba0-115">相互關聯集合資料是一種路由機制，可確保系統中移動的訊息會分派至正確的執行中商務程序執行個體。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-115">Correlation set data is the routing mechanism used to ensure that messages moving through the system are dispatched to the appropriate running instance of a business process.</span></span> <span data-ttu-id="b7ba0-116">例如，如果採購單傳送至交易夥伴進行處理，在採購單傳回時，必須叫用正確對應的商務程序執行個體。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-116">For example, if a purchase order is sent to a trading partner for processing, it is imperative that the correct instance of the business process corresponding to that purchase order be invoked on its return.</span></span>  
  
-   <span data-ttu-id="b7ba0-117">**servicelinktype。**</span><span class="sxs-lookup"><span data-stu-id="b7ba0-117">**servicelinktype.**</span></span> <span data-ttu-id="b7ba0-118">此資料型別定義的一組**porttype**形成邏輯一致的商務程序中使用的連接埠群組的值。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-118">This data type defines the set of **porttype** values that form a logically consistent group of ports used in a business process.</span></span> <span data-ttu-id="b7ba0-119">使用服務連結是一項功能強大的機制，允許在執行階段對連接埠群組進行動態指派。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-119">The use of service links is a powerful mechanism that allows dynamic assignment to a group of ports at run time.</span></span> <span data-ttu-id="b7ba0-120">這可讓您定義一個可用於與多個交易夥伴互動的商務程序。</span><span class="sxs-lookup"><span data-stu-id="b7ba0-120">This allows you to define a single business process that can be used to interact with multiple trading partners.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7ba0-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7ba0-121">See Also</span></span>  
 <span data-ttu-id="b7ba0-122">[XLANG s 陳述式](../core/xlang-s-statements.md) </span><span class="sxs-lookup"><span data-stu-id="b7ba0-122">[XLANG-s Statements](../core/xlang-s-statements.md) </span></span>  
 <span data-ttu-id="b7ba0-123">[XLANG 的變數和運算子](../core/xlang-s-variables-and-operators.md) </span><span class="sxs-lookup"><span data-stu-id="b7ba0-123">[XLANG-s Variables and Operators](../core/xlang-s-variables-and-operators.md) </span></span>  
 <span data-ttu-id="b7ba0-124">[XLANG 的運算式](../core/xlang-s-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="b7ba0-124">[XLANG-s Expressions](../core/xlang-s-expressions.md) </span></span>  
 <span data-ttu-id="b7ba0-125">[XLANG s 保留字](../core/xlang-s-reserved-words.md) </span><span class="sxs-lookup"><span data-stu-id="b7ba0-125">[XLANG-s Reserved Words](../core/xlang-s-reserved-words.md) </span></span>  
 [<span data-ttu-id="b7ba0-126">XLANG-s 至 BPEL4WS 型別轉換</span><span class="sxs-lookup"><span data-stu-id="b7ba0-126">XLANG-s to BPEL4WS Type Conversions</span></span>](../core/xlang-s-to-bpel4ws-type-conversions.md)