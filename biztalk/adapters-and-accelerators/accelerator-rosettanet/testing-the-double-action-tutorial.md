---
title: "測試雙向動作教學課程 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- double action tutorial, testing solutions
- testing solutions
ms.assetid: e5bc66e6-333e-4d94-ae1e-345ab45c83e5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 807308623780e029fff571a36dc703de0f79460d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="testing-the-double-action-tutorial"></a><span data-ttu-id="7c656-102">測試雙向動作教學課程</span><span class="sxs-lookup"><span data-stu-id="7c656-102">Testing the Double Action Tutorial</span></span>
<span data-ttu-id="7c656-103">在本節中，您將使用在前面章節中建立的 Contoso 與 Fabrikam 解決方案，以測試四種不同的「夥伴介面程序」(PIP)：0C2、0C4、3A2 和 3A4。</span><span class="sxs-lookup"><span data-stu-id="7c656-103">In this section, you use the Contoso and Fabrikam solutions that you created in the earlier sections to test four different Partner Interface Processes (PIPs): 0C2, 0C4, 3A2 and 3A4.</span></span> <span data-ttu-id="7c656-104">您將使用 Fabrikam 電腦上的 LOBWebApplication 來產生要求。</span><span class="sxs-lookup"><span data-stu-id="7c656-104">You use the LOBWebApplication on the Fabrikam computer to make the request.</span></span> <span data-ttu-id="7c656-105">系統將使用增強的通訊管道，傳送要求到 Contoso 電腦。</span><span class="sxs-lookup"><span data-stu-id="7c656-105">The system will send the request using an enhanced communication channel to the Contoso computer.</span></span> <span data-ttu-id="7c656-106">「雙向動作」協調流程將根據您使用的 PIP 產生適當的回應。</span><span class="sxs-lookup"><span data-stu-id="7c656-106">The Double Action orchestration will generate an appropriate response based on the PIP you use.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7c656-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="7c656-107">In This Section</span></span>  
  
-   [<span data-ttu-id="7c656-108">步驟 1： 提交 0 C 2 要求</span><span class="sxs-lookup"><span data-stu-id="7c656-108">Step 1: Submitting a 0C2 Request</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-1-submitting-a-0c2-request.md)  
  
-   [<span data-ttu-id="7c656-109">步驟 2： 提交 0 C 4 查詢</span><span class="sxs-lookup"><span data-stu-id="7c656-109">Step 2: Submitting a 0C4 Query</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-2-submitting-a-0c4-query.md)  
  
-   [<span data-ttu-id="7c656-110">步驟 3： 提交 3A2 要求</span><span class="sxs-lookup"><span data-stu-id="7c656-110">Step 3: Submitting a 3A2 Request</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-submitting-a-3a2-request.md)  
  
-   [<span data-ttu-id="7c656-111">步驟 4： 提交 3A4 要求</span><span class="sxs-lookup"><span data-stu-id="7c656-111">Step 4: Submitting a 3A4 Request</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-4-submitting-a-3a4-request.md)