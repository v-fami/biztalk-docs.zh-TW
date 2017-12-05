---
title: "測試解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing solutions
- private process tutorial, testing solutions
ms.assetid: 90faf959-bac6-4695-8cb7-ecabe52baf1a
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7af2cab529344f499ff006a6cd99401ae63c4668
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="testing-the-solution"></a><span data-ttu-id="f9136-102">測試方案</span><span class="sxs-lookup"><span data-stu-id="f9136-102">Testing the Solution</span></span>
<span data-ttu-id="f9136-103">在本節中，您將測試完整的解決方案。</span><span class="sxs-lookup"><span data-stu-id="f9136-103">In this section, you test your complete solution.</span></span> <span data-ttu-id="f9136-104">您將使用在 Fabrikam 解決方案中建立的 LOBWebApplication 工具，提交 3A2 PIP 要求至 Contoso LOB 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f9136-104">You use the LOBWebApplication tool created in the Fabrikam solution to submit 3A2 PIP requests to the Contoso LOB application.</span></span> <span data-ttu-id="f9136-105">然後您建立的 Contoso 私用協調流程提交 Contoso 3A2 價格與可用性要求至 ERP 系統，以便讓 BizTalk Server 使用 SQL 配接器。</span><span class="sxs-lookup"><span data-stu-id="f9136-105">The Contoso private orchestration that you created then submits a Contoso based 3A2 Price and Availability request to the ERP system using the SQL adapter for BizTalk Server.</span></span> <span data-ttu-id="f9136-106">接收到來自 ERP 系統的回應時，協調流程便會呼叫商務規則引擎，以強制套用您所建立的緊急需求商務原則。</span><span class="sxs-lookup"><span data-stu-id="f9136-106">When the response is received from the ERP system, the orchestration calls the Business Rule Engine to enforce the emergency needs business policy that you created.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f9136-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="f9136-107">In This Section</span></span>  
  
-   [<span data-ttu-id="f9136-108">使用 Fabrikam 範例建立價格與可用性要求</span><span class="sxs-lookup"><span data-stu-id="f9136-108">Creating a Price and Availability Request with the Fabrikam Sample</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-a-price-and-availability-request-with-the-fabrikam-sample.md)