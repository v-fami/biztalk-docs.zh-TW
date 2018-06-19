---
title: 開發協調流程的安全性考量 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, orchestrations
- messages, subscriptions
- orchestrations, security
- messages, security
ms.assetid: a29b2018-4a8f-49ad-a817-6f279db3f801
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e020759a8d389461978a4de4138bcc139d527539
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269318"
---
# <a name="security-considerations-for-developing-orchestrations"></a><span data-ttu-id="9dd1b-102">開發協調流程的安全性考量</span><span class="sxs-lookup"><span data-stu-id="9dd1b-102">Security Considerations for Developing Orchestrations</span></span>
<span data-ttu-id="9dd1b-103">設計協調流程時，您應該考量可能的安全性問題。</span><span class="sxs-lookup"><span data-stu-id="9dd1b-103">When designing your orchestrations, you should consider potential security issues.</span></span>  
  
## <a name="avoid-subscriptions-based-on-content-from-untrusted-messages"></a><span data-ttu-id="9dd1b-104">避免訂閱來自不信任之訊息的內容</span><span class="sxs-lookup"><span data-stu-id="9dd1b-104">Avoid subscriptions based on content from untrusted messages</span></span>  
 <span data-ttu-id="9dd1b-105">為確保低權限訊息不會起始可能依據訊息內容建立訂閱的協調流程執行個體，強烈建議您，請勿讓您的協調流程依據不信任之訊息內容建立訊息訂閱。</span><span class="sxs-lookup"><span data-stu-id="9dd1b-105">To ensure that a low-privilege message does not initiate an orchestration instance that could potentially create subscriptions based on the message content or context, it is highly recommended that your orchestrations do not create their message subscriptions based on the content or context of a message that is not trusted.</span></span>  
  
 <span data-ttu-id="9dd1b-106">如需中的安全性資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，請參閱[保護 BizTalk Server](../core/securing-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="9dd1b-106">For information about security in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [Securing BizTalk Server](../core/securing-biztalk-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dd1b-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9dd1b-107">See Also</span></span>  
 <span data-ttu-id="9dd1b-108">[建立協調流程](../core/creating-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="9dd1b-108">[Creating Orchestrations](../core/creating-orchestrations.md) </span></span>  
 [<span data-ttu-id="9dd1b-109">關於協調流程</span><span class="sxs-lookup"><span data-stu-id="9dd1b-109">About Orchestrations</span></span>](../core/about-orchestrations.md)