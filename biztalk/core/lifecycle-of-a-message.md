---
title: 訊息的生命週期 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- messages, MessageBox database
- messages, orchestrations
- messages, host instances
- messages, receive locations
- send ports, about send ports
- processing, messages
- messages, processing
- host instances, about host instances
- receive locations, about receive locations
- hosts, about hosts
- messages, lifecycle
- MessageBox database, about MessageBox database
- receive ports, about receive ports
- send port groups, about send port groups
- messages, hosts
- messages, send port groups
- messages, receive ports
- orchestrations, about orchestrations
- messages, send ports
ms.assetid: d2374f86-9b5f-404f-ba7b-9cab69873fa8
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e05aca3ec819fb8615552c5ed57114032d7ea60b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22262822"
---
# <a name="lifecycle-of-a-message"></a><span data-ttu-id="c0a16-102">訊息的生命週期</span><span class="sxs-lookup"><span data-stu-id="c0a16-102">Lifecycle of a Message</span></span>
<span data-ttu-id="c0a16-103">下圖提供從傳訊觀點來看的 BizTalk Server 架構之概要簡介。</span><span class="sxs-lookup"><span data-stu-id="c0a16-103">The following figure provides a high-level overview of the BizTalk Server architecture from a messaging perspective.</span></span>  
  
 <span data-ttu-id="c0a16-104">![BizTalk Server 傳訊架構](../core/media/arch-messaging-01.gif "arch_messaging_01")</span><span class="sxs-lookup"><span data-stu-id="c0a16-104">![BizTalk Server messaging architecture](../core/media/arch-messaging-01.gif "arch_messaging_01")</span></span>  
  
 <span data-ttu-id="c0a16-105">在此簡化的檢視中，訊息是透過指定接收埠所定義的接收位置來接收。</span><span class="sxs-lookup"><span data-stu-id="c0a16-105">In this simplified view, a message is received through a receive location defined in a given receive port.</span></span> <span data-ttu-id="c0a16-106">此訊息是由接收位置所處理，然後發佈到 MessageBox 資料庫，這是 BizTalk Server 的主要保存與路由機制。</span><span class="sxs-lookup"><span data-stu-id="c0a16-106">This message is processed by the receive location and then published to the MessageBox database, the main persistence and routing mechanism for BizTalk Server.</span></span> <span data-ttu-id="c0a16-107">MessageBox 會評估作用中的訂閱，並將訊息路由至具有符合訂閱的協調流程與傳送埠。</span><span class="sxs-lookup"><span data-stu-id="c0a16-107">The MessageBox evaluates active subscriptions and routes the message to those orchestrations and send ports with matching subscriptions.</span></span> <span data-ttu-id="c0a16-108">協調流程可能會透過 MessageBox 處理訊息並將訊息發佈到傳送埠，在此傳送埠上會將訊息推出至其最終目的地。</span><span class="sxs-lookup"><span data-stu-id="c0a16-108">Orchestrations may process the message and publish messages through the MessageBox to a send port where it is pushed out to its final destination.</span></span>  
  
 <span data-ttu-id="c0a16-109">下列是 BizTalk Server 訊息處理所需的主要元件。</span><span class="sxs-lookup"><span data-stu-id="c0a16-109">The following are key components involved in BizTalk Server message processing.</span></span>  
  
## <a name="receive-ports-and-receive-locations"></a><span data-ttu-id="c0a16-110">接收埠與接收位置</span><span class="sxs-lookup"><span data-stu-id="c0a16-110">Receive Ports and Receive Locations</span></span>  
 <span data-ttu-id="c0a16-111">A*接收埠*是集合的一個或多個接收到 BizTalk Server 定義特定的進入點的位置。</span><span class="sxs-lookup"><span data-stu-id="c0a16-111">A *receive port* is a collection of one or more receive locations that define specific entry points into BizTalk Server.</span></span> <span data-ttu-id="c0a16-112">A*接收位置*是單一的端點 (URL) 的組態來接收訊息。</span><span class="sxs-lookup"><span data-stu-id="c0a16-112">A *receive location* is the configuration of a single endpoint (URL) to receive messages.</span></span> <span data-ttu-id="c0a16-113">此位置包含接收配接器與接收管線的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="c0a16-113">The location contains configuration information for both a receive adapter and a receive pipeline.</span></span> <span data-ttu-id="c0a16-114">*配接器*負責接收訊息的傳輸與通訊部分。</span><span class="sxs-lookup"><span data-stu-id="c0a16-114">The *adapter* is responsible for the transport and communications part of receiving a message.</span></span> <span data-ttu-id="c0a16-115">像這樣的範例有 FILE 配接器與 SOAP 配接器，每一個配接器都從不同類型的來源接收訊息。</span><span class="sxs-lookup"><span data-stu-id="c0a16-115">Examples include the File adapter and SOAP adapter, each of which receives messages from different types of sources.</span></span> <span data-ttu-id="c0a16-116">接收管線負責準備要發佈到 MessageBox 的訊息。</span><span class="sxs-lookup"><span data-stu-id="c0a16-116">The receive pipeline is responsible for preparing the message for publishing into the MessageBox.</span></span> <span data-ttu-id="c0a16-117">A*管線*是一系列的順序，每個提供特定處理的訊息，例如解密/加密、 剖析或驗證來執行的元件。</span><span class="sxs-lookup"><span data-stu-id="c0a16-117">A *pipeline* is a series of components that are executed in sequence, each providing specific processing to a message such as decryption/encryption, parsing, or validation.</span></span> <span data-ttu-id="c0a16-118">如需管線的詳細資訊，接收埠和接收位置，請參閱[成品](../core/artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="c0a16-118">For more information about pipelines, receive ports, and receive locations, see [Artifacts](../core/artifacts.md).</span></span>  
  
## <a name="send-ports-and-send-port-groups"></a><span data-ttu-id="c0a16-119">傳送埠與傳送埠群組</span><span class="sxs-lookup"><span data-stu-id="c0a16-119">Send Ports and Send Port Groups</span></span>  
 <span data-ttu-id="c0a16-120">A*傳送埠*是傳送管線和傳送配接器的組合。</span><span class="sxs-lookup"><span data-stu-id="c0a16-120">A *send port* is the combination of a send pipeline and a send adapter.</span></span> <span data-ttu-id="c0a16-121">傳送埠群組是傳送埠的集合，與電子郵件通訊群組清單的運作方式非常相似。</span><span class="sxs-lookup"><span data-stu-id="c0a16-121">A send port group is a collection of send ports and works much like an e-mail distribution list.</span></span> <span data-ttu-id="c0a16-122">傳送到傳送埠群組的訊息將會傳送到該群組的所有傳送埠。</span><span class="sxs-lookup"><span data-stu-id="c0a16-122">A message sent to a send port group will be sent to all send ports in that group.</span></span> <span data-ttu-id="c0a16-123">傳送管線是用來準備將源自 BizTalk Server 的訊息傳輸到另一個服務。</span><span class="sxs-lookup"><span data-stu-id="c0a16-123">The send pipeline is used to prepare a message coming from BizTalk Server for transmission to another service.</span></span> <span data-ttu-id="c0a16-124">傳送配接器負責使用特定通訊協定 (如 SOAP 或 FTP) 來實際傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="c0a16-124">The send adapter is responsible for actually sending the message using a specific protocol such as SOAP, or FTP.</span></span> <span data-ttu-id="c0a16-125">如需有關傳送埠與傳送埠群組的詳細資訊，請參閱[成品](../core/artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="c0a16-125">For more information on send ports and send port groups, see [Artifacts](../core/artifacts.md).</span></span>  
  
## <a name="orchestrations"></a><span data-ttu-id="c0a16-126">協調流程</span><span class="sxs-lookup"><span data-stu-id="c0a16-126">Orchestrations</span></span>  
 <span data-ttu-id="c0a16-127">協調流程可以透過 MessageBox 訂閱 (接收) 和發佈 (傳送) 訊息。</span><span class="sxs-lookup"><span data-stu-id="c0a16-127">Orchestrations can subscribe to (receive) and publish (send) messages through the MessageBox.</span></span> <span data-ttu-id="c0a16-128">此外，協調流程可以建構新的訊息。</span><span class="sxs-lookup"><span data-stu-id="c0a16-128">In addition, orchestrations can construct new messages.</span></span> <span data-ttu-id="c0a16-129">我們已經討論過藉由使用訂閱與路由機制來接收訊息。</span><span class="sxs-lookup"><span data-stu-id="c0a16-129">Messages are received using the subscription and routing mechanism already discussed.</span></span> <span data-ttu-id="c0a16-130">若已為協調流程填入訂閱，則會啟動新的執行個體並傳送訊息，或者，在執行個體訂閱的狀況下，若有需要，執行個體會解除凍結，然後會傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="c0a16-130">When subscriptions are filled for orchestrations, a new instance is activated and the message is delivered, or in the case of instance subscriptions, the instance is rehydrated if necessary and the message is then delivered.</span></span> <span data-ttu-id="c0a16-131">當訊息從協調流程傳送時，會以訊息到達接收位置的相同方式來將它們發佈至 MessageBox，並將適當的屬性插入資料庫以供路由使用。</span><span class="sxs-lookup"><span data-stu-id="c0a16-131">When messages are sent from an orchestration, they are published to the MessageBox in the same manner as a message arriving at a receive location with the appropriate properties is inserted into the database for use in routing.</span></span> <span data-ttu-id="c0a16-132">如需協調流程的詳細資訊，請參閱[成品](../core/artifacts.md)。</span><span class="sxs-lookup"><span data-stu-id="c0a16-132">For more information about orchestrations, see [Artifacts](../core/artifacts.md).</span></span>  
  
## <a name="messagebox-database"></a><span data-ttu-id="c0a16-133">MessageBox 資料庫</span><span class="sxs-lookup"><span data-stu-id="c0a16-133">MessageBox Database</span></span>  
 <span data-ttu-id="c0a16-134">BizTalk Server 中發佈/訂閱引擎的核心為 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c0a16-134">The heart of the publish/subscribe engine in BizTalk Server is the MessageBox database.</span></span> <span data-ttu-id="c0a16-135">MessageBox 是由兩個元件所組成：一或多個 Microsoft SQL Server 資料庫以及訊息代理程式。</span><span class="sxs-lookup"><span data-stu-id="c0a16-135">The MessageBox is made up of two components: one or more Microsoft SQL Server databases and the Message Agent.</span></span> <span data-ttu-id="c0a16-136">SQL Server 資料庫為許多項目提供持續的存放區，包括訊息、訊息屬性、訂閱、協調流程狀態、追蹤資料以及要路由的主控件佇列。</span><span class="sxs-lookup"><span data-stu-id="c0a16-136">The SQL Server database provides the persistence store for many things including messages, message properties, subscriptions, orchestration states, tracking data, and host queues for routing.</span></span> <span data-ttu-id="c0a16-137">如需 MessageBox 資料庫的詳細資訊，請參閱[MessageBox 資料庫](../core/the-messagebox-database.md)。</span><span class="sxs-lookup"><span data-stu-id="c0a16-137">For more information about the MessageBox database, see [The MessageBox Database](../core/the-messagebox-database.md).</span></span>  
  
## <a name="hosts-and-host-instances"></a><span data-ttu-id="c0a16-138">主控件與主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="c0a16-138">Hosts and Host Instances</span></span>  
 <span data-ttu-id="c0a16-139">A*主機*是執行 BizTalk Server 成品，例如 Microsoft Windows 處理序的邏輯表示法傳送埠和協調流程。</span><span class="sxs-lookup"><span data-stu-id="c0a16-139">A *host* is a logical representation of a Microsoft Windows process that executes BizTalk Server artifacts such as send ports and orchestrations.</span></span> <span data-ttu-id="c0a16-140">A*主控件執行個體*是特定伺服器上的主機的實體表示法。</span><span class="sxs-lookup"><span data-stu-id="c0a16-140">A *host instance* is the physical representation of a host on a specific server.</span></span> <span data-ttu-id="c0a16-141">主控件可以是內含式主控件，這表示它是由 BizTalk Server 所擁有和管理，或者是外掛式主控件，這表示 BizTalk Server 程式碼是在不受 BizTalk Server 控制的程序中執行。</span><span class="sxs-lookup"><span data-stu-id="c0a16-141">A host can be either an in-process host, which means it is owned and managed by BizTalk Server, or an isolated host, which means that the BizTalk Server code is running in a process that is not controlled by BizTalk Server.</span></span> <span data-ttu-id="c0a16-142">外掛式主控件最好的範例就是 Internet Information Services (IIS)，它裝載 HTTP 與 SOAP 配接器的接收功能。</span><span class="sxs-lookup"><span data-stu-id="c0a16-142">A good example of an isolated host is Internet Information Services (IIS), which hosts the receive functionality of the HTTP and SOAP adapters.</span></span> <span data-ttu-id="c0a16-143">主控件是為整個 BizTalk Server 群組所定義；是共用組態、MessageBox、連接埠等等的 BizTalk Server 集合。</span><span class="sxs-lookup"><span data-stu-id="c0a16-143">Hosts are defined for an entire BizTalk Server group; a collection of BizTalk Servers that share configuration, MessageBoxes, ports, and so on.</span></span> <span data-ttu-id="c0a16-144">如需主控件和主控件執行個體的詳細資訊，請參閱[實體](../core/entities.md)。</span><span class="sxs-lookup"><span data-stu-id="c0a16-144">For more information about hosts and host instances, see [Entities](../core/entities.md).</span></span>  
  
## <a name="saving-a-message-body"></a><span data-ttu-id="c0a16-145">儲存訊息內文</span><span class="sxs-lookup"><span data-stu-id="c0a16-145">Saving a Message Body</span></span>  
 <span data-ttu-id="c0a16-146">有三種方法可以儲存訊息內文。</span><span class="sxs-lookup"><span data-stu-id="c0a16-146">There are three ways to save a message body.</span></span>  
  
### <a name="from-the-admin-mmc-group-hub-page-queries"></a><span data-ttu-id="c0a16-147">從 [管理] MMC 群組中樞頁面查詢</span><span class="sxs-lookup"><span data-stu-id="c0a16-147">From the Admin MMC group hub page queries</span></span>  
 <span data-ttu-id="c0a16-148">此方法僅適用於 MessageBox 資料庫中的訊息。</span><span class="sxs-lookup"><span data-stu-id="c0a16-148">This method is for messages in the MessageBox database only.</span></span>  
  
-   <span data-ttu-id="c0a16-149">檢視服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="c0a16-149">View a Service Instance.</span></span>  
  
-   <span data-ttu-id="c0a16-150">開啟**服務執行個體詳細資料** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c0a16-150">Open the **Service Instance Details** dialog box.</span></span>  
  
-   <span data-ttu-id="c0a16-151">按一下**訊息索引標籤**若要檢視與此執行個體相關聯的訊息清單。</span><span class="sxs-lookup"><span data-stu-id="c0a16-151">Click the **Messages Tab** to view the list of messages associated with this instance.</span></span>  
  
-   <span data-ttu-id="c0a16-152">請以滑鼠右鍵按一下訊息，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="c0a16-152">Either right-click the message, and then click **Save**.</span></span>  
  
     <span data-ttu-id="c0a16-153">-或-</span><span class="sxs-lookup"><span data-stu-id="c0a16-153">-or-</span></span>  
  
-   <span data-ttu-id="c0a16-154">按兩下要開啟中的訊息**訊息檢視器**，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="c0a16-154">Double-click the message to open it in the **Message Viewer**, and click **Save**.</span></span>  
  
### <a name="from-the-operations-om"></a><span data-ttu-id="c0a16-155">從作業 OM</span><span class="sxs-lookup"><span data-stu-id="c0a16-155">From the Operations OM</span></span>  
  
-   <span data-ttu-id="c0a16-156">使用**GetInstance**擷取服務執行個體物件。</span><span class="sxs-lookup"><span data-stu-id="c0a16-156">Use **GetInstance** to retrieve a Service Instance object.</span></span>  
  
-   <span data-ttu-id="c0a16-157">使用**Instance.Messages []** 列舉服務執行個體目前參考的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="c0a16-157">Use **Instance.Messages [ ]** to enumerate all messages which the service instance currently references.</span></span>  
  
-   <span data-ttu-id="c0a16-158">訊息物件上使用方法，例如**Message.BodyPart []** 和**Message.Context []** 存取並儲存它。</span><span class="sxs-lookup"><span data-stu-id="c0a16-158">Use methods on the message object such as **Message.BodyPart [ ]** and **Message.Context [  ]** to access and save it.</span></span>  
  
### <a name="from-the-dta"></a><span data-ttu-id="c0a16-159">從 DTA</span><span class="sxs-lookup"><span data-stu-id="c0a16-159">From the DTA</span></span>  
  
-   <span data-ttu-id="c0a16-160">從使用 DTA 擷取訊息**GetTrackedInstance**和**GetTrackedmessage** API 呼叫。</span><span class="sxs-lookup"><span data-stu-id="c0a16-160">Retrieve messages from the DTA using the **GetTrackedInstance** and **GetTrackedmessage** API calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0a16-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0a16-161">See Also</span></span>  
 [<span data-ttu-id="c0a16-162">執行階段架構</span><span class="sxs-lookup"><span data-stu-id="c0a16-162">Runtime Architecture</span></span>](../core/runtime-architecture.md)