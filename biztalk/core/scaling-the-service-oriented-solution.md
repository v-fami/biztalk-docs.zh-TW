---
title: 擴充服務導向解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scaling, service solutions
- service solution tutorial, scaling
ms.assetid: 6c22a68d-03e7-4174-b612-0e2246aa9413
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3026664d3a365630c93bf1c61d7cf635fdd9dc31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22269174"
---
# <a name="scaling-the-service-oriented-solution"></a><span data-ttu-id="c7e6a-102">擴充服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="c7e6a-102">Scaling the Service Oriented Solution</span></span>
<span data-ttu-id="c7e6a-103">若要在維持較低的訊息延遲時擴充解決方案以支援更高的輸送量，您必須使用解決方案的內嵌版本。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-103">To scale the solution to support higher throughput while maintaining low message latency requires you to use the inline version of the solution.</span></span> <span data-ttu-id="c7e6a-104">內嵌解決方案在與後端系統互動時會略過 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-104">The inline solution bypasses the MessageBox database when interacting with the back-end systems.</span></span>  
  
 <span data-ttu-id="c7e6a-105">您也可以新增 BizTalk Server 處理伺服器以執行協調流程。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-105">You can also add BizTalk Server processing servers to run orchestrations.</span></span> <span data-ttu-id="c7e6a-106">如此可降低各個伺服器的使用率，以便快速處理新的要求。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-106">This decreases the utilization of each server so that new requests can be processed quickly.</span></span> <span data-ttu-id="c7e6a-107">您也可以擴大 MessageBox 伺服器，以便有足夠的額外容量來處理訊息輸送量。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-107">You can also scale up the MessageBox server so that it has enough additional capacity to handle the message throughput.</span></span>  
  
 <span data-ttu-id="c7e6a-108">不過，對服務導向架構解決方案而言，擁有多個 MessageBox 資料庫，並沒有好處。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-108">However, the service oriented architecture solution does not benefit from having multiple MessageBox databases.</span></span> <span data-ttu-id="c7e6a-109">多個 MessageBox 需要分散式交易協調器 (DTC) 交易。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-109">Multiple MessageBoxes require distributed transaction coordinator (DTC) transactions.</span></span> <span data-ttu-id="c7e6a-110">這些交易會增加整體訊息延遲。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-110">The transactions increase overall message latency.</span></span>  
  
 <span data-ttu-id="c7e6a-111">您可以藉由排除新增 MQSeries 標頭資訊的管線元件，以降低回應時間。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-111">You can decrease response time by eliminating the pipeline component that adds MQSeries header information.</span></span> <span data-ttu-id="c7e6a-112">如需詳細資訊，請參閱[服務導向解決方案的實作重點](../core/implementation-highlights-of-the-service-oriented-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="c7e6a-112">For more information, see [Implementation Highlights of the Service Oriented Solution](../core/implementation-highlights-of-the-service-oriented-solution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7e6a-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7e6a-113">See Also</span></span>  
 [<span data-ttu-id="c7e6a-114">開發服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="c7e6a-114">Developing a Service Oriented Solution</span></span>](../core/developing-a-service-oriented-solution.md)