---
title: 附錄 c： 使用元件介面 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Enterprise Integration Points
- EIP
- component interfaces
ms.assetid: 2e3bc5ef-24ea-4e09-8e95-31feefaf5536
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df03df6a1e36fd988109ebe85913512916b4222e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968903"
---
# <a name="appendix-c-using-component-interfaces"></a><span data-ttu-id="3cffc-102">附錄 c： 使用元件介面</span><span class="sxs-lookup"><span data-stu-id="3cffc-102">Appendix C: Using Component Interfaces</span></span>
<span data-ttu-id="3cffc-103">本章節中的主題說明如何建立新的元件介面，以及如何修改現有元件介面，以便搭配 Microsoft BizTalk Adapter for PeopleSoft Enterprise 使用。</span><span class="sxs-lookup"><span data-stu-id="3cffc-103">The topics in this section describe how to create new component interfaces—and how to modify existing component interfaces—for use with Microsoft BizTalk Adapter for PeopleSoft Enterprise.</span></span> <span data-ttu-id="3cffc-104">這些主題也會說明如何套用安全性至這些元件介面，以及如何測試安全性。</span><span class="sxs-lookup"><span data-stu-id="3cffc-104">They also describe how to apply security to those component interfaces and how to test them.</span></span>  
  
 <span data-ttu-id="3cffc-105">您可以執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="3cffc-105">You can do the following:</span></span>  
  
- <span data-ttu-id="3cffc-106">搭配您的應用程式使用 PeopleSoft 提供的元件介面。</span><span class="sxs-lookup"><span data-stu-id="3cffc-106">Use component interfaces supplied by PeopleSoft with your application.</span></span>  
  
   <span data-ttu-id="3cffc-107">元件介面亦稱為 Enterprise Integration Points (EIP)。</span><span class="sxs-lookup"><span data-stu-id="3cffc-107">Component interfaces also are known as Enterprise Integration Points (EIP).</span></span>  
  
- <span data-ttu-id="3cffc-108">修改現有的元件介面。</span><span class="sxs-lookup"><span data-stu-id="3cffc-108">Modify an existing component interface.</span></span>  
  
- <span data-ttu-id="3cffc-109">建立新元件介面。</span><span class="sxs-lookup"><span data-stu-id="3cffc-109">Create a new component interface.</span></span>  
  
  <span data-ttu-id="3cffc-110">使用您的元件介面之前，必須先套用及測試安全性。</span><span class="sxs-lookup"><span data-stu-id="3cffc-110">Before using your component interface, you must apply and test security.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3cffc-111">本章節的目的在於提供有用的補充資訊，並不能取代 PeopleSoft 文件。</span><span class="sxs-lookup"><span data-stu-id="3cffc-111">This section is intended as a helpful supplement; it is not a substitute for PeopleSoft documentation.</span></span> <span data-ttu-id="3cffc-112">如需 PeopleSoft 元件介面完整與最新資訊，請參閱 PeopleSoft Online Library。</span><span class="sxs-lookup"><span data-stu-id="3cffc-112">For complete and up-to-date information about PeopleSoft component interfaces, see the PeopleSoft Online Library.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3cffc-113">本節內容</span><span class="sxs-lookup"><span data-stu-id="3cffc-113">In This Section</span></span>  
  
-   [<span data-ttu-id="3cffc-114">如何建立元件介面</span><span class="sxs-lookup"><span data-stu-id="3cffc-114">How to Create Component Interfaces</span></span>](../core/how-to-create-component-interfaces.md)  
  
-   [<span data-ttu-id="3cffc-115">元件介面中的標準方法</span><span class="sxs-lookup"><span data-stu-id="3cffc-115">Standard Methods in Component Interfaces</span></span>](../core/standard-methods-in-component-interfaces.md)  
  
-   [<span data-ttu-id="3cffc-116">如何協助保護元件介面</span><span class="sxs-lookup"><span data-stu-id="3cffc-116">How to Help Secure Component Interfaces</span></span>](../core/how-to-help-secure-component-interfaces.md)  
  
-   [<span data-ttu-id="3cffc-117">如何測試元件介面</span><span class="sxs-lookup"><span data-stu-id="3cffc-117">How to Test Component Interfaces</span></span>](../core/how-to-test-component-interfaces.md)