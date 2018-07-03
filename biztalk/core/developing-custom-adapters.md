---
title: 開發自訂配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 44765fbb-b24d-43b6-a40c-d28e319b90a5
caps.latest.revision: 29
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60f901800cb1d7426a364a87b0f3f915d8436244
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022556"
---
# <a name="developing-custom-adapters"></a><span data-ttu-id="5a397-102">開發自訂配接器</span><span class="sxs-lookup"><span data-stu-id="5a397-102">Developing Custom Adapters</span></span>
<span data-ttu-id="5a397-103">為了與外部系統、應用程式和實體交換訊息，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用配接器的概念。</span><span class="sxs-lookup"><span data-stu-id="5a397-103">To exchange messages with external systems, applications, and entities, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses the concept of an adapter.</span></span> <span data-ttu-id="5a397-104">配接器都是 COM 或[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]傳送商務端點的訊息的元件。</span><span class="sxs-lookup"><span data-stu-id="5a397-104">Adapters are COM or [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] components that transfer messages to and from business end.</span></span> <span data-ttu-id="5a397-105">點 （例如檔案系統、 資料庫和自訂商務應用程式） 使用各種通訊協定。</span><span class="sxs-lookup"><span data-stu-id="5a397-105">points (such as file systems, databases, and custom business applications) by using various communication protocols.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5a397-106"> 提供支援各種通訊協定的原生配接器。</span><span class="sxs-lookup"><span data-stu-id="5a397-106"> provides native adapters that support various protocols.</span></span> <span data-ttu-id="5a397-107">其中包括：</span><span class="sxs-lookup"><span data-stu-id="5a397-107">These include:</span></span>  
  
- <span data-ttu-id="5a397-108">支援從「檔案」位置傳送和接收訊息的 FILE 配接器。</span><span class="sxs-lookup"><span data-stu-id="5a397-108">A File adapter that supports sending and receiving messages from a File location</span></span>  
  
- <span data-ttu-id="5a397-109">適用於 EDI、FTP、HTTP、MSMQ、SMTP、POP3 及 SOAP 通訊協定的配接器</span><span class="sxs-lookup"><span data-stu-id="5a397-109">Adapters for EDI, FTP, HTTP, MSMQ, SMTP, POP3, and SOAP protocols</span></span>  
  
- <span data-ttu-id="5a397-110">適用於 [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)] 的配接器</span><span class="sxs-lookup"><span data-stu-id="5a397-110">An adapter for [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)]</span></span>  
  
  <span data-ttu-id="5a397-111">在某些情況下，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可能需要將訊息傳輸到特定的自訂應用程式，或是使用不存在原生配接器的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="5a397-111">In some cases [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] may need to transport messages to a specific custom application or use a protocol for which a native adapter does not exist.</span></span> <span data-ttu-id="5a397-112">有些協力廠商有撰寫配接器以支援其他的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="5a397-112">Third-party companies have written adapters to support additional protocols.</span></span> <span data-ttu-id="5a397-113">在決定要撰寫自訂配接器之前，您必須判斷是否有適用於通訊協定的配接器。</span><span class="sxs-lookup"><span data-stu-id="5a397-113">You may want to determine if there is an adapter for your protocol before deciding to write a custom adapter.</span></span> <span data-ttu-id="5a397-114">如需配接器和相關聯的供應商的清單，請參閱[ http://go.microsoft.com/fwlink/?LinkId=47140 ](http://go.microsoft.com/fwlink/?LinkId=47140)。</span><span class="sxs-lookup"><span data-stu-id="5a397-114">For a list of adapters and associated vendors see [http://go.microsoft.com/fwlink/?LinkId=47140](http://go.microsoft.com/fwlink/?LinkId=47140).</span></span> <span data-ttu-id="5a397-115">如果您找不到支援您通訊需求的配接器，即可開發自己的自訂配接器。</span><span class="sxs-lookup"><span data-stu-id="5a397-115">If you are unable to locate an adapter to support your communication requirements, you can develop your own custom adapter.</span></span>  
  
  <span data-ttu-id="5a397-116">撰寫自訂配接器可能會是具有挑戰性的工作。</span><span class="sxs-lookup"><span data-stu-id="5a397-116">Writing a custom adapter can be a challenging exercise.</span></span> <span data-ttu-id="5a397-117">為了簡化這項程序，Microsoft 開發了稱為「配接器架構」的基礎。</span><span class="sxs-lookup"><span data-stu-id="5a397-117">To simplify this process Microsoft has developed a foundation called the Adapter Framework.</span></span> <span data-ttu-id="5a397-118">您可以使用此架構，連同 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SDK 中的範例配接器程式碼，做為開發工作的基礎。</span><span class="sxs-lookup"><span data-stu-id="5a397-118">You can use this framework as a basis for your development along with sample adapter source code in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] SDK.</span></span>  
  
  <span data-ttu-id="5a397-119">本節中的主題描述自訂配接器開發秘訣和建議。</span><span class="sxs-lookup"><span data-stu-id="5a397-119">The topics in this section present custom adapter development tips and recommendations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5a397-120">本節內容</span><span class="sxs-lookup"><span data-stu-id="5a397-120">In This Section</span></span>  
  
-   [<span data-ttu-id="5a397-121">何謂配接器架構？</span><span class="sxs-lookup"><span data-stu-id="5a397-121">What Is the Adapter Framework?</span></span>](../core/what-is-the-adapter-framework.md)  
  
-   [<span data-ttu-id="5a397-122">BizTalk Server 如何具現化配接器</span><span class="sxs-lookup"><span data-stu-id="5a397-122">How BizTalk Server Instantiates an Adapter</span></span>](../core/how-biztalk-server-instantiates-an-adapter.md)  
  
-   [<span data-ttu-id="5a397-123">訊息批次</span><span class="sxs-lookup"><span data-stu-id="5a397-123">Message Batches</span></span>](../core/message-batches.md)  
  
-   [<span data-ttu-id="5a397-124">交易式訊息批次</span><span class="sxs-lookup"><span data-stu-id="5a397-124">Transactional Message Batches</span></span>](../core/transactional-message-batches.md)  
  
-   [<span data-ttu-id="5a397-125">開發接收配接器</span><span class="sxs-lookup"><span data-stu-id="5a397-125">Developing a Receive Adapter</span></span>](../core/developing-a-receive-adapter.md)  
  
-   [<span data-ttu-id="5a397-126">開發傳送配接器</span><span class="sxs-lookup"><span data-stu-id="5a397-126">Developing a Send Adapter</span></span>](../core/developing-a-send-adapter.md)  
  
-   [<span data-ttu-id="5a397-127">具現化外掛式配接器</span><span class="sxs-lookup"><span data-stu-id="5a397-127">Instantiating Isolated Adapters</span></span>](../core/instantiating-isolated-adapters.md)  
  
-   [<span data-ttu-id="5a397-128">配接器設計問題</span><span class="sxs-lookup"><span data-stu-id="5a397-128">Adapter Design Issues</span></span>](../core/adapter-design-issues.md)  
  
-   [<span data-ttu-id="5a397-129">配接器如何處理大型訊息</span><span class="sxs-lookup"><span data-stu-id="5a397-129">How Adapters Handle Large Messages</span></span>](../core/how-adapters-handle-large-messages.md)  
  
-   [<span data-ttu-id="5a397-130">如何處理配接器失敗</span><span class="sxs-lookup"><span data-stu-id="5a397-130">How to Handle Adapter Failures</span></span>](../core/how-to-handle-adapter-failures.md)  
  
-   [<span data-ttu-id="5a397-131">如何終止配接器</span><span class="sxs-lookup"><span data-stu-id="5a397-131">How to Terminate an Adapter</span></span>](../core/how-to-terminate-an-adapter.md)  
  
-   [<span data-ttu-id="5a397-132">如何設計高效能的配接器</span><span class="sxs-lookup"><span data-stu-id="5a397-132">How to Design a Performant Adapter</span></span>](../core/how-to-design-a-performant-adapter.md)  
  
-   [<span data-ttu-id="5a397-133">如何部署自訂配接器</span><span class="sxs-lookup"><span data-stu-id="5a397-133">How to Deploy a Custom Adapter</span></span>](../core/how-to-deploy-a-custom-adapter.md)  
  
-   [<span data-ttu-id="5a397-134">如何測試和偵錯配接器</span><span class="sxs-lookup"><span data-stu-id="5a397-134">How to Test and Debug an Adapter</span></span>](../core/how-to-test-and-debug-an-adapter.md)  
  
-   [<span data-ttu-id="5a397-135">如何將配接器中繼資料新增至 BizTalk 專案</span><span class="sxs-lookup"><span data-stu-id="5a397-135">How to Add Adapter Metadata to a BizTalk Project</span></span>](../core/how-to-add-adapter-metadata-to-a-biztalk-project.md)  
  
-   [<span data-ttu-id="5a397-136">配接器當地語系化問題</span><span class="sxs-lookup"><span data-stu-id="5a397-136">Adapter Localization Issues</span></span>](../core/adapter-localization-issues.md)  
  
-   [<span data-ttu-id="5a397-137">設計配接器的祕訣</span><span class="sxs-lookup"><span data-stu-id="5a397-137">Tips for Designing Your Adapter</span></span>](../core/tips-for-designing-your-adapter.md)  
  
-   [<span data-ttu-id="5a397-138">配接器設計階段設定</span><span class="sxs-lookup"><span data-stu-id="5a397-138">Adapter Design-Time Configuration</span></span>](../core/adapter-design-time-configuration.md)  
  
## <a name="see-also"></a><span data-ttu-id="5a397-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a397-139">See Also</span></span>  
 [<span data-ttu-id="5a397-140">開發自訂元件</span><span class="sxs-lookup"><span data-stu-id="5a397-140">Developing Custom Components</span></span>](../core/developing-custom-components.md)