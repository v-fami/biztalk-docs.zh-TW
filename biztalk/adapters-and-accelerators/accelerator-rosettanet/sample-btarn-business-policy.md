---
title: BTARN 商務原則的範例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: db932c17-8e8f-4f7a-b165-d1d7d749cdb6
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e055d039e323fb985d9650f6f105bb3b44e9581
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974903"
---
# <a name="sample-btarn-business-policy"></a><span data-ttu-id="b0498-102">BTARN 商務原則範例</span><span class="sxs-lookup"><span data-stu-id="b0498-102">Sample BTARN Business Policy</span></span>
<span data-ttu-id="b0498-103">這個範例是 Microsoft® 相關聯的 XML 程式碼[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]商務規則原則。</span><span class="sxs-lookup"><span data-stu-id="b0498-103">This sample is the XML code associated with a Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] business-rules policy.</span></span>  
  
 <span data-ttu-id="b0498-104">範例檔案是中的 samplebtarnpolicy.xml \<*磁碟機*\>: \Program Files\\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\PIPAutomation\3A4。</span><span class="sxs-lookup"><span data-stu-id="b0498-104">The sample file is samplebtarnpolicy.xml in \<*drive*\>:\Program Files\\Microsoft  BizTalk \<version\> Accelerator for RosettaNet\SDK\PIPAutomation\3A4.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="b0498-105">示範</span><span class="sxs-lookup"><span data-stu-id="b0498-105">Demonstrates</span></span>  
 <span data-ttu-id="b0498-106">本程式碼顯示具有下列規則的商務規則：</span><span class="sxs-lookup"><span data-stu-id="b0498-106">This code shows a business-rule policy with the following rule:</span></span>  
  
 <span data-ttu-id="b0498-107">IF (內送 3A4 Purchase Order 訊息的 AccountNumber = "111111111") 和 (Order < 500 的 MonetaryAmount) THEN 會自動傳送回應訊息</span><span class="sxs-lookup"><span data-stu-id="b0498-107">IF (AccountNumber in the incoming 3A4 Purchase Order message = "111111111") and (MonetaryAmount of the Order < 500) THEN automatically send a response message</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0498-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b0498-108">See Also</span></span>  
 [<span data-ttu-id="b0498-109">使用商務規則的 3A4 私用回應者協調流程</span><span class="sxs-lookup"><span data-stu-id="b0498-109">3A4 Private Responder Orchestration Using a Business Rule</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)