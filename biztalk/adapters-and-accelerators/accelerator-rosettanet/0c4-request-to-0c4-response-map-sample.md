---
title: "0c4 要求至 0 C 4 回應對應範例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21084807-3d96-45e8-b949-032006a13cab
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfc53475ed0705d17832744593663aeb44845cd3
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="0c4-request-to-0c4-response-map-sample"></a><span data-ttu-id="fc559-102">0c4 要求至 0 C 4 回應對應範例</span><span class="sxs-lookup"><span data-stu-id="fc559-102">0C4 Request to 0C4 Response Map Sample</span></span>
<span data-ttu-id="fc559-103">_0C4RequestMessageTo0C4ResponseMessage.btm 範例示範如何將 0C4 要求訊息對應到 0C4 回應訊息。</span><span class="sxs-lookup"><span data-stu-id="fc559-103">The _0C4RequestMessageTo0C4ResponseMessage.btm sample demonstrates how you can map a 0C4 request message to a 0C4 response message.</span></span>  
  
 <span data-ttu-id="fc559-104">根據預設， [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® BizTalk Server 安裝程式在此範例安裝\<*磁碟機*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk\<版本\>Accelerator for rosettanet\sdk\pipautomation\doubleaction。</span><span class="sxs-lookup"><span data-stu-id="fc559-104">By default, the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® BizTalk Server Setup program installs the sample in \<*drive*\>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\PIPAutomation\DoubleAction.</span></span>  
  
## <a name="sample-contents"></a><span data-ttu-id="fc559-105">範例內容</span><span class="sxs-lookup"><span data-stu-id="fc559-105">Sample Contents</span></span>  
 <span data-ttu-id="fc559-106">這個範例會示範如何將 0C4 要求訊息的欄位對應至 0C4 回應訊息。</span><span class="sxs-lookup"><span data-stu-id="fc559-106">This sample demonstrates how to map the fields of a 0C4 request message to a 0C4 response message.</span></span> <span data-ttu-id="fc559-107">您可以將這個範例與「雙向動作 PIPAutomation 協調流程」範例一起使用。</span><span class="sxs-lookup"><span data-stu-id="fc559-107">You can use this sample with the Double Action PIPAutomation Orchestration sample.</span></span> <span data-ttu-id="fc559-108">「雙向動作 PIPAutomation 協調流程」範例示範如何實作協調流程，以自動產生雙向動作 0C2、0C4、3A2 和 3A4 PIP 的回應。</span><span class="sxs-lookup"><span data-stu-id="fc559-108">The Double Action PIPAutomation Orchestration sample demonstrates how to implement an orchestration to automatically generate responses for double action 0C2, 0C4, 3A2, and 3A4 PIPs.</span></span>