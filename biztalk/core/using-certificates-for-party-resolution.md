---
title: "使用憑證進行合作對象解析 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4eb9b616-be1c-4b68-b3de-8721a344a423
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b157191e4004671a8b276f47d15a8589974dfbac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-certificates-for-party-resolution"></a><span data-ttu-id="b0089-102">使用憑證進行合作對象解析</span><span class="sxs-lookup"><span data-stu-id="b0089-102">Using Certificates for Party Resolution</span></span>
<span data-ttu-id="b0089-103">A*合作對象*是與協調流程互動的 BizTalk Server 外部的實體。</span><span class="sxs-lookup"><span data-stu-id="b0089-103">A *party* is an entity outside BizTalk Server that interacts with an orchestration.</span></span> <span data-ttu-id="b0089-104">當 BizTalk Server 接收訊息時，它會使用公開金鑰憑證來決定是誰傳送訊息，並將傳送者解析為 BizTalk Server 環境中的已知合作對象。</span><span class="sxs-lookup"><span data-stu-id="b0089-104">When BizTalk Server receives a message, it uses the public key certificate to determine who sent the message, and to resolve the sender to a known party in the BizTalk Server environment.</span></span>  
  
 <span data-ttu-id="b0089-105">本節提供如何設定 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 管線、接收位置、連接埠和 BizTalk Server 環境，以進行合作對象解析的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b0089-105">This section provides information about how to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipelines, receive locations, ports, and the BizTalk Server environment for party resolution.</span></span>  
  
 <span data-ttu-id="b0089-106">如需訊息驗證的詳細資訊，請參閱[驗證訊息的傳送者](../core/authenticating-the-sender-of-a-message.md)。</span><span class="sxs-lookup"><span data-stu-id="b0089-106">For more information about authentication of a message, see [Authenticating the Sender of a Message](../core/authenticating-the-sender-of-a-message.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b0089-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="b0089-107">In This Section</span></span>  
 [<span data-ttu-id="b0089-108">如何設定 BizTalk Server 進行合作對象解析</span><span class="sxs-lookup"><span data-stu-id="b0089-108">How to Configure BizTalk Server for Party Resolution</span></span>](../core/how-to-configure-biztalk-server-for-party-resolution.md)