---
title: 互動配接器端對端可靠傳遞 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac7c22f2-ee4a-4e9b-af40-da7eb58daf51
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90ca0fc7ae5872598ed9a61cd7541017a6a39667
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22222990"
---
# <a name="interact-adapter-end-to-end-reliable-delivery"></a><span data-ttu-id="4a612-102">互動配接器端對端可靠傳遞</span><span class="sxs-lookup"><span data-stu-id="4a612-102">InterAct Adapter End-to-End Reliable Delivery</span></span>
<span data-ttu-id="4a612-103">將訊息或檔案傳送給收件者中，我們建議您確認已傳遞的訊息或檔案，以及的商務交易包含在這些執行沒有更多的時間比預期。</span><span class="sxs-lookup"><span data-stu-id="4a612-103">When sending messages or files to a recipient, we recommend that you ensure that the message or file is delivered, and that the business transaction(s) contained in these are executed no more times than anticipated.</span></span>  
  
 <span data-ttu-id="4a612-104">當這兩個實體互相通訊可以使用永續性儲存體 （例如，持續性的訊息導向中介軟體和使用它的介面應用程式所提供） 時，所以可以輕鬆地實作可靠的傳遞，如果通訊的方式標準化察覺到的訊息的狀態。</span><span class="sxs-lookup"><span data-stu-id="4a612-104">When both entities communicating with each other can use a persistent storage (for example, provided by a persistent message-oriented middleware and an interface application using it), it is easy to implement a reliable delivery if the way to communicate the perceived status of the message is standardized.</span></span>  
  
 <span data-ttu-id="4a612-105">下圖顯示的 E2EControl 結構的範例。</span><span class="sxs-lookup"><span data-stu-id="4a612-105">The following figure shows an example of the structure of the E2EControl.</span></span>  
  
 <span data-ttu-id="4a612-106">![結束 &#45; 若要 &#45; 結束控制項](../../adapters-and-accelerators/fileact-interact/media/63e39b43-118e-4572-9d75-21770253a1ee.gif "63e39b43-118e-4572-9d75-21770253a1ee")</span><span class="sxs-lookup"><span data-stu-id="4a612-106">![End&#45;to&#45;end control](../../adapters-and-accelerators/fileact-interact/media/63e39b43-118e-4572-9d75-21770253a1ee.gif "63e39b43-118e-4572-9d75-21770253a1ee")</span></span>  
  
 <span data-ttu-id="4a612-107">下圖所示的範例中的項目是 SwInt:Request 內傳送，並傳遞至接收應用程式 SwInt:RequestHandle 內不變。</span><span class="sxs-lookup"><span data-stu-id="4a612-107">The element in the example shown in the figure is sent within the SwInt:Request and delivered unchanged within the SwInt:RequestHandle to the receiving application.</span></span> <span data-ttu-id="4a612-108">行 02 可讓您將指派給要求的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="4a612-108">Line 02 allows assigning a unique identifier to the request.</span></span> <span data-ttu-id="4a612-109">以相同的要求每個後續重新傳輸重複這個唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="4a612-109">This unique identifier is repeated in each subsequent re-transmission of the same request.</span></span>  
  
 <span data-ttu-id="4a612-110">建構這個識別項的方法，則會留給實施者，但通常根據系統呼叫，例如 uuidgen()，或者可能是運算 sha-1 上傳送要求的結果 （帶有前置詞的 Sw:MsgId 與然後取代它藉由 base64 編碼的 sha-1 s置於雙引號）。</span><span class="sxs-lookup"><span data-stu-id="4a612-110">The way this identifier is constructed is left to the implementer, but typically it is based on a system call such as uuidgen(), or it may be the result of computing a SHA-1 on the request to be sent (with a prefixed Sw:MsgId and then replace it by the base64 encoded SHA-1 string).</span></span> <span data-ttu-id="4a612-111">主要的需求是全域唯一 （使用非常高的機率）。</span><span class="sxs-lookup"><span data-stu-id="4a612-111">The main requirement is that it is globally unique (with a very high probability).</span></span>  
  
 <span data-ttu-id="4a612-112">Sw:CreationTime 就是建立的原始要求時間。</span><span class="sxs-lookup"><span data-stu-id="4a612-112">The Sw:CreationTime is the time of creation of the original request.</span></span> <span data-ttu-id="4a612-113">這是選擇性參數，但可以限制針對此訊息的先前通訊嘗試的最終搜尋。</span><span class="sxs-lookup"><span data-stu-id="4a612-113">It is an optional parameter, but it is useful to limit eventual searches for previous communication attempts of this message.</span></span>  
  
 <span data-ttu-id="4a612-114">項目 Sw:PDIndication 存在於，指出這是第二個或更進一步來傳輸訊息的嘗試。</span><span class="sxs-lookup"><span data-stu-id="4a612-114">The element Sw:PDIndication is present to indicate that this is a second or further attempt to transmit the message.</span></span> <span data-ttu-id="4a612-115">接收應用程式感知的 E2EControl 然後可以使用 Sw:MsgId 回尋找是否已收到的訊息。</span><span class="sxs-lookup"><span data-stu-id="4a612-115">The receiving application that is aware of the E2EControl can then use the Sw:MsgId to find back whether the message has been received or not.</span></span> <span data-ttu-id="4a612-116">選擇性 Sw:EmissionList 包含先前嘗試的時間。</span><span class="sxs-lookup"><span data-stu-id="4a612-116">The optional Sw:EmissionList contains the time of the previous attempts.</span></span> <span data-ttu-id="4a612-117">這次使用 Sw:GetDateTime 函式時，寄件者收到為本地時間 （以國際標準時間） 寄件者。</span><span class="sxs-lookup"><span data-stu-id="4a612-117">This time is the local time of the sender (in universal time) as got by the Sender when using the Sw:GetDateTime function.</span></span> <span data-ttu-id="4a612-118">再次會很有用限制搜尋。</span><span class="sxs-lookup"><span data-stu-id="4a612-118">Again this could be useful to limit searches.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a612-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a612-119">See Also</span></span>  
 <span data-ttu-id="4a612-120">[互動的配接器架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="4a612-120">[InterAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md) </span></span>  
 <span data-ttu-id="4a612-121">[InterAct 配接器元件](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md) </span><span class="sxs-lookup"><span data-stu-id="4a612-121">[InterAct Adapter Components](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md) </span></span>  
 <span data-ttu-id="4a612-122">[配接器訊息互動的商務交換](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md) </span><span class="sxs-lookup"><span data-stu-id="4a612-122">[InterAct Adapter Messages for Business Exchange](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md) </span></span>  
 <span data-ttu-id="4a612-123">[InterAct 配接器用戶端應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md) </span><span class="sxs-lookup"><span data-stu-id="4a612-123">[InterAct Adapter Client Application](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md) </span></span>  
 <span data-ttu-id="4a612-124">[InterAct 配接器伺服器應用程式](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md) </span><span class="sxs-lookup"><span data-stu-id="4a612-124">[InterAct Adapter Server Application](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md) </span></span>  
 <span data-ttu-id="4a612-125">[配接器儲存與轉送互動](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="4a612-125">[InterAct Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md) </span></span>  
 <span data-ttu-id="4a612-126">[互動的配接器安全性架構](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="4a612-126">[InterAct Adapter Security Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md) </span></span>  
 <span data-ttu-id="4a612-127">[互動的介面卡狀態監視](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md) </span><span class="sxs-lookup"><span data-stu-id="4a612-127">[InterAct Adapter Status Monitoring](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md) </span></span>  
 [<span data-ttu-id="4a612-128">互動配接器不可否認性</span><span class="sxs-lookup"><span data-stu-id="4a612-128">InterAct Adapter Non-Repudiation</span></span>](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)