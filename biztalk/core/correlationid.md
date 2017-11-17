---
title: "CorrelationID |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4faf210-7e7f-450d-8bb1-84d3d31c3022
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1192de4a49c300220ce0b297bbc1ee02ce64c6dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="correlationid"></a><span data-ttu-id="44f6b-102">CorrelationID</span><span class="sxs-lookup"><span data-stu-id="44f6b-102">CorrelationID</span></span>
<span data-ttu-id="44f6b-103">`CorrelationID` 項目用來指定訊息的相互關聯識別碼。</span><span class="sxs-lookup"><span data-stu-id="44f6b-103">The `CorrelationID` element is used to specify a correlation ID for a message.</span></span>  
  
## <a name="format"></a><span data-ttu-id="44f6b-104">格式</span><span class="sxs-lookup"><span data-stu-id="44f6b-104">Format</span></span>  
 <span data-ttu-id="44f6b-105">`CorrelationID` 項目由一個 `Expression` 項目組成，後者使用一或多個 `Operation` 項目以指定做為相互關聯識別碼的字串。</span><span class="sxs-lookup"><span data-stu-id="44f6b-105">The `CorrelationID` element consists of an `Expression` element that uses one or more `Operation` elements to specify the string to use as the correlation ID.</span></span>  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <!-- Operations -->  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
## <a name="remarks"></a><span data-ttu-id="44f6b-106">備註</span><span class="sxs-lookup"><span data-stu-id="44f6b-106">Remarks</span></span>  
 <span data-ttu-id="44f6b-107">相互關聯識別碼運算式中不允許執行下列常見的運算：</span><span class="sxs-lookup"><span data-stu-id="44f6b-107">The following common operations are not allowed in correlation ID expressions:</span></span>  
  
-   <span data-ttu-id="44f6b-108">And</span><span class="sxs-lookup"><span data-stu-id="44f6b-108">And</span></span>  
  
-   <span data-ttu-id="44f6b-109">等於</span><span class="sxs-lookup"><span data-stu-id="44f6b-109">Equals</span></span>  
  
## <a name="example"></a><span data-ttu-id="44f6b-110">範例</span><span class="sxs-lookup"><span data-stu-id="44f6b-110">Example</span></span>  
 <span data-ttu-id="44f6b-111">下列 Workflow Foundation (WF) 攔截器範例組態區塊會使用 "OrderNum" 來建立相互關聯識別碼。</span><span class="sxs-lookup"><span data-stu-id="44f6b-111">The following Workflow Foundation (WF) interceptor sample configuration block uses "OrderNum" to establish a correlation ID.</span></span> <span data-ttu-id="44f6b-112">您可以使用 WF 和常見的運算來建置複雜運算式，以建構工作流程的適當相互關聯識別碼。</span><span class="sxs-lookup"><span data-stu-id="44f6b-112">Using the WF and common operations, you can build sophisticated expressions to construct an appropriate correlation ID for your workflow.</span></span>  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <wf:Operation Name="GetWorkflowProperty">  
      <wf:Argument>OrderNum</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
 <span data-ttu-id="44f6b-113">對於 Windows Communication Foundation (WCF) 應用程式，您可以使用 WCF 專有和常見的運算以建構相互關聯識別碼。</span><span class="sxs-lookup"><span data-stu-id="44f6b-113">For Windows Communication Foundation (WCF) applications, you can use WCF-specific and common operations to construct a correlation ID.</span></span> <span data-ttu-id="44f6b-114">下列範例會使用**XPath**運算和 XPath，從使用做為相互關聯識別碼的訊息擷取信用卡號碼：</span><span class="sxs-lookup"><span data-stu-id="44f6b-114">The following sample uses the **XPath** operation and XPath to retrieve a credit card number from a message for use as a correlation ID:</span></span>  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <wcf:Operation Name ="XPath">  
      <wcf:Argument>//s:Body/creditCard:CreditCardNumber</wcf:Argument>  
    </wcf:Operation>  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
## <a name="see-also"></a><span data-ttu-id="44f6b-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44f6b-115">See Also</span></span>  
 [<span data-ttu-id="44f6b-116">攔截器 OnEvent 項目</span><span class="sxs-lookup"><span data-stu-id="44f6b-116">Interceptor OnEvent Element</span></span>](../core/interceptor-onevent-element.md)