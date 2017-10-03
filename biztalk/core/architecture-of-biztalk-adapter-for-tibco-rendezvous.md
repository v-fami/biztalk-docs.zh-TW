---
title: "BizTalk Adapter for TIBCO Rendezvous 的架構 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- passing messages
- architecture
- message passing
- messages, passing
ms.assetid: 174d6ceb-8e1d-4c93-827d-8155cfe47836
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 801f92453ffc85d83d57c1caa5c89ec618b96ed0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="architecture-of-biztalk-adapter-for-tibco-rendezvous"></a><span data-ttu-id="a8dbc-102">BizTalk Adapter for TIBCO Rendezvous 的架構</span><span class="sxs-lookup"><span data-stu-id="a8dbc-102">Architecture of BizTalk Adapter for TIBCO Rendezvous</span></span>
<span data-ttu-id="a8dbc-103">Microsoft BizTalk Adapter for TIBCO Rendezvous 提供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 與 TIBCO Rendezvous 之間的雙向連線。</span><span class="sxs-lookup"><span data-stu-id="a8dbc-103">Microsoft BizTalk Adapter for TIBCO Rendezvous provides bi-directional connectivity between [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and TIBCO Rendezvous.</span></span> <span data-ttu-id="a8dbc-104">此配接器同時使用 TIBCO Rendezvous API 與 BizTalk 配接器架構 API 來提供緊密整合。</span><span class="sxs-lookup"><span data-stu-id="a8dbc-104">This adapter uses both the TIBCO Rendezvous API and the BizTalk Adapter Framework API to provide tight integration.</span></span>  
  
 <span data-ttu-id="a8dbc-105">TIBCO Rendezvous 軟體產品可為企業應用程式整合 (EAI) 提供訊息匯流排。</span><span class="sxs-lookup"><span data-stu-id="a8dbc-105">TIBCO Rendezvous is a software product that provides a message bus for enterprise application integration (EAI).</span></span> <span data-ttu-id="a8dbc-106">TIBCO 可提供 C、C++、Java、Visual Basic 與 Microsoft .NET Framework 的訊息 API 以在 Microsoft Office Excel 工作表與其他自選的應用程式上接收資料摘要。</span><span class="sxs-lookup"><span data-stu-id="a8dbc-106">TIBCO provides messaging APIs in C, C++, Java, Visual Basic and the Microsoft .NET Framework to receive data feeds on Microsoft Office Excel worksheets and other applications of choice.</span></span>  
  
## <a name="message-passing"></a><span data-ttu-id="a8dbc-107">訊息傳遞</span><span class="sxs-lookup"><span data-stu-id="a8dbc-107">Message Passing</span></span>  
 <span data-ttu-id="a8dbc-108">訊息傳遞的基本概念相當簡單：</span><span class="sxs-lookup"><span data-stu-id="a8dbc-108">The basic concept of message passing is fairly simple:</span></span>  
  
-   <span data-ttu-id="a8dbc-109">訊息包含單一主旨，這個主旨是由以句點分隔的多個項目所組成。</span><span class="sxs-lookup"><span data-stu-id="a8dbc-109">A message has a single subject composed of elements separated by periods.</span></span> <span data-ttu-id="a8dbc-110">訊息會傳送至單一 Rendezvous 精靈 (但最後會廣播到其他精靈中)。</span><span class="sxs-lookup"><span data-stu-id="a8dbc-110">It is sent to a single Rendezvous daemon (though it might eventually be broadcast onto other daemons).</span></span>  
  
-   <span data-ttu-id="a8dbc-111">待命程式會向精靈宣告感興趣之主旨 (使用基本萬用字元功能)，這時如果兩個精靈彼此「互連」或是事實上為同一個精靈時，就會將具有相符主旨的訊息傳遞給該待命程式。</span><span class="sxs-lookup"><span data-stu-id="a8dbc-111">A listener announces its subjects of interest to a daemon (with a basic wildcard facility), and messages that have matching subjects are delivered to it if the two daemons are 'connected' to each other, or are indeed the same daemon.</span></span> <span data-ttu-id="a8dbc-112">如需詳細資訊，請參閱中的訊息[BizTalk Adapter for TIBCO Rendezvous 中的訊息](../core/messages-in-biztalk-adapter-for-tibco-rendezvous.md)。</span><span class="sxs-lookup"><span data-stu-id="a8dbc-112">For more information, see Messages in [Messages in BizTalk Adapter for TIBCO Rendezvous](../core/messages-in-biztalk-adapter-for-tibco-rendezvous.md).</span></span>  
  
 <span data-ttu-id="a8dbc-113">下圖說明 BizTalk Adapter for TIBCO Rendezvous 的架構。</span><span class="sxs-lookup"><span data-stu-id="a8dbc-113">The following figure shows the architecture for BizTalk Adapter for TIBCO Rendezvous.</span></span>  
  
 ![](../core/media/tibcorend-arch.gif "TibcoRend_Arch")  
  
## <a name="see-also"></a><span data-ttu-id="a8dbc-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8dbc-114">See Also</span></span>  
 <span data-ttu-id="a8dbc-115">[使用者入門](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md) </span><span class="sxs-lookup"><span data-stu-id="a8dbc-115">[Getting Started](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md) </span></span>  
 [<span data-ttu-id="a8dbc-116">規劃與架構</span><span class="sxs-lookup"><span data-stu-id="a8dbc-116">Planning and Architecture</span></span>](../core/planning-and-architecture15.md)