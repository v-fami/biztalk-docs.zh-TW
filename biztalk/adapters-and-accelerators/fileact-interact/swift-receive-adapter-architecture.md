---
title: SWIFT 接收配接器架構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 16f32689-0b70-4389-8596-991fd776f185
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3aca9b5ef1fd1130feeebad3ec6fdf072d3bf88d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224982"
---
# <a name="swift-receive-adapter-architecture"></a><span data-ttu-id="35f95-102">SWIFT 接收配接器架構</span><span class="sxs-lookup"><span data-stu-id="35f95-102">SWIFT Receive Adapter Architecture</span></span>
<span data-ttu-id="35f95-103">在 BizTalk Server 中，接收配接器會裝載於自己的記憶體空間，這表示不同的處理序是用來執行主機內。</span><span class="sxs-lookup"><span data-stu-id="35f95-103">In BizTalk Server, the receive adapter is hosted within its own memory space, which means a separate process is created to run the host.</span></span> <span data-ttu-id="35f95-104">此主機未繁衍 SWIFTNet 連結 (SNL) 組態中定義的子系統。</span><span class="sxs-lookup"><span data-stu-id="35f95-104">This host is spawned by defining a subsystem in the SWIFTNet Link (SNL) configuration.</span></span>  
  
 <span data-ttu-id="35f95-105">伺服器可執行檔會設定為 SNL 組態 (paramfile) 中的子系統，並產生藉由執行 SWIFTNet 啟動命令。</span><span class="sxs-lookup"><span data-stu-id="35f95-105">The server executable is configured as a subsystem in the SNL configuration (paramfile) and is spawned by executing the SWIFTNet Start command.</span></span> <span data-ttu-id="35f95-106">SNL 伺服器應用程式便會終止執行 SWIFTNet 停止命令。</span><span class="sxs-lookup"><span data-stu-id="35f95-106">The SNL server application is terminated by executing the SWIFTNet Stop command.</span></span> <span data-ttu-id="35f95-107">SNL 管理伺服器可執行檔的存留期間。</span><span class="sxs-lookup"><span data-stu-id="35f95-107">SNL manages the lifetime of the server executable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35f95-108">服務局案例需要服務在其自己的安全性內容下執行的多個 SWIFT 成員介面卡。</span><span class="sxs-lookup"><span data-stu-id="35f95-108">The service bureau scenario requires the adapter to service multiple SWIFT members running under their own security contexts.</span></span> <span data-ttu-id="35f95-109">藉由設定個別支援此接收位置，每個成員和繁衍 （spawn） 的伺服器可執行檔的多個執行個體，每一部專門用於其中一個接收位置。</span><span class="sxs-lookup"><span data-stu-id="35f95-109">This can be supported by configuring an individual receive location per member and spawning multiple instances of the server executable — each one dedicated to one receive location.</span></span>  
  
 <span data-ttu-id="35f95-110">在 BizTalk Server 中，接收配接器支援下列通訊模式與 「 BizTalk 傳訊引擎互動：</span><span class="sxs-lookup"><span data-stu-id="35f95-110">In BizTalk Server, the receive adapter supports the following communication patterns to interact with the BizTalk Messaging Engine:</span></span>  
  
-   <span data-ttu-id="35f95-111">其中一種方式 — 接收配接器 （伺服器） 正在延遲模式下運作時，就需要此模式。</span><span class="sxs-lookup"><span data-stu-id="35f95-111">One way — this mode is required when the receive adapter (server) is operating in deferred mode.</span></span> <span data-ttu-id="35f95-112">在延遲模式中，配接器會傳送內送訊息的預設通知。</span><span class="sxs-lookup"><span data-stu-id="35f95-112">In deferred mode, the adapter sends a default acknowledgment for incoming messages.</span></span> <span data-ttu-id="35f95-113">通知的預設值可以設定在配接器屬性。</span><span class="sxs-lookup"><span data-stu-id="35f95-113">The default values for the acknowledgment can be configured in the adapter properties.</span></span> <span data-ttu-id="35f95-114">可以透過傳送配接器的 LOB 應用程式稍後傳送商務層級回應。</span><span class="sxs-lookup"><span data-stu-id="35f95-114">Business level response can be sent later by the LOB application through the send adapter.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="35f95-115">發生延遲模式中，所有的值必須被填滿在配接器組態中，因為配接器做為建構回應。</span><span class="sxs-lookup"><span data-stu-id="35f95-115">In case of deferred mode, all values must be filled up in the adapter configuration, since the adapter is constructing the response.</span></span>  
  
-   <span data-ttu-id="35f95-116">要求回應 — 在此模式中，配接器提交至 BizTalk 來自 SWIFT 要求並等候回應。</span><span class="sxs-lookup"><span data-stu-id="35f95-116">Request response — in this mode the adapter submits the request from SWIFT to BizTalk and waits for response.</span></span> <span data-ttu-id="35f95-117">如果從 LOB 應用程式沒有回應，配接器將會逾時。</span><span class="sxs-lookup"><span data-stu-id="35f95-117">The adapter would timeout if there is no response from the LOB application.</span></span> <span data-ttu-id="35f95-118">逾時值是在配接器組態中設定的。</span><span class="sxs-lookup"><span data-stu-id="35f95-118">The time out value is configurable in adapter configuration.</span></span> <span data-ttu-id="35f95-119">預設值為 60 秒。</span><span class="sxs-lookup"><span data-stu-id="35f95-119">The default value is 60 seconds.</span></span>  
  
     <span data-ttu-id="35f95-120">接收配接器可以只在一個執行緒上，以接收來自 SNL 回呼。</span><span class="sxs-lookup"><span data-stu-id="35f95-120">The receive adapter can receive the callback from SNL only on one thread.</span></span> <span data-ttu-id="35f95-121">這表示，接收配接器可以進一步從接收訊息 SNL 只有在送出第一個訊息之後。</span><span class="sxs-lookup"><span data-stu-id="35f95-121">This means that the receive adapter can receive further messages from SNL only after submitting the first message.</span></span> <span data-ttu-id="35f95-122">因此，預設批次大小是設定為 1。</span><span class="sxs-lookup"><span data-stu-id="35f95-122">Therefore, the default batch size is set to 1.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="35f95-123">本節內容</span><span class="sxs-lookup"><span data-stu-id="35f95-123">In This Section</span></span>  
  
-   [<span data-ttu-id="35f95-124">SWIFT 接收配接器 URI</span><span class="sxs-lookup"><span data-stu-id="35f95-124">SWIFT Receive Adapter URI</span></span>](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-uri.md)  
  
-   [<span data-ttu-id="35f95-125">SWIFT 接收配接器初始化</span><span class="sxs-lookup"><span data-stu-id="35f95-125">SWIFT Receive Adapter Initialization</span></span>](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-initialization.md)  
  
-   [<span data-ttu-id="35f95-126">SWIFT 接收配接器的安全性內容</span><span class="sxs-lookup"><span data-stu-id="35f95-126">SWIFT Receive Adapter Security Context</span></span>](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-security-context.md)  
  
-   [<span data-ttu-id="35f95-127">SWIFT 接收配接器同步與延遲模式</span><span class="sxs-lookup"><span data-stu-id="35f95-127">SWIFT Receive Adapter Synchronous and Deferred Modes</span></span>](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-synchronous-and-deferred-modes.md)  
  
-   [<span data-ttu-id="35f95-128">SWIFT 接收配接器儲存與轉送</span><span class="sxs-lookup"><span data-stu-id="35f95-128">SWIFT Receive Adapter Store and Forward</span></span>](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-store-and-forward.md)