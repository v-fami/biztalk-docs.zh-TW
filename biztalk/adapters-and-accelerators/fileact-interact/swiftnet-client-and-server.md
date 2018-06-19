---
title: SWIFTNet 用戶端和伺服器 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 89d9f54f-af16-4f14-bbe4-8306758320d8
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ea3a1b974a26f90d03bb65675c1c4e8966720f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224654"
---
# <a name="swiftnet-client-and-server"></a><span data-ttu-id="90ded-102">SWIFTNet 用戶端和伺服器</span><span class="sxs-lookup"><span data-stu-id="90ded-102">SWIFTNet Client and Server</span></span>
<span data-ttu-id="90ded-103">SWIFT 使用規定用戶端和伺服器來描述傳送和接收。</span><span class="sxs-lookup"><span data-stu-id="90ded-103">SWIFT uses the terms client and server to describe sending and receiving.</span></span> <span data-ttu-id="90ded-104">SWIFT 的用戶端會呼叫 SWIFTNet 連結 (SNL) 透過 SWIFTNet 啟始通訊的程序。</span><span class="sxs-lookup"><span data-stu-id="90ded-104">A SWIFT client is a process that calls the SWIFTNet Link (SNL) to initiate communication over SWIFTNet.</span></span> <span data-ttu-id="90ded-105">在 BizTalk Server 中，這稱為傳送配接器。</span><span class="sxs-lookup"><span data-stu-id="90ded-105">In BizTalk Server, this is called the send adapter.</span></span> <span data-ttu-id="90ded-106">SWIFT 的伺服器是由 SNL 流量流入透過 SWIFTNet 時呼叫的程式。</span><span class="sxs-lookup"><span data-stu-id="90ded-106">A SWIFT server is a program that is called by the SNL when traffic comes in over SWIFTNet.</span></span> <span data-ttu-id="90ded-107">在 BizTalk Server 中，這稱為接收配接器。</span><span class="sxs-lookup"><span data-stu-id="90ded-107">In BizTalk Server, this is called the receive adapter.</span></span>  
  
 <span data-ttu-id="90ded-108">請勿混淆 SWIFT 的用戶端和商務用戶端與伺服器的伺服器。</span><span class="sxs-lookup"><span data-stu-id="90ded-108">Do not confuse the SWIFT client and server with the business client and server.</span></span> <span data-ttu-id="90ded-109">例如，用戶端 （組織） 會依賴伺服器 （組織） 所提供的服務。</span><span class="sxs-lookup"><span data-stu-id="90ded-109">For example, a client (organization) relies on the services provided by a server (organization).</span></span> <span data-ttu-id="90ded-110">如果伺服器 （組織） 想要與用戶端 （組織） 進行通訊，則必須使用 SNL 用戶端應用程式，才能執行這項操作，和用戶端 （組織） 必須擁有 SNL 伺服器應用程式接收連入流量。</span><span class="sxs-lookup"><span data-stu-id="90ded-110">If the server (organization) wants to initiate a communication with the client (organization), it must use an SNL client application to do so, and the client (organization) must have an SNL server application to receive the incoming traffic.</span></span> <span data-ttu-id="90ded-111">這會在下圖中說明。</span><span class="sxs-lookup"><span data-stu-id="90ded-111">This is described in the following figure.</span></span>  
  
 <span data-ttu-id="90ded-112">![用戶端與伺服器之間的 SWIFTNet 關係](../../adapters-and-accelerators/fileact-interact/media/7ad5d877-19d4-431f-9358-d5ae278cf945.gif "7ad5d877-19d4-431f-9358-d5ae278cf945")</span><span class="sxs-lookup"><span data-stu-id="90ded-112">![SWIFTNet relationship between client and server](../../adapters-and-accelerators/fileact-interact/media/7ad5d877-19d4-431f-9358-d5ae278cf945.gif "7ad5d877-19d4-431f-9358-d5ae278cf945")</span></span>  
  
 <span data-ttu-id="90ded-113">SNL 假設用戶端和伺服器應用程式是從命令提示字元啟動的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="90ded-113">SNL assumes both client and server applications are executables started from the command prompt.</span></span> <span data-ttu-id="90ded-114">它們都連結至 SNL API DLL，會與實際 SNL 執行個體處理序進行通訊。</span><span class="sxs-lookup"><span data-stu-id="90ded-114">They both link to the SNL API DLL, which communicates with the actual SNL instance process.</span></span>  
  
## <a name="snl-client-applications"></a><span data-ttu-id="90ded-115">SNL 用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="90ded-115">SNL client applications</span></span>  
 <span data-ttu-id="90ded-116">SNL 用戶端應用程式依賴 SwCall API，如下所述。</span><span class="sxs-lookup"><span data-stu-id="90ded-116">SNL client applications rely on the SwCall API described below.</span></span> <span data-ttu-id="90ded-117">就技術上來說，一般用戶端應用程式可以描述，如下所示：</span><span class="sxs-lookup"><span data-stu-id="90ded-117">Technically speaking, a typical client application can be described as follows:</span></span>  
  
```  
Main:  
  Initialize SNL API  
  Repeat  
    Call SwCall API  
  Until shutdown  
```  
  
 <span data-ttu-id="90ded-118">SNL 用戶端應用程式必須在中執行專用的處理序，因為 SNL 參考用戶端內容的處理序識別碼。</span><span class="sxs-lookup"><span data-stu-id="90ded-118">SNL client applications must run in a dedicated process, because SNL references the client context by process ID.</span></span> <span data-ttu-id="90ded-119">SNL 同步處理使用 SwCall Tuxedo 資源的呼叫。</span><span class="sxs-lookup"><span data-stu-id="90ded-119">SNL synchronizes calls that use Tuxedo resources to SwCall.</span></span> <span data-ttu-id="90ded-120">如此一來，只有單一用戶端一次可以有效地執行執行緒 SwCall。</span><span class="sxs-lookup"><span data-stu-id="90ded-120">As a result, only a single client thread at a time can effectively execute a SwCall.</span></span>  
  
 <span data-ttu-id="90ded-121">用戶端支援的同步通訊模式。</span><span class="sxs-lookup"><span data-stu-id="90ded-121">The client supports the synchronous communication mode.</span></span> <span data-ttu-id="90ded-122">這表示回應從伺服器傳回時發生 SWCall 報酬率。</span><span class="sxs-lookup"><span data-stu-id="90ded-122">This means that the return on the SWCall occurs when the response comes back from the server.</span></span> <span data-ttu-id="90ded-123">這個傳回之後，才可以執行下一步 SwCall。</span><span class="sxs-lookup"><span data-stu-id="90ded-123">The next SwCall can be performed only after this return.</span></span>  
  
## <a name="snl-server-applications"></a><span data-ttu-id="90ded-124">SNL 伺服器應用程式</span><span class="sxs-lookup"><span data-stu-id="90ded-124">SNL server applications</span></span>  
 <span data-ttu-id="90ded-125">SNL 伺服器應用程式是用戶端應用程式比稍微更為複雜。</span><span class="sxs-lookup"><span data-stu-id="90ded-125">SNL server applications are slightly more complex than the client applications.</span></span> <span data-ttu-id="90ded-126">伺服器應用程式註冊之前執行封鎖 SNL DLL 呼叫的回呼函式。</span><span class="sxs-lookup"><span data-stu-id="90ded-126">Server applications register callback functions before performing a blocking call into the SNL DLL.</span></span> <span data-ttu-id="90ded-127">就技術上來說，一般的伺服器應用程式可以描述，如下所示：</span><span class="sxs-lookup"><span data-stu-id="90ded-127">Technically speaking, a typical server application can be described as follows:</span></span>  
  
```  
Main:  
  Initialize SNL API  
  Call SwRegisterSwCallback, registering the Callback function  
  Call SwServer, block and receive callbacks  
  
Callback(Request):  
  Process Request  
  Return Response  
```  
  
 <span data-ttu-id="90ded-128">伺服器應用程式可以呼叫的回呼函式中 SwCall API。</span><span class="sxs-lookup"><span data-stu-id="90ded-128">The server application can call the SwCall API while in the callback function.</span></span> <span data-ttu-id="90ded-129">在某些情況下，它必須呼叫 SwCall 能夠產生想要的結果或回應。</span><span class="sxs-lookup"><span data-stu-id="90ded-129">In some cases it must call SwCall to be able to produce the desired result or response.</span></span> <span data-ttu-id="90ded-130">不過，伺服器應用程式可以永遠不會透過網路初始通訊。</span><span class="sxs-lookup"><span data-stu-id="90ded-130">However, a server application can never initiate a communication over the network.</span></span> <span data-ttu-id="90ded-131">伺服器應用程式不可以用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="90ded-131">A server application can never be a client application.</span></span>  
  
 <span data-ttu-id="90ded-132">在下圖中，呼叫標示**初始化**是 SNL API 初始化程序，需要多次呼叫的抽象概念。</span><span class="sxs-lookup"><span data-stu-id="90ded-132">In the following figure, the call labeled **Initialize** is an abstraction for the SNL API initialization process, which requires multiple calls.</span></span> <span data-ttu-id="90ded-133">標示為呼叫**SwCallback()** 重複數次，而且呼叫標示**SwCall()** 是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="90ded-133">The call labeled **SwCallback()** will be repeated several times, and the call labeled **SwCall()** is optional.</span></span>  
  
 <span data-ttu-id="90ded-134">![SNL 伺服器功能](../../adapters-and-accelerators/fileact-interact/media/42395775-cdbc-4e36-8b36-566caefa2aaf.gif "42395775-cdbc-4e36-8b36-566caefa2aaf")</span><span class="sxs-lookup"><span data-stu-id="90ded-134">![SNL Server functionality](../../adapters-and-accelerators/fileact-interact/media/42395775-cdbc-4e36-8b36-566caefa2aaf.gif "42395775-cdbc-4e36-8b36-566caefa2aaf")</span></span>  
  
 <span data-ttu-id="90ded-135">伺服器和 SNL API DLL 之間的所有呼叫都都標準的 C 呼叫慣例同步函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="90ded-135">All calls between the server and the SNL API DLL are standard C calling convention synchronous function calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90ded-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90ded-136">See Also</span></span>  
 <span data-ttu-id="90ded-137">[了解 FileAct 和互動的配接器架構](../../adapters-and-accelerators/fileact-interact/understanding-fileact-and-interact-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="90ded-137">[Understanding FileAct and InterAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/understanding-fileact-and-interact-adapter-architecture.md) </span></span>  
 <span data-ttu-id="90ded-138">[SWIFT 傳送配接器架構](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="90ded-138">[SWIFT Send Adapter Architecture](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-architecture.md) </span></span>  
 [<span data-ttu-id="90ded-139">SWIFT 接收配接器架構</span><span class="sxs-lookup"><span data-stu-id="90ded-139">SWIFT Receive Adapter Architecture</span></span>](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md)