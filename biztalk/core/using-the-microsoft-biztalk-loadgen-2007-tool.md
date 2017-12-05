---
title: "使用 Microsoft BizTalk LoadGen 2007 工具 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d1973a26-1c98-4261-bd9a-6357cdb19ccf
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2dcf55b2371387ffd52139724d74a118d52ce999
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="using-the-microsoft-biztalk-loadgen-2007-tool"></a><span data-ttu-id="c1e60-102">使用 Microsoft BizTalk LoadGen 2007 工具</span><span class="sxs-lookup"><span data-stu-id="c1e60-102">Using the Microsoft BizTalk LoadGen 2007 Tool</span></span>
<span data-ttu-id="c1e60-103">Microsoft BizTalk LoadGen 2007 工具是專門為開發人員及 IT 專業人員模擬 BizTalk Server 上的負載所設計。</span><span class="sxs-lookup"><span data-stu-id="c1e60-103">The Microsoft BizTalk LoadGen 2007 Tool is intended for developers and IT professionals to simulate load on a BizTalk Server.</span></span> <span data-ttu-id="c1e60-104">使用此工具，您就可以模擬工具效能的負載以及 BizTalk 部署的負荷。</span><span class="sxs-lookup"><span data-stu-id="c1e60-104">Using this tool, you can simulate load to instrument performance and stress against a BizTalk deployment.</span></span> <span data-ttu-id="c1e60-105">此外，開發人員還可以擴充此工具，以模擬自訂傳輸的負載。</span><span class="sxs-lookup"><span data-stu-id="c1e60-105">In addition, this tool may also be extended by developers to simulate load for custom transports.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1e60-106">下載[LoadGen](https://www.microsoft.com/download/details.aspx?id=14925)。</span><span class="sxs-lookup"><span data-stu-id="c1e60-106">Download [LoadGen](https://www.microsoft.com/download/details.aspx?id=14925).</span></span> 
  
 <span data-ttu-id="c1e60-107">此工具只能用於測試環境，不應使用於生產環境。</span><span class="sxs-lookup"><span data-stu-id="c1e60-107">This tool should be used in a test environment only, and should not be used in a production environment.</span></span> <span data-ttu-id="c1e60-108">此工具是以「現況」提供，所以並不支援。</span><span class="sxs-lookup"><span data-stu-id="c1e60-108">This tool is provided "as-is" and is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1e60-109">您可以使用 BizTalk Server 負載產生工具搭配 MSMQ 配接器，但您必須執行一些額外的步驟。</span><span class="sxs-lookup"><span data-stu-id="c1e60-109">You can use BizTalk Server Load Generation Tool with the MSMQ adapter, but you must do some additional steps.</span></span> <span data-ttu-id="c1e60-110">如需指示，請參閱[搭配 MSMQ 使用 LoadGen 2007](../core/using-loadgen-2007-with-msmq.md)。</span><span class="sxs-lookup"><span data-stu-id="c1e60-110">For instructions, see [Using LoadGen 2007 with MSMQ](../core/using-loadgen-2007-with-msmq.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1e60-111">在 64 位元電腦上可能不支援 LoadGen。</span><span class="sxs-lookup"><span data-stu-id="c1e60-111">LoadGen may not be supported on 64-bit computers.</span></span> <span data-ttu-id="c1e60-112">您可以使用在 32 位元遠端電腦上執行的 LoadGen，針對 64 位元伺服器產生負載。</span><span class="sxs-lookup"><span data-stu-id="c1e60-112">You can use LoadGen remotely running on a 32-bit computer to generate load against a 64-bit server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1e60-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="c1e60-113">See Also</span></span>  
 [<span data-ttu-id="c1e60-114">加速負載測試</span><span class="sxs-lookup"><span data-stu-id="c1e60-114">Overdrive Load Test</span></span>](../core/overdrive-load-test.md)