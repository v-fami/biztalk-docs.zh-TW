---
title: 調整實際執行 BizTalk Server 環境 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a972b983-5ec5-4a2a-934f-b2788ccd424e
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f6dfd90864f6698c54558c65aa3a87b96c0459c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302950"
---
# <a name="scaling-a-production-biztalk-server-environment"></a><span data-ttu-id="ade22-102">調整實際執行 BizTalk Server 環境</span><span class="sxs-lookup"><span data-stu-id="ade22-102">Scaling a Production BizTalk Server Environment</span></span>
<span data-ttu-id="ade22-103">本節提供將用於執行 BizTalk Server 解決方案，負載測試結果，以及一般的觀察值和根據在實驗室中發現的建議的摘要的負載測試的實驗室環境的概觀。</span><span class="sxs-lookup"><span data-stu-id="ade22-103">This section provides an overview of the lab environment that was used to perform load testing of a BizTalk Server solution, a summary of the load test results, and general observations and recommendations based upon the findings in the lab.</span></span>  
  
 <span data-ttu-id="ade22-104">這些主題中所提供的資訊可以和應該用於做為指南調整您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="ade22-104">The information provided in these topics can and should be used as a guide for scaling your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span> <span data-ttu-id="ade22-105">除了本指南，我們建議您先完成定期負載測試的開發週期您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]應用程式。</span><span class="sxs-lookup"><span data-stu-id="ade22-105">In addition to this guidance we recommend that you complete periodic load testing throughout the development cycle of your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ade22-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="ade22-106">In This Section</span></span>  
  
-   [<span data-ttu-id="ade22-107">案例概觀</span><span class="sxs-lookup"><span data-stu-id="ade22-107">Scenario Overview</span></span>](../technical-guides/scenario-overview.md)  
  
-   [<span data-ttu-id="ade22-108">關鍵效能指標</span><span class="sxs-lookup"><span data-stu-id="ade22-108">Key Performance Indicators</span></span>](../technical-guides/key-performance-indicators.md)  
  
-   [<span data-ttu-id="ade22-109">觀察與建議</span><span class="sxs-lookup"><span data-stu-id="ade22-109">Observations and Recommendations</span></span>](../technical-guides/observations-and-recommendations.md)