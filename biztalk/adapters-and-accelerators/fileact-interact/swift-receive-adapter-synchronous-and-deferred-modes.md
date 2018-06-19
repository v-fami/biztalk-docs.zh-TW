---
title: SWIFT 接收配接器同步與延遲模式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 704def2c-ac82-4cdb-9354-609cc8dc1a0d
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f85617a75cfbbb7473874760d99d6c550ab2f8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224814"
---
# <a name="swift-receive-adapter-synchronous-and-deferred-modes"></a><span data-ttu-id="de5cc-102">SWIFT 接收配接器同步與延遲模式</span><span class="sxs-lookup"><span data-stu-id="de5cc-102">SWIFT Receive Adapter Synchronous and Deferred Modes</span></span>
<span data-ttu-id="de5cc-103">SWIFTNet 連結 (SNL) 伺服器應用程式可以在兩種不同模式中運作： 同步與延遲模式。</span><span class="sxs-lookup"><span data-stu-id="de5cc-103">SWIFTNet Link (SNL) server applications can operate in two different modes: synchronous and deferred mode.</span></span> <span data-ttu-id="de5cc-104">在同步模式中，伺服器應用程式會傳送商務回應傳回給用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="de5cc-104">In synchronous mode, the server application sends a business response back to the client application.</span></span> <span data-ttu-id="de5cc-105">在延遲模式中，伺服器應用程式會傳送技術通知傳回給用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="de5cc-105">In deferred mode, the server application sends a technical acknowledgement back to the client application.</span></span>  
  
 <span data-ttu-id="de5cc-106">下圖顯示序列。</span><span class="sxs-lookup"><span data-stu-id="de5cc-106">The following figure shows the sequence.</span></span>  
  
 <span data-ttu-id="de5cc-107">![接收配接器同步與延遲模式](../../adapters-and-accelerators/fileact-interact/media/2fd504f9-5ee5-4461-a354-54c8c2f33230.gif "2fd504f9-5ee5-4461-a354-54c8c2f33230")</span><span class="sxs-lookup"><span data-stu-id="de5cc-107">![Receive adapter synchronous and deferred mode](../../adapters-and-accelerators/fileact-interact/media/2fd504f9-5ee5-4461-a354-54c8c2f33230.gif "2fd504f9-5ee5-4461-a354-54c8c2f33230")</span></span>  
  
 <span data-ttu-id="de5cc-108">下圖顯示接收端的高層級表示法。</span><span class="sxs-lookup"><span data-stu-id="de5cc-108">The following figure shows a high level representation of the receive side.</span></span>  
  
 <span data-ttu-id="de5cc-109">![接收配接器實例](../../adapters-and-accelerators/fileact-interact/media/b7cfeecb-3783-432b-886e-a77961500ad5.gif "b7cfeecb-3783-432b-886e-a77961500ad5")</span><span class="sxs-lookup"><span data-stu-id="de5cc-109">![Receive adapter scenario](../../adapters-and-accelerators/fileact-interact/media/b7cfeecb-3783-432b-886e-a77961500ad5.gif "b7cfeecb-3783-432b-886e-a77961500ad5")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de5cc-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de5cc-110">See Also</span></span>  
 <span data-ttu-id="de5cc-111">[SWIFT 接收配接器架構](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="de5cc-111">[SWIFT Receive Adapter Architecture](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md) </span></span>  
 <span data-ttu-id="de5cc-112">[SWIFT 接收配接器 URI](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-uri.md) </span><span class="sxs-lookup"><span data-stu-id="de5cc-112">[SWIFT Receive Adapter URI](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-uri.md) </span></span>  
 <span data-ttu-id="de5cc-113">[SWIFT 接收配接器初始化](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-initialization.md) </span><span class="sxs-lookup"><span data-stu-id="de5cc-113">[SWIFT Receive Adapter Initialization](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-initialization.md) </span></span>  
 <span data-ttu-id="de5cc-114">[SWIFT 接收配接器的安全性內容](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-security-context.md) </span><span class="sxs-lookup"><span data-stu-id="de5cc-114">[SWIFT Receive Adapter Security Context](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-security-context.md) </span></span>  
 [<span data-ttu-id="de5cc-115">SWIFT 接收配接器儲存與轉送</span><span class="sxs-lookup"><span data-stu-id="de5cc-115">SWIFT Receive Adapter Store and Forward</span></span>](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-store-and-forward.md)