---
title: "如何使用運算式動態地轉換訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48387d97-9312-4df5-b614-727ea9035bf8
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b9d16c38fefb4e2732bd05f7c3489acaa8ca645
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-expressions-to-dynamic-transform-messages"></a><span data-ttu-id="1cffc-102">如何使用運算式動態地轉換訊息</span><span class="sxs-lookup"><span data-stu-id="1cffc-102">How to Use Expressions to Dynamic Transform Messages</span></span>
<span data-ttu-id="1cffc-103">您可使用運算式在協調流程中動態地轉換訊息。</span><span class="sxs-lookup"><span data-stu-id="1cffc-103">You can use expressions to dynamic transform messages in your orchestration.</span></span> <span data-ttu-id="1cffc-104">XLANG 公開可以呼叫內的轉換方法**訊息指派**圖形內**建構訊息**圖形。</span><span class="sxs-lookup"><span data-stu-id="1cffc-104">XLANG exposes a transform method that can be called from within a **Message Assignment** shape inside of a **Construct Message** shape.</span></span> <span data-ttu-id="1cffc-105">這是相同的方法時，會呼叫**轉換**圖形會使用，但可讓您以程式設計方式轉換訊息使用您指定在協調流程中的對應。</span><span class="sxs-lookup"><span data-stu-id="1cffc-105">This is the same method that is called when a **Transform** shape is used, but allows you to programmatically transform the messages using the map you designated within the orchestration.</span></span> <span data-ttu-id="1cffc-106">當您進行類型不可知的訊息處理時，這點便會相當有用。</span><span class="sxs-lookup"><span data-stu-id="1cffc-106">This is useful when you are doing type-agnostic message processing.</span></span> <span data-ttu-id="1cffc-107">例如，如果您有商務程序需要從一系列對應中選擇，以便根據接收之輸入訊息所提供的參數轉換輸入訊息，可使用「運算式」圖形中的轉換方法來進行，而且同時可維持整體商務程序的完整。</span><span class="sxs-lookup"><span data-stu-id="1cffc-107">For example, if you have a business process that needs to choose from a series of maps to transform inbound messages based on the parameters provided by the received inbound messages, you can achieve this by using the transform method in the Expression shape while maintaining your overall business process intact.</span></span>  
  
## <a name="transforming-messages"></a><span data-ttu-id="1cffc-108">轉換訊息</span><span class="sxs-lookup"><span data-stu-id="1cffc-108">Transforming messages</span></span>  
 <span data-ttu-id="1cffc-109">您可以使用下列範例程式碼，以程式設計方式轉換中的訊息**訊息指派**圖形：</span><span class="sxs-lookup"><span data-stu-id="1cffc-109">You can use the following sample code to programmatically transform the messages in the **Message Assignment** shape:</span></span>  
  
```  
MyMapType = typeof(MyMapName);  
transform(MyOutputMsg) = MyMapType(MyInputMsg);  
```  
  
 <span data-ttu-id="1cffc-110">在此範例中，MyMapType 宣告為類型的變數**System.Type**協調流程中。</span><span class="sxs-lookup"><span data-stu-id="1cffc-110">In this example, MyMapType is declared as a variable of type **System.Type** in the orchestration.</span></span> <span data-ttu-id="1cffc-111">MyMapName 是已經在您的 BizTalk 專案中建立之對應的名稱。</span><span class="sxs-lookup"><span data-stu-id="1cffc-111">MyMapName is the name of a map that was already created in your BizTalk project.</span></span> <span data-ttu-id="1cffc-112">如果您要參考個別 BizTalk 組件中的對應，您便需要在 BizTalk 專案中參考該組件。</span><span class="sxs-lookup"><span data-stu-id="1cffc-112">If you would like to reference a map that is in a separate BizTalk assembly, you will need to reference that assembly in your BizTalk project.</span></span> <span data-ttu-id="1cffc-113">MyInputMsg 是來源訊息，而 MyOutputMsg 則是目的訊息。</span><span class="sxs-lookup"><span data-stu-id="1cffc-113">MyInputMsg is the source message and MyOutputMsg is the destination message.</span></span> <span data-ttu-id="1cffc-114">如果您的對應使用多個來源訊息，您就可以使用下列範例程式碼來轉換這些訊息：</span><span class="sxs-lookup"><span data-stu-id="1cffc-114">If your map takes multiple source messages, then you can use the following sample code to transform the messages:</span></span>  
  
```  
MyMapType = typeof(MyMapName);  
transform(MyOutputMsg) = MyMapType(MyInputMsg1, MyInputMsg2);  
```  
  
> [!NOTE]
>  <span data-ttu-id="1cffc-115">如果您有多個來源訊息，則必須根據在對應中指示的輸入訊息部分編號，將訊息分別依序放置在運算式中。</span><span class="sxs-lookup"><span data-stu-id="1cffc-115">If you have multiple source messages, they must be placed in order in the expression with respect to the input message part number indicated in the map.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1cffc-116">當動態地轉換「運算式」圖形中的訊息時，建議您在使用者程式碼中寫入快取，以便快取已編譯的對應，然後使用「運算式」圖形中的快取，在執行訊息轉換之前擷取對應。</span><span class="sxs-lookup"><span data-stu-id="1cffc-116">When dynamic transforming messages in the Expression shape, we recommend that you write a cache in user code for caching the compiled maps, and then use the cache in the Expression shape to retrieve the maps before performing the message transformation.</span></span> <span data-ttu-id="1cffc-117">如果您沒有快取對應，便有可能看到 Common Language Runtime (CLR) 記憶體顯著地成長。</span><span class="sxs-lookup"><span data-stu-id="1cffc-117">If you are not caching the maps, it is possible to see Common Language Runtime (CLR) memory grow significantly.</span></span> <span data-ttu-id="1cffc-118">動態對應需要 .NET Runtime 執行程式碼存取檢查，讓 .NET Evidence 物件放置在每個轉換的「大型物件堆積」，而且在協調流程完成之前，都不會處置這個物件。</span><span class="sxs-lookup"><span data-stu-id="1cffc-118">Dynamic mapping requires that the .NET Runtime perform code access check which results in a .NET Evidence object being placed in the Large Object Heap for each transformation and this object is not disposed of until the orchestration completes.</span></span> <span data-ttu-id="1cffc-119">因此，當有許多這些類型的轉換同時發生時，您便可能會看到記憶體使用的顯著增加，如此也會導致記憶體不足的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1cffc-119">Therefore, when there are a lot of these types of transforms occurring simultaneously, you may see the memory usage increase substantially which can also lead to the out of memory exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cffc-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cffc-120">See Also</span></span>  
 <span data-ttu-id="1cffc-121">[協調流程圖形](../core/orchestration-shapes.md) </span><span class="sxs-lookup"><span data-stu-id="1cffc-121">[Orchestration Shapes](../core/orchestration-shapes.md) </span></span>  
 [<span data-ttu-id="1cffc-122">使用 BizTalk 對應工具建立對應</span><span class="sxs-lookup"><span data-stu-id="1cffc-122">Creating Maps Using BizTalk Mapper</span></span>](../core/creating-maps-using-biztalk-mapper.md)