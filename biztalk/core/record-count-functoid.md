---
title: 記錄計數運算質 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Max Occurs property
- Record Count functoids
ms.assetid: e6aab13f-afbe-4401-abbe-020570e2ff16
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87653709bf5d52c21537064bad286078ad625cf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268742"
---
# <a name="record-count-functoid"></a><span data-ttu-id="9507c-102">記錄計數運算質</span><span class="sxs-lookup"><span data-stu-id="9507c-102">Record Count Functoid</span></span>
<span data-ttu-id="9507c-103">**記錄計數**運算質會計算在輸入執行個體訊息中的記錄。</span><span class="sxs-lookup"><span data-stu-id="9507c-103">The **Record Count** functoid counts records in the input instance message.</span></span>  
  
 <span data-ttu-id="9507c-104">**記錄計數**運算質有一個輸入和一個輸出。</span><span class="sxs-lookup"><span data-stu-id="9507c-104">The **Record Count** functoid has one input and one output.</span></span> <span data-ttu-id="9507c-105">輸入為來源結構描述中迴圈記錄的連結。</span><span class="sxs-lookup"><span data-stu-id="9507c-105">The input is a link from a looping record in the source schema.</span></span> <span data-ttu-id="9507c-106">輸出**記錄計數**運算質是實際輸入執行個體訊息中迴圈記錄的計數。</span><span class="sxs-lookup"><span data-stu-id="9507c-106">The output of the **Record Count** functoid is the count of the looping record in an actual input instance message.</span></span>  
  
 <span data-ttu-id="9507c-107">迴圈記錄對應到輸入執行個體訊息中重複次數無法預測的項目。</span><span class="sxs-lookup"><span data-stu-id="9507c-107">Looping records correspond to elements that repeat an unpredictable number of times in an input instance message.</span></span> <span data-ttu-id="9507c-108">例如，在採購單，**項目**項目可能會發生多次。</span><span class="sxs-lookup"><span data-stu-id="9507c-108">For example, in a purchase order, the **Item** element might occur many times.</span></span> <span data-ttu-id="9507c-109">此外，**項目**項目可能包含產品、 描述、 價格以及數量。</span><span class="sxs-lookup"><span data-stu-id="9507c-109">And, the **Item** element might include products, descriptions, prices, and quantities.</span></span> <span data-ttu-id="9507c-110">下列程式碼是此類訂單的簡化範例。</span><span class="sxs-lookup"><span data-stu-id="9507c-110">The following code is a simplified example of such a purchase order.</span></span>  
  
```  
<ns0:PurchaseOrder xmlns:ns0="http://RecordFunctoid.PurchaseOrder">  
    <From>Kevin F. Browne</From>  
    <To>Northwind Traders</To>  
    <LineItems>  
        <Item>  
            <Product>Laptop Computer</Product>  
            <Description>Thin profile laptop</Description>  
            <Price>1999.95</Price>  
            <Quantity>1</Quantity>  
        </Item>  
        <Item>  
            <Product>Monitor Swipes</Product>  
            <Description>Disposable monitor swipes</Description>  
            <Price>3.95</Price>  
            <Quantity>10</Quantity>  
        </Item>  
    </LineItems>  
</ns0:PurchaseOrder>  
```  
  
 <span data-ttu-id="9507c-111">**Max Occurs**屬性**項目**記錄設定為 unbounded。</span><span class="sxs-lookup"><span data-stu-id="9507c-111">The **Max Occurs** property for the **Item** record is set as unbounded.</span></span> <span data-ttu-id="9507c-112">這表示**項目**記錄會重複，而 BizTalk 對應工具會編譯為迴圈這筆記錄。</span><span class="sxs-lookup"><span data-stu-id="9507c-112">This indicates that the **Item** record loops, and BizTalk Mapper compiles this record as a loop.</span></span>  
  
 <span data-ttu-id="9507c-113">假設您想要尋找的總數**項目**採購訂單輸入執行個體中的項目訊息，並將結果放在輸出執行個體訊息中的欄位。</span><span class="sxs-lookup"><span data-stu-id="9507c-113">Suppose you want to find the total number of **Item** elements in the purchase order input instance message and place the result in a field in the output instance message.</span></span>  
  
 <span data-ttu-id="9507c-114">下圖顯示**記錄計數**運算質，計算的內送訂單中的項目數目，並將該值放入**ItemCount**欄位**SummedPO**輸出執行個體訊息。</span><span class="sxs-lookup"><span data-stu-id="9507c-114">The following figure shows a **Record Count** functoid that counts the number of items in an incoming purchase order and puts that value in the **ItemCount** field in the **SummedPO** output instance message.</span></span>  
  
 <span data-ttu-id="9507c-115">![地圖顯示的記錄計數運算質使用。](../core/media/recordcountfunctoid.gif "recordcountfunctoid")</span><span class="sxs-lookup"><span data-stu-id="9507c-115">![Map showing the use of the record count functoid.](../core/media/recordcountfunctoid.gif "recordcountfunctoid")</span></span>  
<span data-ttu-id="9507c-116">記錄計數運算質對應</span><span class="sxs-lookup"><span data-stu-id="9507c-116">Record Count Functoid Map</span></span>  
  
 <span data-ttu-id="9507c-117">請注意， **Max Occurs**屬性**項目**會記錄**unbounded**。</span><span class="sxs-lookup"><span data-stu-id="9507c-117">Notice that the **Max Occurs** property for the **Item** record would be **unbounded**.</span></span> <span data-ttu-id="9507c-118">這表示**項目**記錄會重複，而 BizTalk 對應工具會編譯為迴圈這筆記錄。</span><span class="sxs-lookup"><span data-stu-id="9507c-118">This indicates that the **Item** record loops, and BizTalk Mapper compiles this record as a loop.</span></span>  
  
 <span data-ttu-id="9507c-119">如上述範例訂單執行個體訊息，其中包含兩個**項目**項目、 值**ItemCount**欄位將會設定為 2。</span><span class="sxs-lookup"><span data-stu-id="9507c-119">For the preceding sample purchase order instance message, which contained two **Item** elements, the value of the **ItemCount** field will be set to 2.</span></span>  
  
```  
<ns0:SummedPO xmlns:ns0="http://RecordCountFunctoid.SummedPO">  
    <From>Kevin F. Browne</From>  
    <To>Northwind Traders</To>  
    <POTotal>2039.45</POTotal>  
    <ItemCount>2</ItemCount>  
</ns0:SummedPO>  
```  
  
> [!NOTE]
>  <span data-ttu-id="9507c-120">您也可以使用**記錄計數**運算質計算重複的欄位項目。</span><span class="sxs-lookup"><span data-stu-id="9507c-120">You can also use the **Record Count** functoid to count repeating field elements.</span></span> <span data-ttu-id="9507c-121">並不僅限計算記錄。</span><span class="sxs-lookup"><span data-stu-id="9507c-121">It is not restricted to records.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9507c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9507c-122">See Also</span></span>  
 <span data-ttu-id="9507c-123">[如何新增記錄計數運算質至對應](../core/how-to-add-record-count-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="9507c-123">[How to Add Record Count Functoids to a Map](../core/how-to-add-record-count-functoids-to-a-map.md) </span></span>  
 <span data-ttu-id="9507c-124">[進階運算質](../core/advanced-functoids.md) </span><span class="sxs-lookup"><span data-stu-id="9507c-124">[Advanced Functoids](../core/advanced-functoids.md) </span></span>  
 <span data-ttu-id="9507c-125">[索引運算質](../core/index-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="9507c-125">[Index Functoid](../core/index-functoid.md) </span></span>  
 <span data-ttu-id="9507c-126">[反覆項目運算質](../core/iteration-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="9507c-126">[Iteration Functoid](../core/iteration-functoid.md) </span></span>  
 [<span data-ttu-id="9507c-127">迴圈運算質</span><span class="sxs-lookup"><span data-stu-id="9507c-127">Looping Functoid</span></span>](../core/looping-functoid.md)