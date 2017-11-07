---
title: "TIBCO Rendezvous 配接器架構 |Microsoft 文件"
description: "深入了解 BizTalk Adapter for TIBCO Rendezvous 的運作方式，包括在 BizTalk Server 中傳遞的訊息，"
ms.custom: 
ms.date: 10/23/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 174d6ceb-8e1d-4c93-827d-8155cfe47836
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3bfee2b51df8781091ea30e512810bae21a5f2a
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
---
# <a name="architecture-of-the-tibco-rendezvous-adapter"></a><span data-ttu-id="4c02e-103">TIBCO Rendezvous 配接器的架構</span><span class="sxs-lookup"><span data-stu-id="4c02e-103">Architecture of the TIBCO Rendezvous adapter</span></span>

## <a name="overview"></a><span data-ttu-id="4c02e-104">概觀</span><span class="sxs-lookup"><span data-stu-id="4c02e-104">Overview</span></span>
<span data-ttu-id="4c02e-105">Microsoft BizTalk Adapter for TIBCO Rendezvous 提供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 與 TIBCO Rendezvous 之間的雙向連線。</span><span class="sxs-lookup"><span data-stu-id="4c02e-105">Microsoft BizTalk Adapter for TIBCO Rendezvous provides bi-directional connectivity between [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and TIBCO Rendezvous.</span></span> <span data-ttu-id="4c02e-106">此配接器同時使用 TIBCO Rendezvous API 與 BizTalk 配接器架構 API 來提供緊密整合。</span><span class="sxs-lookup"><span data-stu-id="4c02e-106">This adapter uses both the TIBCO Rendezvous API and the BizTalk Adapter Framework API to provide tight integration.</span></span>  
  
 <span data-ttu-id="4c02e-107">TIBCO Rendezvous 軟體產品可為企業應用程式整合 (EAI) 提供訊息匯流排。</span><span class="sxs-lookup"><span data-stu-id="4c02e-107">TIBCO Rendezvous is a software product that provides a message bus for enterprise application integration (EAI).</span></span> <span data-ttu-id="4c02e-108">TIBCO 可提供 C、C++、Java、Visual Basic 與 Microsoft .NET Framework 的訊息 API 以在 Microsoft Office Excel 工作表與其他自選的應用程式上接收資料摘要。</span><span class="sxs-lookup"><span data-stu-id="4c02e-108">TIBCO provides messaging APIs in C, C++, Java, Visual Basic and the Microsoft .NET Framework to receive data feeds on Microsoft Office Excel worksheets and other applications of choice.</span></span>  
  
## <a name="message-passing"></a><span data-ttu-id="4c02e-109">訊息傳遞</span><span class="sxs-lookup"><span data-stu-id="4c02e-109">Message Passing</span></span>  
 <span data-ttu-id="4c02e-110">訊息傳遞的基本概念相當簡單：</span><span class="sxs-lookup"><span data-stu-id="4c02e-110">The basic concept of message passing is fairly simple:</span></span>  
  
-   <span data-ttu-id="4c02e-111">訊息包含單一主旨，這個主旨是由以句點分隔的多個項目所組成。</span><span class="sxs-lookup"><span data-stu-id="4c02e-111">A message has a single subject composed of elements separated by periods.</span></span> <span data-ttu-id="4c02e-112">訊息會傳送至單一 Rendezvous 精靈 (但最後會廣播到其他精靈中)。</span><span class="sxs-lookup"><span data-stu-id="4c02e-112">It is sent to a single Rendezvous daemon (though it might eventually be broadcast onto other daemons).</span></span>  
  
-   <span data-ttu-id="4c02e-113">待命程式會向精靈宣告感興趣之主旨 (使用基本萬用字元功能)，這時如果兩個精靈彼此「互連」或是事實上為同一個精靈時，就會將具有相符主旨的訊息傳遞給該待命程式。</span><span class="sxs-lookup"><span data-stu-id="4c02e-113">A listener announces its subjects of interest to a daemon (with a basic wildcard facility), and messages that have matching subjects are delivered to it if the two daemons are 'connected' to each other, or are indeed the same daemon.</span></span> <span data-ttu-id="4c02e-114">如需詳細資訊，請參閱中的訊息[BizTalk Adapter for TIBCO Rendezvous 中的訊息](../core/messages-in-biztalk-adapter-for-tibco-rendezvous.md)。</span><span class="sxs-lookup"><span data-stu-id="4c02e-114">For more information, see Messages in [Messages in BizTalk Adapter for TIBCO Rendezvous](../core/messages-in-biztalk-adapter-for-tibco-rendezvous.md).</span></span>  
  
 <span data-ttu-id="4c02e-115">下圖說明 BizTalk Adapter for TIBCO Rendezvous 的架構。</span><span class="sxs-lookup"><span data-stu-id="4c02e-115">The following figure shows the architecture for BizTalk Adapter for TIBCO Rendezvous.</span></span>  
  
 ![](../core/media/tibcorend-arch.gif "TibcoRend_Arch")  
  
## <a name="see-also"></a><span data-ttu-id="4c02e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c02e-116">See Also</span></span>  
 [<span data-ttu-id="4c02e-117">快速入門</span><span class="sxs-lookup"><span data-stu-id="4c02e-117">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)  