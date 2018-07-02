---
title: MessageBox 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, MessageBox database
- messages, suspended messages
- MessageBox database, messages
- MessageBox database, about MessageBox database
- MessageBox database, suspended messages
- suspended messages
- MessageBox database
- suspended messages, MessageBox database
ms.assetid: f89eb02c-1b83-4127-8a91-e78fb4a1f96e
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cec97829d96aa81403a4f4457cb1aebf9c3d9522
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966375"
---
# <a name="the-messagebox-database"></a><span data-ttu-id="fb198-102">MessageBox 資料庫</span><span class="sxs-lookup"><span data-stu-id="fb198-102">The MessageBox Database</span></span>
<span data-ttu-id="fb198-103">在 Microsoft BizTalk Server 中發佈/訂閱引擎的中心是 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fb198-103">The heart of the publish/subscribe engine in Microsoft BizTalk Server is the MessageBox database.</span></span> <span data-ttu-id="fb198-104">MessageBox 是由兩個元件組成：一或多個 Microsoft SQL Server 資料庫和傳訊代理程式。</span><span class="sxs-lookup"><span data-stu-id="fb198-104">The MessageBox is made up of two components: one or more Microsoft SQL Server databases and the Messaging Agent.</span></span> <span data-ttu-id="fb198-105">SQL Server 資料庫會提供許多項目的持續性存放區，這些項目包括訊息、訊息部分、訊息屬性、訂閱、協調流程狀態、追蹤資料、路由的主控件佇列，以及其他項目。</span><span class="sxs-lookup"><span data-stu-id="fb198-105">The SQL Server database provides the persistence store for many things including messages, message parts, message properties, subscriptions, orchestration state, tracking data, host queues for routing, and others.</span></span> <span data-ttu-id="fb198-106">BizTalk Server 群組可能會有一或多個 MessageBox 資料庫，可讓它發佈訊息到其中，而那些訊息的訂閱者也會從其中擷取訊息。</span><span class="sxs-lookup"><span data-stu-id="fb198-106">The BizTalk Server group may have one or more MessageBox databases into which it publishes messages and from which subscribers to those messages extract messages.</span></span>  
  
 <span data-ttu-id="fb198-107">資料庫提供與路由訊息及完成訂閱相關的部分邏輯。</span><span class="sxs-lookup"><span data-stu-id="fb198-107">The database provides some of the logic related to routing messages and fulfilling subscriptions.</span></span> <span data-ttu-id="fb198-108">不過，訊息代理程式是封裝和抽象化資料庫元件的元件，也是 BizTalk Server 與 MessageBox 互動所使用的介面。</span><span class="sxs-lookup"><span data-stu-id="fb198-108">The Message Agent, however, is the component that encapsulates and abstracts the database component and is the interface used by BizTalk Server to interact with the MessageBox.</span></span> <span data-ttu-id="fb198-109">訊息代理程式是提供發佈訊息、訂閱訊息、擷取訊息等介面的「元件物件模型」(COM) 元件。</span><span class="sxs-lookup"><span data-stu-id="fb198-109">The Message Agent is a Component Object Model (COM) component that provides interfaces for publishing messages, subscribing to messages, retrieving messages, and so on.</span></span> <span data-ttu-id="fb198-110">這個介面是其他 BizTalk Server 元件 (包括配接器架構和協調流程) 用來與 MessageBox 互動的唯一機制。</span><span class="sxs-lookup"><span data-stu-id="fb198-110">This interface is the only mechanism used by other BizTalk Server components, including the adapter framework and orchestrations, to interact with the MessageBox.</span></span>  
  
## <a name="the-messagebox-and-the-message"></a><span data-ttu-id="fb198-111">MessageBox 和訊息</span><span class="sxs-lookup"><span data-stu-id="fb198-111">The MessageBox and the Message</span></span>  
 <span data-ttu-id="fb198-112">MessageBox 資料庫訂閱是一組建立的資訊和服務資訊。</span><span class="sxs-lookup"><span data-stu-id="fb198-112">A MessageBox database subscription is a set of established information and service information.</span></span> <span data-ttu-id="fb198-113">建立的 (或述詞) 資訊是訊息必須符合的準則。</span><span class="sxs-lookup"><span data-stu-id="fb198-113">The established (or predicate) information is the criteria that a message must meet.</span></span> <span data-ttu-id="fb198-114">服務資訊是處理符合準則之訊息的方法。</span><span class="sxs-lookup"><span data-stu-id="fb198-114">The service information is what to do with the message that meets the criteria.</span></span> <span data-ttu-id="fb198-115">這個資訊的全部都儲存在可呼叫傳訊與協調流程引擎的一組資料表中。</span><span class="sxs-lookup"><span data-stu-id="fb198-115">All of this information is stored in a set of tables that call the messaging and orchestration engine.</span></span>  
  
 <span data-ttu-id="fb198-116">當 BizTalk Server 接收訊息時，它會在管線中處理訊息，並將訊息存放在 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fb198-116">When BizTalk Server receives a message, it processes the message in a pipeline, and places the message in the MessageBox database.</span></span> <span data-ttu-id="fb198-117">內送訊息有內容。</span><span class="sxs-lookup"><span data-stu-id="fb198-117">The incoming message has a context.</span></span> <span data-ttu-id="fb198-118">訊息內容是一組與訊息相關的屬性。</span><span class="sxs-lookup"><span data-stu-id="fb198-118">The message context is a set of properties associated with the message.</span></span> <span data-ttu-id="fb198-119">訊息內容屬性有三種類型：</span><span class="sxs-lookup"><span data-stu-id="fb198-119">The three types of message context properties are:</span></span>  
  
- <span data-ttu-id="fb198-120">簡單寫入屬性</span><span class="sxs-lookup"><span data-stu-id="fb198-120">Simple written properties</span></span>  
  
- <span data-ttu-id="fb198-121">升級屬性</span><span class="sxs-lookup"><span data-stu-id="fb198-121">Promoted properties</span></span>  
  
- <span data-ttu-id="fb198-122">述詞屬性</span><span class="sxs-lookup"><span data-stu-id="fb198-122">Predicate properties</span></span>  
  
  <span data-ttu-id="fb198-123">升級與述詞訊息屬性會指出訂閱此訊息的商務程序，以及商務程序是否有接收訊息所需的權限。</span><span class="sxs-lookup"><span data-stu-id="fb198-123">The promoted and predicate message properties indicate the business process that subscribes to this message, and whether the business process has the permissions necessary to receive the message.</span></span>  
  
  <span data-ttu-id="fb198-124">若商務程序訂閱訊息，MessageBox 資料庫會將訊息傳送到商務程序。</span><span class="sxs-lookup"><span data-stu-id="fb198-124">If a business process subscribes to the message, the MessageBox database sends the message to the business process.</span></span> <span data-ttu-id="fb198-125">當商務程序接收訊息時，它會在可用的主控件執行個體上處理訊息。</span><span class="sxs-lookup"><span data-stu-id="fb198-125">When the business process receives the message, it processes the message on an available host instance.</span></span> <span data-ttu-id="fb198-126">處理訊息之後，若商務程序訂閱一個管線或傳送埠，則商務程序會傳送一個回傳訊息到 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fb198-126">After processing the message, if the business process subscribes to a pipeline or send port, the business process sends a return message to the MessageBox database.</span></span>  
  
  <span data-ttu-id="fb198-127">對於每個 BizTalk 主控件，相關的 MessageBox 會有一個工作佇列和一個擱置的佇列。</span><span class="sxs-lookup"><span data-stu-id="fb198-127">For each BizTalk Host, the associated MessageBox has one work queue and one suspended queue.</span></span> <span data-ttu-id="fb198-128">此外，每個 MessageBox 資料庫都會包含一組靜態狀態、動態狀態和執行個體狀態的資料表。</span><span class="sxs-lookup"><span data-stu-id="fb198-128">Additionally, each MessageBox database contains a set of tables for static states, dynamic states, and instance state.</span></span> <span data-ttu-id="fb198-129">如需 BizTalk 主控件的詳細資訊，請參閱[實體](../core/entities.md)。</span><span class="sxs-lookup"><span data-stu-id="fb198-129">For information about BizTalk Hosts, see [Entities](../core/entities.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fb198-130">若主控件變成無法使用 (例如，從該主控件接收訊息的 MessageBox 資料庫變成無法使用)，則所有其他 MessageBox 資料庫都會變成無法使用。</span><span class="sxs-lookup"><span data-stu-id="fb198-130">If a host becomes unavailable --for example, the MessageBox database that receives messages from that host becomes unavailable, all other MessageBox databases become unavailable.</span></span>  
  
 <span data-ttu-id="fb198-131">當您執行「組態精靈」時，就會建立第一個 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fb198-131">You create the first MessageBox database when you run the Configuration Wizard.</span></span> <span data-ttu-id="fb198-132">設定的 MessageBox 資料庫會變成主要 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fb198-132">The MessageBox database that is configured becomes the master MessageBox database.</span></span> <span data-ttu-id="fb198-133">主要 MessageBox 資料庫會評估訂閱，並將其路由至 BizTalk Server 環境中的所有其他 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="fb198-133">The master MessageBox database evaluates and routes subscriptions to all other MessageBox databases in the BizTalk Server environment.</span></span> <span data-ttu-id="fb198-134">如需改善主要 MessageBox 資料庫的效能資訊，請參閱[管理 MessageBox 資料庫](../core/managing-messagebox-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="fb198-134">For information about improving performance for the master MessageBox database, see [Managing MessageBox Databases](../core/managing-messagebox-databases.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fb198-135">您必須使用 SQL Server 叢集，來提供 MessageBox 資料庫的容錯移轉保護。</span><span class="sxs-lookup"><span data-stu-id="fb198-135">You must use SQL Server clustering to provide failover protection for MessageBox databases.</span></span>  
  
## <a name="suspended-messages-in-the-messagebox-database"></a><span data-ttu-id="fb198-136">MessageBox 資料庫中擱置的訊息</span><span class="sxs-lookup"><span data-stu-id="fb198-136">Suspended Messages in the MessageBox Database</span></span>  
 <span data-ttu-id="fb198-137">BizTalk Server 會儲存與 MessageBox 資料庫中擱置管線相關的訊息。</span><span class="sxs-lookup"><span data-stu-id="fb198-137">BizTalk Server stores messages associated with suspended pipelines in the MessageBox database.</span></span> <span data-ttu-id="fb198-138">若管線中發生容錯轉移，BizTalk Server 會擱置訊息的執行個體。</span><span class="sxs-lookup"><span data-stu-id="fb198-138">If a failure occurs in the pipeline, BizTalk Server suspends the instance of a message.</span></span> <span data-ttu-id="fb198-139">擱置的服務執行個體有兩種類型：</span><span class="sxs-lookup"><span data-stu-id="fb198-139">There are two types of suspended service instances:</span></span>  
  
- <span data-ttu-id="fb198-140">您可以繼續的擱置執行個體。</span><span class="sxs-lookup"><span data-stu-id="fb198-140">Suspended instances that you can resume.</span></span>  
  
- <span data-ttu-id="fb198-141">您無法繼續的擱置執行個體。</span><span class="sxs-lookup"><span data-stu-id="fb198-141">Suspended instances that you cannot resume.</span></span> <span data-ttu-id="fb198-142">例如，若一個執行個體已損毀。</span><span class="sxs-lookup"><span data-stu-id="fb198-142">For example, if an instance is corrupt.</span></span>  
  
  <span data-ttu-id="fb198-143">視擱置的原因而定，您或許可以繼續 BizTalk Server 擱置的服務，例如，若協調流程叫用「擱置」圖形，或是傳輸無法遞送訊息。BizTalk Server 不會自動移除您無法從 MessageBox 資料庫繼續的擱置執行個體。</span><span class="sxs-lookup"><span data-stu-id="fb198-143">Depending on the cause of the suspension, you may be able to resume services that BizTalk Server suspends -- for example, if an orchestration hits a Suspend shape, or if a transport was unable to deliver a message, BizTalk Server does not automatically remove suspended instances that you cannot resume from the MessageBox database.</span></span> <span data-ttu-id="fb198-144">在從擱置的佇列移除服務執行個體之前，您可以選擇將該服務執行個體儲存至磁碟。</span><span class="sxs-lookup"><span data-stu-id="fb198-144">You can choose to save a service instance to disk before removing it from the suspended queue.</span></span>  
  
  <span data-ttu-id="fb198-145">如需備份 MessageBox 資料庫的詳細資訊，請參閱 <<c0> [ 備份和還原 BizTalk Server 資料庫](../core/backing-up-and-restoring-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="fb198-145">For information about backing up MessageBox databases, see [Backing Up and Restoring BizTalk Server Databases](../core/backing-up-and-restoring-biztalk-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb198-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb198-146">See Also</span></span>  
 [<span data-ttu-id="fb198-147">傳訊引擎</span><span class="sxs-lookup"><span data-stu-id="fb198-147">The Messaging Engine</span></span>](../core/the-messaging-engine.md)