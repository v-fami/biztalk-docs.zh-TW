---
title: "範例 BTARN 商務原則 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db932c17-8e8f-4f7a-b165-d1d7d749cdb6
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bfe0bd746894106fc7ac9ebeaae600fe7344ba18
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sample-btarn-business-policy"></a><span data-ttu-id="7494a-102">BTARN 商務原則範例</span><span class="sxs-lookup"><span data-stu-id="7494a-102">Sample BTARN Business Policy</span></span>
<span data-ttu-id="7494a-103">這個範例是與相關聯的 XML 程式碼[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]商務規則原則。</span><span class="sxs-lookup"><span data-stu-id="7494a-103">This sample is the XML code associated with a [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] business-rules policy.</span></span>  
  
 <span data-ttu-id="7494a-104">範例檔案是中的 samplebtarnpolicy.xml \<*磁碟機*>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本 > Accelerator for rosettanet\sdk\pipautomation\3a4。</span><span class="sxs-lookup"><span data-stu-id="7494a-104">The sample file is samplebtarnpolicy.xml in \<*drive*>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version> Accelerator for RosettaNet\SDK\PIPAutomation\3A4.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="7494a-105">示範</span><span class="sxs-lookup"><span data-stu-id="7494a-105">Demonstrates</span></span>  
 <span data-ttu-id="7494a-106">本程式碼顯示具有下列規則的商務規則：</span><span class="sxs-lookup"><span data-stu-id="7494a-106">This code shows a business-rule policy with the following rule:</span></span>  
  
 <span data-ttu-id="7494a-107">IF (內送 3A4 Purchase Order 訊息的 AccountNumber = "111111111") 和 (Order < 500 的 MonetaryAmount) THEN 會自動傳送回應訊息</span><span class="sxs-lookup"><span data-stu-id="7494a-107">IF (AccountNumber in the incoming 3A4 Purchase Order message = "111111111") and (MonetaryAmount of the Order < 500) THEN automatically send a response message</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7494a-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7494a-108">See Also</span></span>  
 [<span data-ttu-id="7494a-109">使用商務規則的 3A4 私用回應者協調流程</span><span class="sxs-lookup"><span data-stu-id="7494a-109">3A4 Private Responder Orchestration Using a Business Rule</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)