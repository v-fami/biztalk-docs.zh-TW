---
title: "Siebel 的 EXEC 陳述式的語法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- EXEC statement, syntax for
- Data Provider for Siebel, EXEC statement
ms.assetid: c5534102-bf37-4b39-83ab-e09483744c4d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d18481b206b1be7e0062762c1844305fc36e10f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="syntax-for-an-exec-statement-in-siebel"></a><span data-ttu-id="30680-102">Siebel 中 EXEC 陳述式語法</span><span class="sxs-lookup"><span data-stu-id="30680-102">Syntax for an EXEC Statement in Siebel</span></span>
<span data-ttu-id="30680-103">使用[!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)]，ADO.NET 用戶端也可以執行 EXEC 作業[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="30680-103">Using the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], ADO.NET clients can also perform an EXEC operation on the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="30680-104">EXEC 陳述式的語法為：</span><span class="sxs-lookup"><span data-stu-id="30680-104">The syntax for the EXEC statement is:</span></span>  
  
```  
EXEC  
<Business Service name>.<Business Service method>  
\<value 1..n>,  
@parameter 1..n [OUTPUT],  
@parameter 1..n = <value>  
  
```  
  
 <span data-ttu-id="30680-105">在上述語法中，`\<value 1..n>`代表一組未命名的參數。</span><span class="sxs-lookup"><span data-stu-id="30680-105">In the preceding syntax, `\<value 1..n>` represents a set of unnamed parameters.</span></span> <span data-ttu-id="30680-106">這些是硬式編碼值。</span><span class="sxs-lookup"><span data-stu-id="30680-106">These are hard-coded values.</span></span> <span data-ttu-id="30680-107">它們通常代表在參數中。</span><span class="sxs-lookup"><span data-stu-id="30680-107">They usually represent IN parameters.</span></span>  <span data-ttu-id="30680-108">它們也可能代表 INOUT 參數。</span><span class="sxs-lookup"><span data-stu-id="30680-108">They can also represent INOUT parameters.</span></span> <span data-ttu-id="30680-109">不過，如果 INOUT 參數使用硬式編碼值，該參數相關聯的輸出值無法擷取在 EXEC 陳述式執行之後。</span><span class="sxs-lookup"><span data-stu-id="30680-109">However, if a hard-coded value is used for an INOUT parameter, the output value associated with that parameter cannot be retrieved after the EXEC statement is executed.</span></span>  
  
 <span data-ttu-id="30680-110">`@parameter 1..n`語法代表一組具名參數，它可以是 IN、 INOUT、 參數或 OUT 參數。</span><span class="sxs-lookup"><span data-stu-id="30680-110">The `@parameter 1..n` syntax represents a set of named parameters, which can be IN, INOUT, or OUT parameters.</span></span> <span data-ttu-id="30680-111">輸出參數後面必須接著**輸出**關鍵字。</span><span class="sxs-lookup"><span data-stu-id="30680-111">The output parameters must be followed by the **OUTPUT** keyword.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30680-112">**輸出**關鍵字只能用於與 OUT 參數，而不是使用 INOUT 參數。</span><span class="sxs-lookup"><span data-stu-id="30680-112">The **OUTPUT** keyword must only be used with OUT parameters and not with INOUT parameters.</span></span>  
  
 <span data-ttu-id="30680-113">若要指定參數值的內嵌，使用`@parameter 1..n = <value>`語法。</span><span class="sxs-lookup"><span data-stu-id="30680-113">To specify parameter values inline, use the `@parameter 1..n = <value>` syntax.</span></span>  
  
 <span data-ttu-id="30680-114">所有參數必須都是以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="30680-114">All parameters must be comma-separated.</span></span>  
  
 <span data-ttu-id="30680-115">EXEC 陳述式的範例如下：</span><span class="sxs-lookup"><span data-stu-id="30680-115">The following are examples of EXEC statements:</span></span>  
  
```  
EXEC ExtractDataService.Echo @In, @InOut, @Out OUTPUT  
  
EXEC ExtractDataService.Echo 'InputValue', @InOut, @Out OUTPUT  
  
EXEC ExtractDataService.Echo @InOut, @Out OUTPUT, @In='InputValue'  
  
EXEC ExtractDataService.Echo 'InputValue', @Out OUTPUT, @InOut='InputValue'  
  
```  
  
> [!NOTE]
>  <span data-ttu-id="30680-116">每個參數名稱 (例如`@In`在上述範例中) 必須符合對應的引數名稱，在 Siebel 商務服務方法。</span><span class="sxs-lookup"><span data-stu-id="30680-116">Every parameter name (like `@In` in the preceding example) must match the corresponding argument name in the Siebel Business Service method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30680-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30680-117">See Also</span></span>  
 [<span data-ttu-id="30680-118">使用.NET Framework Data Provider for Siebel eBusiness 應用程式</span><span class="sxs-lookup"><span data-stu-id="30680-118">Use the .NET Framework Data Provider for Siebel eBusiness Applications</span></span>](../../adapters-and-accelerators/adapter-siebel/use-the-net-framework-data-provider-for-siebel-ebusiness-applications.md)