---
title: 找出效能瓶頸 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance, bottlenecks
ms.assetid: d8b93243-e383-4c21-9c08-073a0d4f79be
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b63519c51fdfbe2c8d63496132dd9f2a2438dcad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="identifying-performance-bottlenecks"></a><span data-ttu-id="e1f0d-102">識別效能瓶頸</span><span class="sxs-lookup"><span data-stu-id="e1f0d-102">Identifying Performance Bottlenecks</span></span>
<span data-ttu-id="e1f0d-103">理想情況下，當系統以將近滿載的條件執行 (充分利用可用的資源) 時，便可達到維持輸送量的目標，從而降低整體擁有成本 (TCO)。</span><span class="sxs-lookup"><span data-stu-id="e1f0d-103">Ideally, when a system is running at almost full capacity (optimal utilization of available resources), sustainable throughput can be achieved, lowering total cost of ownership (TCO).</span></span>  
  
 <span data-ttu-id="e1f0d-104">當系統執行狀況不如預期時，找出問題的來源非常重要。</span><span class="sxs-lookup"><span data-stu-id="e1f0d-104">When the system does not perform as expected, it is essential to identify the source of the problem.</span></span> <span data-ttu-id="e1f0d-105">這些主題說明如何識別及解決效能瓶頸。</span><span class="sxs-lookup"><span data-stu-id="e1f0d-105">These topics explain how to identify and resolve the performance bottlenecks.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e1f0d-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="e1f0d-106">In This Section</span></span>  
  
-   [<span data-ttu-id="e1f0d-107">如何調查瓶頸</span><span class="sxs-lookup"><span data-stu-id="e1f0d-107">How to Investigate Bottlenecks</span></span>](../core/how-to-investigate-bottlenecks.md)  
  
-   [<span data-ttu-id="e1f0d-108">識別 BizTalk 層中的瓶頸</span><span class="sxs-lookup"><span data-stu-id="e1f0d-108">Identifying Bottlenecks in the BizTalk Tier</span></span>](../core/identifying-bottlenecks-in-the-biztalk-tier.md)  
  
-   [<span data-ttu-id="e1f0d-109">如何識別 MessageBox 資料庫中的瓶頸</span><span class="sxs-lookup"><span data-stu-id="e1f0d-109">How to Identify Bottlenecks in the MessageBox Database</span></span>](../core/how-to-identify-bottlenecks-in-the-messagebox-database2.md)

- [<span data-ttu-id="e1f0d-110">如何識別 BizTalkDTADb 資料庫中的瓶頸</span><span class="sxs-lookup"><span data-stu-id="e1f0d-110">How to Identify Bottlenecks in the BizTalkDTADb Database</span></span>](../core/how-to-identify-bottlenecks-in-the-biztalkdtadb-database.md)

- [<span data-ttu-id="e1f0d-111">如何識別 BAM 資料庫中的瓶頸</span><span class="sxs-lookup"><span data-stu-id="e1f0d-111">How to Identify Bottlenecks in the BAM Database</span></span>](../core/how-to-identify-bottlenecks-in-the-bam-database.md)

- [<span data-ttu-id="e1f0d-112">如何避免磁碟爭用</span><span class="sxs-lookup"><span data-stu-id="e1f0d-112">How to Avoid Disk Contention</span></span>](../core/how-to-avoid-disk-contention1.md)
  
-   [<span data-ttu-id="e1f0d-113">避免瓶頸的指導方針</span><span class="sxs-lookup"><span data-stu-id="e1f0d-113">Guidelines for Avoiding Bottlenecks</span></span>](../core/guidelines-for-avoiding-bottlenecks.md)