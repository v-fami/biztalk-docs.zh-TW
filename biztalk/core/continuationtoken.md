---
title: "ContinuationToken |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d4911fc-c6fb-4628-9177-bd723d4d8ebc
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54cf9b9326661925f2d55bacd2fb22d02f565f89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="continuationtoken"></a><span data-ttu-id="5126c-102">ContinuationToken</span><span class="sxs-lookup"><span data-stu-id="5126c-102">ContinuationToken</span></span>
<span data-ttu-id="5126c-103">接續 Token 是用來讓 BAM 基礎結構內的異質資訊相互關聯。</span><span class="sxs-lookup"><span data-stu-id="5126c-103">A continuation token is used to correlate heterogeneous information within the BAM infrastructure.</span></span> <span data-ttu-id="5126c-104">請參考建構下列類型訊息的商務程序：</span><span class="sxs-lookup"><span data-stu-id="5126c-104">Consider a business process that constructs the following types of messages:</span></span>  
  
-   <span data-ttu-id="5126c-105">由訂單編號識別的訂單</span><span class="sxs-lookup"><span data-stu-id="5126c-105">Purchase order identified by a purchase order number</span></span>  
  
-   <span data-ttu-id="5126c-106">由銷售訂單編號識別的銷售訂單</span><span class="sxs-lookup"><span data-stu-id="5126c-106">Sales order identified by a sales order number</span></span>  
  
-   <span data-ttu-id="5126c-107">由送貨單編號識別的送貨單</span><span class="sxs-lookup"><span data-stu-id="5126c-107">Shipping order identified by a shipping order number</span></span>  
  
 <span data-ttu-id="5126c-108">在這個過程中，有三個重要的識別項： 採購單識別碼、 銷售訂單識別碼和傳送順序識別碼。</span><span class="sxs-lookup"><span data-stu-id="5126c-108">In this process, there are three important identifiers: purchase order ID, sales order ID and shipping order ID.</span></span> <span data-ttu-id="5126c-109">這三個識別碼每一個都表示原始訂單存留期間的一個重要事件，但是彼此之間無法直接關聯。</span><span class="sxs-lookup"><span data-stu-id="5126c-109">Each of these identifiers signals an important event in the lifetime of the original order, but they cannot be directly correlated.</span></span> <span data-ttu-id="5126c-110">若要追蹤與訂單相關的事件，就必須識別訊息之間常見的資訊，以協助 BAM 追蹤基礎結構正確地將這些事件相互關聯。</span><span class="sxs-lookup"><span data-stu-id="5126c-110">To track events related to a purchase order, the information that is common between the messages must be identified to help the BAM tracking infrastructure accurately correlate the events.</span></span>  
  
## <a name="format"></a><span data-ttu-id="5126c-111">格式</span><span class="sxs-lookup"><span data-stu-id="5126c-111">Format</span></span>  
 <span data-ttu-id="5126c-112">接續 Token 是由運算式項目和一或多項運算所組成：</span><span class="sxs-lookup"><span data-stu-id="5126c-112">A continuation token consists of an expression element and one or more operations:</span></span>  
  
```  
<ic:ContinuationToken>  
  <ic:Expression>  
    <!-- Operations -->  
  </ic:Expression>  
</ic:ContinuationToken>  
```  
  
## <a name="remarks"></a><span data-ttu-id="5126c-113">備註</span><span class="sxs-lookup"><span data-stu-id="5126c-113">Remarks</span></span>  
 <span data-ttu-id="5126c-114">ContinuationToken 運算式中不允許執行下列常見的運算：</span><span class="sxs-lookup"><span data-stu-id="5126c-114">The following common operations are not allowed in ContinuationToken expressions:</span></span>  
  
-   <span data-ttu-id="5126c-115">And</span><span class="sxs-lookup"><span data-stu-id="5126c-115">And</span></span>  
  
-   <span data-ttu-id="5126c-116">等於</span><span class="sxs-lookup"><span data-stu-id="5126c-116">Equals</span></span>  
  
 <span data-ttu-id="5126c-117">[WF/WCF 中「運算」章節的標頭應有類似的圖表和其他圖表 (如有需要)]</span><span class="sxs-lookup"><span data-stu-id="5126c-117">[Operations section header in WF/WCF should have similar chart and other charts as needed]</span></span>  
  
## <a name="example"></a><span data-ttu-id="5126c-118">範例</span><span class="sxs-lookup"><span data-stu-id="5126c-118">Example</span></span>  
 <span data-ttu-id="5126c-119">此範例中會使用 `GetWorkflowProperty` 從工作流程擷取 WF 程序的接續 Token。</span><span class="sxs-lookup"><span data-stu-id="5126c-119">In this example, a continuation token for a WF process is retrieved from the workflow by using `GetWorkflowProperty`.</span></span> <span data-ttu-id="5126c-120">在此，開發人員決定在工作流程中使用自訂程式碼支援接續，可能是因為判斷接續 Token 的程序涉及兩或三個以上的運算式，且可能倚賴外部資料。</span><span class="sxs-lookup"><span data-stu-id="5126c-120">Here the developer decided to provide support for continuation in the workflow by using custom code, probably because the process for determining the continuation token involves more than two or three expressions and may rely on external data.</span></span>  
  
```  
<ic:ContinuationToken>  
  <ic:Expression>  
    <wf:Operation Name="GetWorkflowProperty">  
      <wf:Argument>ContinuationToken</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:ContinuationToken>  
```  
  
 <span data-ttu-id="5126c-121">您可以選擇在新的 WF 或 WCF 應用程式中提供類似的功能，或者如果使用運算式作業建立 Token 十分容易，則可避免撰寫額外的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5126c-121">You may choose to provide similar functionality in your new WF or WCF applications or, if the token is easy to establish using expression operations, you can avoid writing additional code.</span></span>  
  
 <span data-ttu-id="5126c-122">下列範例會使用建立 WCF 程序的接續 token **XPath**從目前訊息擷取信用卡號碼作業和**常數**和**串連**作業前面加上要擷取的數字的字串"CID_":</span><span class="sxs-lookup"><span data-stu-id="5126c-122">The following example establishes a continuation token for a WCF process by using an **XPath** operation to retrieve the credit card number from the current message and the **constant** and **concatenate** operations to prepend the string "CID_" to the retrieved number:</span></span>  
  
```  
<ic:ContinuationToken>  
  <ic:Expression>  
    <ic:Operation Name="Constant">  
      <ic:Argument>CID_</ic:Argument>  
    </ic:Operation>  
    <wcf:Operation Name="XPath">  
      <wcf:Argument>//Purchase/Payment/CreditCardNumber</wcf:Argument>  
    </wcf:Operation>  
    <ic:Operation Name="Concatenate" />  
  </ic:Expression>  
</ic:ContinuationToken>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5126c-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5126c-123">See Also</span></span>  
 [<span data-ttu-id="5126c-124">攔截器 OnEvent 項目</span><span class="sxs-lookup"><span data-stu-id="5126c-124">Interceptor OnEvent Element</span></span>](../core/interceptor-onevent-element.md)