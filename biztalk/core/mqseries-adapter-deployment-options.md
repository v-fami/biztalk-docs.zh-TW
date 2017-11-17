---
title: "MQSeries 配接器部署選項 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, deploying
- deploying, MQSeries adapters
ms.assetid: d9380aff-40ea-419b-88e2-1e2ec3f023cb
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b88fa674c38df8b31c1954234846fd3939ed8568
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="mqseries-adapter-deployment-options"></a><span data-ttu-id="92054-102">MQSeries 配接器部署選項</span><span class="sxs-lookup"><span data-stu-id="92054-102">MQSeries Adapter Deployment Options</span></span>
<span data-ttu-id="92054-103">MQSeries 配接器讓您在設定硬體方面有很大的彈性。</span><span class="sxs-lookup"><span data-stu-id="92054-103">The MQSeries adapter gives you great flexibility in configuring your hardware.</span></span> <span data-ttu-id="92054-104">至少有三種主要的使用模式：</span><span class="sxs-lookup"><span data-stu-id="92054-104">There are at least three main patterns of use:</span></span>  
  
-   <span data-ttu-id="92054-105">BizTalk Server、配接器和 MQSeries Server for Windows 都在同一部電腦上。</span><span class="sxs-lookup"><span data-stu-id="92054-105">BizTalk Server, the adapter, and MQSeries Server for Windows on the same computer.</span></span>  
  
-   <span data-ttu-id="92054-106">BizTalk Server 和配接器在第一部電腦上，MQSeries Server for Windows (包括 MQSAgent) 在第二部電腦上，連接至執行 MQSeries Server 的一或多部其他電腦。</span><span class="sxs-lookup"><span data-stu-id="92054-106">BizTalk Server and the adapter on one computer, and MQSeries Server for Windows (including the MQSAgent) on a second computer, which connects to one or more additional computers that are running MQSeries Server.</span></span>  
  
-   <span data-ttu-id="92054-107">群組中安裝多部 BizTalk Server 與配接器在一部電腦上，MQSeries Server (包括 MQSAgent) 安裝在另一部電腦上。</span><span class="sxs-lookup"><span data-stu-id="92054-107">Multiple BizTalk Server installations in a group and the adapter, and MQSeries Server (including MQSAgent) on a separate computer.</span></span>  
  
-   <span data-ttu-id="92054-108">若您將 MQSeries Server 與 MQSeries 佇列管理員叢集，配接器可以正常運作。</span><span class="sxs-lookup"><span data-stu-id="92054-108">The adapter functions correctly if you cluster MQSeries Server and the MQSeries Queue Managers.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="92054-109">在此情況下，不應將 MQSAgent COM+ 應用程式叢集。</span><span class="sxs-lookup"><span data-stu-id="92054-109">The MQSAgent COM+ application should not be clustered in this case.</span></span> <span data-ttu-id="92054-110">而是叢集的兩個節點應該安裝和設定 MQSAgent COM+ 應用程式。</span><span class="sxs-lookup"><span data-stu-id="92054-110">Instead, both nodes of the cluster should have the MQSAgent COM+ application installed and configured.</span></span> <span data-ttu-id="92054-111">在此狀況下，若 COM+ 應用程式停止，則用戶端的下次呼叫將會重新啟動它。</span><span class="sxs-lookup"><span data-stu-id="92054-111">In this scenario, if the MQSAgent COM+ application stops, the next call from the client will restart it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92054-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92054-112">See Also</span></span>  
 [<span data-ttu-id="92054-113">使用 MQSeries 配接器</span><span class="sxs-lookup"><span data-stu-id="92054-113">Using the MQSeries Adapter</span></span>](../core/using-the-mqseries-adapter.md)