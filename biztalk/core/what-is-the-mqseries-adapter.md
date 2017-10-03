---
title: "何謂 MQSeries 配接器？ | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, about MQSeries adapters
- MQSeries adapters
ms.assetid: fd3dfa9a-344a-46e5-a342-bc56da7c1c50
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f72d0012050fc8022b53120377aeb648641d21f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-mqseries-adapter"></a><span data-ttu-id="45e6a-103">何謂 MQSeries 配接器？</span><span class="sxs-lookup"><span data-stu-id="45e6a-103">What Is the MQSeries Adapter?</span></span>
<span data-ttu-id="45e6a-104">透過 MQSeries 配接器，您就可以使用 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 來傳送和接收 MQSeries 系統的訊息。</span><span class="sxs-lookup"><span data-stu-id="45e6a-104">With the MQSeries adapter you can send and receive messages to MQSeries systems using Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="45e6a-105">此配接器依賴 MQSeries Server for Windows。</span><span class="sxs-lookup"><span data-stu-id="45e6a-105">The adapter relies on MQSeries Server for Windows.</span></span> <span data-ttu-id="45e6a-106">此設計會保證可靠的傳訊，因為 MQSeries Server for Windows 支援「Microsoft 分散式交易協調器」(MSDTC)。</span><span class="sxs-lookup"><span data-stu-id="45e6a-106">This design guarantees reliable messaging because MQSeries Server for Windows supports Microsoft Distributed Transaction Coordinator (MSDTC).</span></span>  
  
 <span data-ttu-id="45e6a-107">此配接器支援叢集 MQSeries Server、叢集 MQSeries 佇列管理員，以及叢集 BizTalk Server。</span><span class="sxs-lookup"><span data-stu-id="45e6a-107">The adapter supports clustered MQSeries Servers and clustered MQSeries Queue Managers, and also clustered BizTalk servers.</span></span>  
  
 <span data-ttu-id="45e6a-108">您可以使用 MQSeries 配接器，來執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="45e6a-108">You can do the following with the MQSeries adapter:</span></span>  
  
-   <span data-ttu-id="45e6a-109">傳送訊息至 MQSeries 遠端定義佇列、本機佇列、傳輸佇列，以及來自 BizTalk Server 的別名佇列。</span><span class="sxs-lookup"><span data-stu-id="45e6a-109">Send messages to MQSeries remote definition queues, local queues, transmission queues, and alias queues from BizTalk Server.</span></span>  
  
-   <span data-ttu-id="45e6a-110">接收來自 MQSeries 傳輸佇列、本機佇列，以及別名佇列的訊息。</span><span class="sxs-lookup"><span data-stu-id="45e6a-110">Receive messages from MQSeries transmission queues, local queues, and alias queues.</span></span>  
  
-   <span data-ttu-id="45e6a-111">傳送和接收來自 MQSeries Server for Windows 的訊息，而 MQSeries Server 可以在與 BizTalk Server 相同的電腦或是在遠端安裝上執行。</span><span class="sxs-lookup"><span data-stu-id="45e6a-111">Send and receive messages from MQSeries Server for Windows (MQSeries Server can run on the same computer as BizTalk Server or on a remote installation).</span></span> <span data-ttu-id="45e6a-112">您只需要部署一個 MQSAgent (配接器的 COM+ 元件) 複本，即可支援所有的 BizTalk Server 安裝。</span><span class="sxs-lookup"><span data-stu-id="45e6a-112">You only have to deploy one copy of MQSAgent (the COM+ component of the adapter) to support all your BizTalk Server installations.</span></span>  
  
-   <span data-ttu-id="45e6a-113">以等待間隔輪詢 MQSeries Server。</span><span class="sxs-lookup"><span data-stu-id="45e6a-113">Poll MQSeries Server with a wait interval.</span></span>  
  
-   <span data-ttu-id="45e6a-114">使用動態傳送埠來控制配接器。</span><span class="sxs-lookup"><span data-stu-id="45e6a-114">Use dynamic send ports to control the adapter.</span></span>  
  
-   <span data-ttu-id="45e6a-115">在執行階段動態建立查詢。</span><span class="sxs-lookup"><span data-stu-id="45e6a-115">Dynamically create queues at run time.</span></span>  
  
-   <span data-ttu-id="45e6a-116">動態接收佇列，根據 MQSeries 比對選項的訊息。</span><span class="sxs-lookup"><span data-stu-id="45e6a-116">Dynamically receive messages from queues based upon MQSeries MatchOptions.</span></span>  
  
-   <span data-ttu-id="45e6a-117">針對傳輸和接收訊息，將內容屬性對應到標頭屬性。</span><span class="sxs-lookup"><span data-stu-id="45e6a-117">Map context properties to header properties for both transmitting and receiving messages.</span></span> <span data-ttu-id="45e6a-118">您可以透過 BizTalk Server 內容屬性來取得和設定 MQSeries 標頭屬性 (包括 MQMD、MQXQH、MQCIH，以及 MQIIH)。</span><span class="sxs-lookup"><span data-stu-id="45e6a-118">You can get and set MQSeries header properties (including MQMD, MQXQH, MQCIH, and MQIIH) through BizTalk Server context properties.</span></span>  
  
-   <span data-ttu-id="45e6a-119">透過 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 或是 MQSeries Server 建立相互關聯識別項來啟用相互關聯。</span><span class="sxs-lookup"><span data-stu-id="45e6a-119">Enable correlation with either [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] or MQSeries Server creating the correlation identifier.</span></span>  
  
-   <span data-ttu-id="45e6a-120">針對要傳送和接收的訊息要求交易式和非交易式傳遞。</span><span class="sxs-lookup"><span data-stu-id="45e6a-120">Request transactional and nontransactional delivery of messages for send and receive.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="45e6a-121">當使用 MQSeries 這類會對伺服器進行「分散式元件物件模型」(Distributed Component Object Model，DCOM) 呼叫的功能時，請確定您並未啟用「網路位址轉譯」(Network Address Translation，NAT) 架構的防火牆。</span><span class="sxs-lookup"><span data-stu-id="45e6a-121">When using features such as MQSeries which make Distributed Component Object Model (DCOM) calls to the server, make sure you do not have a Network Address Translation (NAT)-based firewall enabled.</span></span> <span data-ttu-id="45e6a-122">用戶端必須能以伺服器的實際 IP 位址來存取伺服器，而 NAT 架構的防火牆會將此位址轉譯為用戶端無法辨識的位址。</span><span class="sxs-lookup"><span data-stu-id="45e6a-122">The client must be able to access the server by its actual IP address, and NAT-based firewalls translate this address to something the client will not recognize.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="45e6a-123">本節內容</span><span class="sxs-lookup"><span data-stu-id="45e6a-123">In This Section</span></span>  
  
-   [<span data-ttu-id="45e6a-124">MQSeries 配接器的元件</span><span class="sxs-lookup"><span data-stu-id="45e6a-124">Components of the MQSeries Adapter</span></span>](../core/components-of-the-mqseries-adapter.md)  
  
-   [<span data-ttu-id="45e6a-125">MQSeries 配接器架構</span><span class="sxs-lookup"><span data-stu-id="45e6a-125">MQSeries Adapter Architecture</span></span>](../core/mqseries-adapter-architecture.md)  
  
-   [<span data-ttu-id="45e6a-126">使用 MQSeries 配接器</span><span class="sxs-lookup"><span data-stu-id="45e6a-126">Using the MQSeries Adapter</span></span>](../core/using-the-mqseries-adapter.md)  
  
-   [<span data-ttu-id="45e6a-127">MQSeries 配接器安全性</span><span class="sxs-lookup"><span data-stu-id="45e6a-127">MQSeries Adapter Security</span></span>](../core/mqseries-adapter-security.md)