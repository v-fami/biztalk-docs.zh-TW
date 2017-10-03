---
title: "BizTalk Adapter for TIBCO Rendezvous 中的訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- passing messages
- TIBCO Rendezvous
- messages
- message passing
- messages, passing
ms.assetid: 12699550-22e7-4a11-a024-2302570970af
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4bc1eadbefdeb5c59df9a1b999ffdd3e530587a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="messages-in-biztalk-adapter-for-tibco-rendezvous"></a><span data-ttu-id="acc92-102">BizTalk Adapter for TIBCO Rendezvous 中的訊息</span><span class="sxs-lookup"><span data-stu-id="acc92-102">Messages in BizTalk Adapter for TIBCO Rendezvous</span></span>
<span data-ttu-id="acc92-103">BizTalk Adapter for TIBCO Rendezvous 提供 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 與 TIBCO Rendezvous 之間的雙向連線。</span><span class="sxs-lookup"><span data-stu-id="acc92-103">BizTalk Adapter for TIBCO Rendezvous provides bi-directional connectivity between [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and TIBCO Rendezvous.</span></span> <span data-ttu-id="acc92-104">此配接器同時使用 TIBCO Rendezvous API 與 BizTalk 配接器架構 API 來提供緊密整合。</span><span class="sxs-lookup"><span data-stu-id="acc92-104">This adapter uses both the TIBCO Rendezvous API and the BizTalk Adapter Framework API to provide tight integration.</span></span>  
  
## <a name="about-tibco-rendezvous"></a><span data-ttu-id="acc92-105">關於 TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="acc92-105">About TIBCO Rendezvous</span></span>  
 <span data-ttu-id="acc92-106">TIBCO Rendezvous 軟體產品可為企業應用程式整合 (EAI) 提供訊息匯流排。</span><span class="sxs-lookup"><span data-stu-id="acc92-106">TIBCO Rendezvous is a software product that provides a message bus for enterprise application integration (EAI).</span></span> <span data-ttu-id="acc92-107">TIBCO 可提供 C、C++、Java、Visual Basic 與 Microsoft .NET Framework 的訊息 API 以在 Microsoft Office Excel 工作表與其他自選的應用程式上接收資料摘要。</span><span class="sxs-lookup"><span data-stu-id="acc92-107">TIBCO provides messaging APIs in C, C++, Java, Visual Basic and for the Microsoft .NET Framework to receive data feeds on Microsoft Office Excel worksheets and other applications of choice.</span></span> <span data-ttu-id="acc92-108">如需詳細資訊，請參閱[TIBCO Rendezvous 概念](../core/tibco-rendezvous-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="acc92-108">For more information, see [TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md).</span></span>  
  
### <a name="message-passing"></a><span data-ttu-id="acc92-109">訊息傳遞</span><span class="sxs-lookup"><span data-stu-id="acc92-109">Message Passing</span></span>  
 <span data-ttu-id="acc92-110">訊息傳遞的基本概念相當簡單：</span><span class="sxs-lookup"><span data-stu-id="acc92-110">The basic concept of message passing is fairly simple:</span></span>  
  
-   <span data-ttu-id="acc92-111">訊息包含單一主旨，這個主旨是由以句點分隔的多個項目所組成。</span><span class="sxs-lookup"><span data-stu-id="acc92-111">A message has a single subject composed of elements separated by periods.</span></span> <span data-ttu-id="acc92-112">訊息會傳送至單一 Rendezvous 精靈 (但最後會廣播到其他精靈中)。</span><span class="sxs-lookup"><span data-stu-id="acc92-112">A message is sent to a single Rendezvous daemon, although it might eventually be broadcast onto other daemons.</span></span>  
  
-   <span data-ttu-id="acc92-113">待命程式會向精靈宣告感興趣之主旨 (使用基本萬用字元功能)，</span><span class="sxs-lookup"><span data-stu-id="acc92-113">A listener announces its subjects of interest to a daemon (with a basic wildcard facility).</span></span> <span data-ttu-id="acc92-114">這時如果兩個精靈彼此「互連」或是事實上為同一個精靈時，就會將具有相符主旨的訊息傳遞給該待命程式。</span><span class="sxs-lookup"><span data-stu-id="acc92-114">Messages that have matching subjects are delivered to it if the two daemons are connected to each other, or are indeed the same daemon.</span></span>  
  
 <span data-ttu-id="acc92-115">必要時，會以此為基礎往上發展重要的「企業」功能 (容錯/可靠或認證選項)：一切都是透過基礎的基本訊息來實作。</span><span class="sxs-lookup"><span data-stu-id="acc92-115">Significant "Enterprise" functionality is layered onto this if desired--with Fault Tolerance/Reliable or Certified options possible--all implemented through the underlying basic messages.</span></span>  
  
 <span data-ttu-id="acc92-116">訊息本身可以視為具型別的名稱值欄位或是數字值欄位 (訊息中的這兩種識別機制可互相混合使用以符合特定限制)。</span><span class="sxs-lookup"><span data-stu-id="acc92-116">The messages themselves can be viewed as typed name-value fields or number-value fields (the two identification mechanisms in a message can mix and match with certain restrictions).</span></span> <span data-ttu-id="acc92-117">訊息本身可以包含子訊息，其中又可以包含更多子訊息。</span><span class="sxs-lookup"><span data-stu-id="acc92-117">A message itself can contain sub-messages, which can contain sub-messages.</span></span>  
  
 <span data-ttu-id="acc92-118">主旨名稱包含一或多個以點字元 (句點) 分隔的元素。</span><span class="sxs-lookup"><span data-stu-id="acc92-118">Subject names consist of one or more elements separated by dot characters (periods).</span></span> <span data-ttu-id="acc92-119">這些元素會實作主旨名稱階層來反映應用程式系統中的資訊結構。</span><span class="sxs-lookup"><span data-stu-id="acc92-119">The elements implement a subject name hierarchy that reflects the structure of information in an application system.</span></span> <span data-ttu-id="acc92-120">下列字串是有效主旨名稱的範例：</span><span class="sxs-lookup"><span data-stu-id="acc92-120">The following strings are examples of valid subject names:</span></span>  
  
-   <span data-ttu-id="acc92-121">RUN.HOME</span><span class="sxs-lookup"><span data-stu-id="acc92-121">RUN.HOME</span></span>  
  
-   <span data-ttu-id="acc92-122">RUN.for.Elected_Office</span><span class="sxs-lookup"><span data-stu-id="acc92-122">RUN.for.Elected_Office</span></span>  
  
 <span data-ttu-id="acc92-123">BizTalk Adapter for TIBCO Rendezvous 透過 TIBCO Rendezvous SDK 將訊息發佈至 TIBCO Rendezvous 主旨，以及註冊接收 TIBCO Rendezvous 事件。</span><span class="sxs-lookup"><span data-stu-id="acc92-123">BizTalk Adapter for TIBCO Rendezvous uses the TIBCO Rendezvous SDK to publish messages to TIBCO Rendezvous subjects and to register for TIBCO Rendezvous events.</span></span> <span data-ttu-id="acc92-124">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 相關類別會裝載在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 電腦中。</span><span class="sxs-lookup"><span data-stu-id="acc92-124">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-related classes are hosted in a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] computer.</span></span> <span data-ttu-id="acc92-125">另一個處理序 (執行階段代理程式) 會啟動並以 Rendezvous 程式形式運作，兩者之間會使用 .NET Framework 遠端處理來交換訊息。</span><span class="sxs-lookup"><span data-stu-id="acc92-125">A separate process (run-time agent) is started and acts as the Rendezvous program, and .NET Framework remoting is used to exchange messages between the two.</span></span>  
  
-   <span data-ttu-id="acc92-126">資訊層級、警告層級與錯誤層級的訊息會傳送至 Windows 事件日誌。</span><span class="sxs-lookup"><span data-stu-id="acc92-126">Info-Level, Warning-Level, and Error-level messages are sent to the Windows event log.</span></span>  
  
-   <span data-ttu-id="acc92-127">所有層級 (包括偵錯層級) 的訊息都會傳送至 Windows 追蹤記錄檔。</span><span class="sxs-lookup"><span data-stu-id="acc92-127">All levels, including Debug-level messages, are sent to the Windows Tracing Log.</span></span>  
  
#### <a name="transmitter"></a><span data-ttu-id="acc92-128">傳輸器</span><span class="sxs-lookup"><span data-stu-id="acc92-128">Transmitter</span></span>  
 <span data-ttu-id="acc92-129">BizTalk Adapter for TIBCO Rendezvous 會針對每個傳送埠各啟動一個執行階段代理程式。</span><span class="sxs-lookup"><span data-stu-id="acc92-129">BizTalk Adapter for TIBCO Rendezvous launches one run-time agent per send port.</span></span> <span data-ttu-id="acc92-130">TIBCO Rendezvous .NET Framework API 只允許設定全域範圍的字元編碼。</span><span class="sxs-lookup"><span data-stu-id="acc92-130">The TIBCO Rendezvous .NET Framework API only allows setting character encoding at a global scope.</span></span> <span data-ttu-id="acc92-131">因此，其中一項連接埠組態選項會是字碼頁編號。</span><span class="sxs-lookup"><span data-stu-id="acc92-131">Therefore, one of the port configuration options is a code page number.</span></span> <span data-ttu-id="acc92-132">透過針對每個字碼頁啟動不同的程序，配接器可以提供更好的全球化支援。</span><span class="sxs-lookup"><span data-stu-id="acc92-132">By starting a different process for each code page, the adapter can provide better support for globalization.</span></span>  
  
#### <a name="receiver"></a><span data-ttu-id="acc92-133">接收器</span><span class="sxs-lookup"><span data-stu-id="acc92-133">Receiver</span></span>  
 <span data-ttu-id="acc92-134">BizTalk Adapter for TIBCO Rendezvous 會啟動一個執行階段代理程式每個接收位置。</span><span class="sxs-lookup"><span data-stu-id="acc92-134">BizTalk Adapter for TIBCO Rendezvous launches one run-time agent per receive location.</span></span>  
  
#### <a name="transactions"></a><span data-ttu-id="acc92-135">交易</span><span class="sxs-lookup"><span data-stu-id="acc92-135">Transactions</span></span>  
 <span data-ttu-id="acc92-136">TIBCO Rendezvous 產品非交易式產品。</span><span class="sxs-lookup"><span data-stu-id="acc92-136">The TIBCO Rendezvous product is not transactional.</span></span> <span data-ttu-id="acc92-137">若要執行交易，需要使用另一個產品 TIBCO Rendezvous TX。</span><span class="sxs-lookup"><span data-stu-id="acc92-137">A separate product, TIBCO Rendezvous TX, is required.</span></span> <span data-ttu-id="acc92-138">此版本的 BizTalk Adapter for TIBCO Rendezvous 不支援交易。</span><span class="sxs-lookup"><span data-stu-id="acc92-138">BizTalk Adapter for TIBCO Rendezvous does not support transactions in this release.</span></span>  
  
#### <a name="security"></a><span data-ttu-id="acc92-139">安全性</span><span class="sxs-lookup"><span data-stu-id="acc92-139">Security</span></span>  
 <span data-ttu-id="acc92-140">TIBCO Rendezvous 僅支援 TIBCO Rendezvous 程式與精靈之間的驗證。</span><span class="sxs-lookup"><span data-stu-id="acc92-140">TIBCO Rendezvous only supports authentication between TIBCO Rendezvous programs and daemons.</span></span> <span data-ttu-id="acc92-141">它不會執行授權或加密。</span><span class="sxs-lookup"><span data-stu-id="acc92-141">It does not perform authorization or encryption.</span></span> <span data-ttu-id="acc92-142">若要執行授權或加密，需要使用另一個產品 TIBCO Rendezvous DataSecurity。</span><span class="sxs-lookup"><span data-stu-id="acc92-142">A separate product, TIBCO Rendezvous DataSecurity, is required.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acc92-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acc92-143">See Also</span></span>  
 <span data-ttu-id="acc92-144">[TIBCO Rendezvous 概念](../core/tibco-rendezvous-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="acc92-144">[TIBCO Rendezvous Concepts](../core/tibco-rendezvous-concepts.md) </span></span>  
 [<span data-ttu-id="acc92-145">快速入門</span><span class="sxs-lookup"><span data-stu-id="acc92-145">Getting Started</span></span>](../core/getting-started-with-biztalk-adapter-for-tibco-rendezvous.md)