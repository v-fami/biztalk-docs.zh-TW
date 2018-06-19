---
title: SWIFT 傳送配接器架構 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e52a5a21-0aa1-4cd9-a2a4-f9df425913a0
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d772203c980495c5aa62266beb060693c1a8ad8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223870"
---
# <a name="swift-send-adapter-architecture"></a><span data-ttu-id="2a5c3-102">SWIFT 傳送配接器架構</span><span class="sxs-lookup"><span data-stu-id="2a5c3-102">SWIFT Send Adapter Architecture</span></span>
<span data-ttu-id="2a5c3-103">一般情況下，BizTalk Server 傳送配接器裝載於 BizTalk 服務處理序，Btsntsvc.exe 中。</span><span class="sxs-lookup"><span data-stu-id="2a5c3-103">In general, BizTalk Server send adapters are hosted in the BizTalk service process, Btsntsvc.exe.</span></span> <span data-ttu-id="2a5c3-104">這表示 BizTalk Server 管理配接器的存留期間。</span><span class="sxs-lookup"><span data-stu-id="2a5c3-104">This means that BizTalk Server manages the lifetime of the adapter.</span></span>  
  
 <span data-ttu-id="2a5c3-105">有兩種方式將訊息傳送到的 SWIFT 網路： 同步的 (ExchangeRequest) 和非同步 （此版本並未實作）。</span><span class="sxs-lookup"><span data-stu-id="2a5c3-105">There are two ways of sending messages to the SWIFT network: synchronous (ExchangeRequest) and asynchronous (not implemented for this release).</span></span> <span data-ttu-id="2a5c3-106">在 BizTalk Server 傳送配接器應支援下列通訊模式與 「 BizTalk 傳訊引擎互動：</span><span class="sxs-lookup"><span data-stu-id="2a5c3-106">In BizTalk Server, the send adapter should support the following communication patterns to interact with the BizTalk Messaging Engine:</span></span>  
  
-   <span data-ttu-id="2a5c3-107">請求回應 — 訊息組，稱為基本項目與 SWIFT 網路種進行交換。</span><span class="sxs-lookup"><span data-stu-id="2a5c3-107">Solicit response — messages are exchanged in pairs, called the primitives, with the SWIFT network.</span></span> <span data-ttu-id="2a5c3-108">任何傳送至 SWIFT 的訊息必須是商務、 通知或錯誤的回應。</span><span class="sxs-lookup"><span data-stu-id="2a5c3-108">Any messages sent to SWIFT will have a response be it business, acknowledgement or error.</span></span> <span data-ttu-id="2a5c3-109">回應訊息提交至 messagebox。</span><span class="sxs-lookup"><span data-stu-id="2a5c3-109">The response message is submitted back to messagebox.</span></span> <span data-ttu-id="2a5c3-110">這種作業模式用於即時通訊。</span><span class="sxs-lookup"><span data-stu-id="2a5c3-110">This mode of operation is used for Real-Time communication.</span></span>  
  
-   <span data-ttu-id="2a5c3-111">其中一種方式傳送，配接器以其中一種方式進行設定時的儲存和轉送模式操作。</span><span class="sxs-lookup"><span data-stu-id="2a5c3-111">One way send — the adapter when configured in one way operates in store and forward mode.</span></span> <span data-ttu-id="2a5c3-112">這些訊息會傳送到預先設定的佇列，而不是收件者。</span><span class="sxs-lookup"><span data-stu-id="2a5c3-112">The messages are sent to a preconfigured queue as opposed to a receipient.</span></span> <span data-ttu-id="2a5c3-113">寄件者可以擷取與佇列發送或提取模式中開啟工作階段的回應。</span><span class="sxs-lookup"><span data-stu-id="2a5c3-113">The sender can retrieve the response by opening a session with the queue in push or pull mode.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a5c3-114">建立配接器的方式會影響它的運作的方式。</span><span class="sxs-lookup"><span data-stu-id="2a5c3-114">The way you create the adapter affects the way it operates.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2a5c3-115">本節內容</span><span class="sxs-lookup"><span data-stu-id="2a5c3-115">In This Section</span></span>  
  
-   [<span data-ttu-id="2a5c3-116">SWIFT 傳送配接器 URI</span><span class="sxs-lookup"><span data-stu-id="2a5c3-116">SWIFT Send Adapter URI</span></span>](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-uri.md)  
  
-   [<span data-ttu-id="2a5c3-117">SWIFT 傳送配接器的動態傳送</span><span class="sxs-lookup"><span data-stu-id="2a5c3-117">SWIFT Send Adapter Dynamic Send</span></span>](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-dynamic-send.md)  
  
-   [<span data-ttu-id="2a5c3-118">SWIFT 傳送配接器初始化</span><span class="sxs-lookup"><span data-stu-id="2a5c3-118">SWIFT Send Adapter Initialization</span></span>](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-initialization.md)  
  
-   [<span data-ttu-id="2a5c3-119">SWIFT 傳送配接器同步模式</span><span class="sxs-lookup"><span data-stu-id="2a5c3-119">SWIFT Send Adapter Synchronous Mode</span></span>](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-synchronous-mode.md)  
  
-   [<span data-ttu-id="2a5c3-120">SWIFT 傳送配接器的終止</span><span class="sxs-lookup"><span data-stu-id="2a5c3-120">SWIFT Send Adapter Termination</span></span>](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-termination.md)