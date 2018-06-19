---
title: SWIFT 接收配接器的安全性內容 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3db2b534-db9d-4075-aaad-0974b024dc71
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b381ba9b4e0e1d53eca8e6cdd01b9770eb82372f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22223822"
---
# <a name="swift-receive-adapter-security-context"></a><span data-ttu-id="d1c9c-102">SWIFT 接收配接器的安全性內容</span><span class="sxs-lookup"><span data-stu-id="d1c9c-102">SWIFT Receive Adapter Security Context</span></span>
<span data-ttu-id="d1c9c-103">接收器配接器，不同於傳送配接器，是從 SWIFTNet 連結 (SNL/RA) 的命令提示字元 （SWIFTNet 開始） 啟動。</span><span class="sxs-lookup"><span data-stu-id="d1c9c-103">The Receiver adapter, unlike send adapter, is started from the SWIFTNet Link (SNL/RA) command prompt (SWIFTNet start).</span></span> <span data-ttu-id="d1c9c-104">SNL/RA 組態檔案 (paramconfig) 中設定接收配接器可執行檔。</span><span class="sxs-lookup"><span data-stu-id="d1c9c-104">The receive adapter executable is configured in the SNL/RA configuration file (paramconfig).</span></span> <span data-ttu-id="d1c9c-105">在啟動配接器初始化 SNL 文件庫根據命令列參數。</span><span class="sxs-lookup"><span data-stu-id="d1c9c-105">The adapter on startup initializes the SNL library based on the command line parameter.</span></span> <span data-ttu-id="d1c9c-106">組態值會快取供稍後使用。</span><span class="sxs-lookup"><span data-stu-id="d1c9c-106">The configuration values are cached for later use.</span></span>  
  
 <span data-ttu-id="d1c9c-107">下圖顯示接收配接器的安全性內容的設定。</span><span class="sxs-lookup"><span data-stu-id="d1c9c-107">The following figure shows the configuration of the receive adapter security context.</span></span>  
  
 <span data-ttu-id="d1c9c-108">![SWIFT 接收配接器的安全性內容](../../adapters-and-accelerators/fileact-interact/media/f48c7cd1-b162-45ea-9ec3-7936f61563c2.gif "f48c7cd1-b162-45ea-9ec3-7936f61563c2")</span><span class="sxs-lookup"><span data-stu-id="d1c9c-108">![SWIFT receive adapter security context](../../adapters-and-accelerators/fileact-interact/media/f48c7cd1-b162-45ea-9ec3-7936f61563c2.gif "f48c7cd1-b162-45ea-9ec3-7936f61563c2")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1c9c-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1c9c-109">See Also</span></span>  
 <span data-ttu-id="d1c9c-110">[SWIFT 接收配接器架構](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="d1c9c-110">[SWIFT Receive Adapter Architecture](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md) </span></span>  
 <span data-ttu-id="d1c9c-111">[SWIFT 接收配接器 URI](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-uri.md) </span><span class="sxs-lookup"><span data-stu-id="d1c9c-111">[SWIFT Receive Adapter URI](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-uri.md) </span></span>  
 <span data-ttu-id="d1c9c-112">[SWIFT 接收配接器初始化](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-initialization.md) </span><span class="sxs-lookup"><span data-stu-id="d1c9c-112">[SWIFT Receive Adapter Initialization](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-initialization.md) </span></span>  
 <span data-ttu-id="d1c9c-113">[SWIFT 接收配接器同步與延遲模式](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-synchronous-and-deferred-modes.md) </span><span class="sxs-lookup"><span data-stu-id="d1c9c-113">[SWIFT Receive Adapter Synchronous and Deferred Modes](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-synchronous-and-deferred-modes.md) </span></span>  
 [<span data-ttu-id="d1c9c-114">SWIFT 接收配接器儲存與轉送</span><span class="sxs-lookup"><span data-stu-id="d1c9c-114">SWIFT Receive Adapter Store and Forward</span></span>](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-store-and-forward.md)