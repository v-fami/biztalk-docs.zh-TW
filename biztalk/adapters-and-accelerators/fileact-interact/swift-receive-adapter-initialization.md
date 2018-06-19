---
title: SWIFT 接收配接器初始化 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ce53aff3-6189-4033-b318-d703037518e0
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35ed17325252f1954f20cb25f963a5bd7a57d5e8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22224198"
---
# <a name="swift-receive-adapter-initialization"></a><span data-ttu-id="89d5c-102">SWIFT 接收配接器初始化</span><span class="sxs-lookup"><span data-stu-id="89d5c-102">SWIFT Receive Adapter Initialization</span></span>
<span data-ttu-id="89d5c-103">SWIFT 伺服器應用程式的初始化程序是類似於 SWIFT 的用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="89d5c-103">The initialization process for the SWIFT server application is similar to that for the SWIFT client application.</span></span> <span data-ttu-id="89d5c-104">初始化引數會當做命令列參數傳遞至接收者可執行檔。</span><span class="sxs-lookup"><span data-stu-id="89d5c-104">The initialization arguments are passed as command line parameters to the receiver executable.</span></span> <span data-ttu-id="89d5c-105">應用程式名稱、 設定接收位置中，在設計期間，會傳遞做為命令列引數。</span><span class="sxs-lookup"><span data-stu-id="89d5c-105">The application name, configured in the receive location during design time, is passed as a command line argument.</span></span> <span data-ttu-id="89d5c-106">此應用程式名稱用來建構接收位置 URI 來擷取設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="89d5c-106">This application name is used to construct the receive location URI to retrieve the configured properties.</span></span>  
  
 <span data-ttu-id="89d5c-107">使用命令列引數的相關資訊，請參閱 「 如何以設定接收配接器環境 」 中的主題 Microsoft[!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)]安裝和設定指南。</span><span class="sxs-lookup"><span data-stu-id="89d5c-107">For information about using the command line argument, see the "How to Configure the Receive Adapter Environment" topic in Microsoft [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] Installation and Configuration Guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89d5c-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89d5c-108">See Also</span></span>  
 <span data-ttu-id="89d5c-109">[SWIFT 接收配接器架構](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="89d5c-109">[SWIFT Receive Adapter Architecture](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md) </span></span>  
 <span data-ttu-id="89d5c-110">[SWIFT 接收配接器 URI](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-uri.md) </span><span class="sxs-lookup"><span data-stu-id="89d5c-110">[SWIFT Receive Adapter URI](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-uri.md) </span></span>  
 <span data-ttu-id="89d5c-111">[SWIFT 接收配接器的安全性內容](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-security-context.md) </span><span class="sxs-lookup"><span data-stu-id="89d5c-111">[SWIFT Receive Adapter Security Context](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-security-context.md) </span></span>  
 <span data-ttu-id="89d5c-112">[SWIFT 接收配接器同步與延遲模式](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-synchronous-and-deferred-modes.md) </span><span class="sxs-lookup"><span data-stu-id="89d5c-112">[SWIFT Receive Adapter Synchronous and Deferred Modes](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-synchronous-and-deferred-modes.md) </span></span>  
 [<span data-ttu-id="89d5c-113">SWIFT 接收配接器儲存與轉送</span><span class="sxs-lookup"><span data-stu-id="89d5c-113">SWIFT Receive Adapter Store and Forward</span></span>](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-store-and-forward.md)