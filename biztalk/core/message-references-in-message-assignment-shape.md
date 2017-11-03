---
title: "訊息 訊息指派圖形中的參考 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, code samples
- code samples, messages
- messages, objects
ms.assetid: 428f7eb8-001e-4147-b1c8-f9bb6f3a80f9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b834eefa991b6cad89a04a836f63d1b9af73fc04
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="message-references-in-message-assignment-shape"></a><span data-ttu-id="3a099-102">訊息指派圖形中的訊息參考</span><span class="sxs-lookup"><span data-stu-id="3a099-102">Message References in Message Assignment Shape</span></span>
<span data-ttu-id="3a099-103">當您首次將以 .NET 為基礎的物件指派到訊息或訊息部分時，該訊息便會保留並維護物件的參考。</span><span class="sxs-lookup"><span data-stu-id="3a099-103">When you first assign a .NET-based object to a message or message part, that message holds and maintains a reference to the object.</span></span>  
  
 <span data-ttu-id="3a099-104">為了效率和延展性，協調流程引擎不會執行 「 深層複製 」 物件的： 也就是說，它不會複製物件的整個內容的訊息。</span><span class="sxs-lookup"><span data-stu-id="3a099-104">For efficiency and scalability, the orchestration engine does not do a "deep copy" of the object: that is, it does not copy the entire contents of the object to the message.</span></span>  
  
 <span data-ttu-id="3a099-105">如果您接著將物件指派到另一個訊息或訊息部分，針對原始物件的任何修改都會造成第二個訊息或訊息部分的修改。</span><span class="sxs-lookup"><span data-stu-id="3a099-105">If you subsequently assign the object to another message or message part, any modifications to the original results in modifications to the second message or message part.</span></span> <span data-ttu-id="3a099-106">您應該避免這種做法，因為結果會是無法預期的。</span><span class="sxs-lookup"><span data-stu-id="3a099-106">You should avoid this practice, because results are unpredictable.</span></span>  
  
 <span data-ttu-id="3a099-107">如果需要讓第二個訊息具有物件的不同複本，您就應該將第一個訊息或訊息部分指派給第二個訊息或訊息部分。</span><span class="sxs-lookup"><span data-stu-id="3a099-107">If you need your second message to have a distinct copy of the object, you should assign the first message or message part to the second message or message part.</span></span>  
  
 <span data-ttu-id="3a099-108">請設想下列範例：</span><span class="sxs-lookup"><span data-stu-id="3a099-108">Consider the following example:</span></span>  
  
 <span data-ttu-id="3a099-109">錯誤方式：</span><span class="sxs-lookup"><span data-stu-id="3a099-109">Wrong way:</span></span>  
  
```  
myMsg1 = myObj; // assign the first message  
myMsg2 = myObj; // assign the second message (wrong!)  
myMsg2.myInt = 100; // modify the second  
myMsg1.myInt = 5;  
```  
  
 <span data-ttu-id="3a099-110">在此情況下，myMsg2.myInt 已經遭到覆寫，而且現在具有 5 的值。</span><span class="sxs-lookup"><span data-stu-id="3a099-110">In this case, myMsg2.myInt has been overwritten, and now has the value 5.</span></span>  
  
 <span data-ttu-id="3a099-111">正確方式：</span><span class="sxs-lookup"><span data-stu-id="3a099-111">Right way:</span></span>  
  
```  
myMsg1 = myObj; // assign the first message  
myMsg2 = myMsg1; // assign the second message (right!)  
myMsg2.myInt = 100; // modify the second  
myMsg1.myInt = 5;  
```  
  
 <span data-ttu-id="3a099-112">在此情況下，myMsg2.myInt 依然具有 100 的值，這點與預期相同。</span><span class="sxs-lookup"><span data-stu-id="3a099-112">In this case, myMsg2.myInt still has the value 100, as expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a099-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a099-113">See Also</span></span>  
 [<span data-ttu-id="3a099-114">建構訊息</span><span class="sxs-lookup"><span data-stu-id="3a099-114">Constructing Messages</span></span>](../core/constructing-messages.md)