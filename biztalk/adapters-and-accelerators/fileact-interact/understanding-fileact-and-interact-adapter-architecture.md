---
title: 了解 FileAct 和互動的配接器架構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f97a7fe-20df-4509-bb6e-53743c3a57df
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c04d0ba8b1c2bbd99a71e3d76c8d7ad60c251147
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223406"
---
# <a name="understanding-fileact-and-interact-adapter-architecture"></a><span data-ttu-id="60a43-102">了解 FileAct 和互動的配接器架構</span><span class="sxs-lookup"><span data-stu-id="60a43-102">Understanding FileAct and InterAct Adapter Architecture</span></span>
<span data-ttu-id="60a43-103">SWIFT 配接器是以 BizTalk 配接器架構為基礎。</span><span class="sxs-lookup"><span data-stu-id="60a43-103">The SWIFT Adapter is based on the BizTalk Adapter Framework.</span></span> <span data-ttu-id="60a43-104">使用 BizTalk Server 中的配接器的分類，快速的配接器，FileAct 和 InterAct，代表下列各項：</span><span class="sxs-lookup"><span data-stu-id="60a43-104">Using the classifications of adapters within BizTalk Server, the SWIFT adapters, FileAct and InterAct, represent the following:</span></span>  
  
-   <span data-ttu-id="60a43-105">自訂配接器。</span><span class="sxs-lookup"><span data-stu-id="60a43-105">Custom Adapter.</span></span> <span data-ttu-id="60a43-106">這是為了與使用專屬的標準呼叫 FileAct 和 Interact 的 SWIFT 網路互動的自訂配接器。</span><span class="sxs-lookup"><span data-stu-id="60a43-106">This is a custom adapter built specifically to interact with the SWIFT network using a proprietary standard called FileAct and Interact.</span></span>  
  
-   <span data-ttu-id="60a43-107">傳輸配接器。</span><span class="sxs-lookup"><span data-stu-id="60a43-107">Transport Adapter.</span></span> <span data-ttu-id="60a43-108">此配接器可讓商務軟體應用程式來傳送和接收訊息的 SWIFT 網路。</span><span class="sxs-lookup"><span data-stu-id="60a43-108">This adapter allows business software application to send and receive messages with the SWIFT network.</span></span>  
  
-   <span data-ttu-id="60a43-109">非交易。</span><span class="sxs-lookup"><span data-stu-id="60a43-109">Non-transacted.</span></span> <span data-ttu-id="60a43-110">配接器不會進行互動的 SWIFT 網路使用的任何交易物件。</span><span class="sxs-lookup"><span data-stu-id="60a43-110">The adapter does not make use of any transaction object to interact with the SWIFT network.</span></span>  
  
-   <span data-ttu-id="60a43-111">外掛式。</span><span class="sxs-lookup"><span data-stu-id="60a43-111">Isolated.</span></span> <span data-ttu-id="60a43-112">接收配接器執行個別的處理序中，並定期傳送配接器處理序中執行。</span><span class="sxs-lookup"><span data-stu-id="60a43-112">The receive adapter runs in a separate process and regular send adapters run in process.</span></span>  
  
 <span data-ttu-id="60a43-113">BizTalk 配接器架構的相關資訊，請參閱 < 什麼是配接器架構？ ></span><span class="sxs-lookup"><span data-stu-id="60a43-113">For information about the BizTalk Adapter Framework, see the "What Is the Adapter Framework?"</span></span> <span data-ttu-id="60a43-114">在 BizTalk Server 說明中的主題。</span><span class="sxs-lookup"><span data-stu-id="60a43-114">topic in BizTalk Server Help.</span></span>  
  
 <span data-ttu-id="60a43-115">下圖顯示 FileAct 和 InterAct 架構的高階檢視。</span><span class="sxs-lookup"><span data-stu-id="60a43-115">The following figure shows a high-level view of the FileAct and InterAct architecture.</span></span>  
  
 ![](../../adapters-and-accelerators/fileact-interact/media/035ebb05-ce11-447c-b56b-ba8b41e07e50.gif "035ebb05-ce11-447c-b56b-ba8b41e07e50")  
  
> [!NOTE]
>  <span data-ttu-id="60a43-116">Microsoft[!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]支援 strict 模式 SWIFTNet 連結 (SNL) API。</span><span class="sxs-lookup"><span data-stu-id="60a43-116">Microsoft [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] supports only strict mode SWIFTNet Link (SNL) API.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="60a43-117">本節內容</span><span class="sxs-lookup"><span data-stu-id="60a43-117">In This Section</span></span>  
  
-   [<span data-ttu-id="60a43-118">SWIFTNet 用戶端和伺服器</span><span class="sxs-lookup"><span data-stu-id="60a43-118">SWIFTNet Client and Server</span></span>](../../adapters-and-accelerators/fileact-interact/swiftnet-client-and-server.md)  
  
-   [<span data-ttu-id="60a43-119">SWIFT 傳送配接器架構</span><span class="sxs-lookup"><span data-stu-id="60a43-119">SWIFT Send Adapter Architecture</span></span>](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-architecture.md)  
  
-   [<span data-ttu-id="60a43-120">SWIFT 接收配接器架構</span><span class="sxs-lookup"><span data-stu-id="60a43-120">SWIFT Receive Adapter Architecture</span></span>](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md)  
  
-   [<span data-ttu-id="60a43-121">FileAct 配接器架構</span><span class="sxs-lookup"><span data-stu-id="60a43-121">FileAct Adapter Architecture</span></span>](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md)  
  
-   [<span data-ttu-id="60a43-122">互動的配接器架構</span><span class="sxs-lookup"><span data-stu-id="60a43-122">InterAct Adapter Architecture</span></span>](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)