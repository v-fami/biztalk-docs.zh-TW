---
title: 最佳化網路效能 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b6c3985a-48b3-489b-8fe3-3b7bfd0515f9
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8225bd082140ac1347bc99a91ea209f9d79a8bab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22299046"
---
# <a name="optimizing-network-performance"></a><span data-ttu-id="594a4-102">網路效能最佳化</span><span class="sxs-lookup"><span data-stu-id="594a4-102">Optimizing Network Performance</span></span>
<span data-ttu-id="594a4-103">在 BizTalk Server 環境中 BizTalk Server 電腦所在的 SQL Server 電腦不同，BizTalk Server 處理的每個訊息不需要透過網路通訊。</span><span class="sxs-lookup"><span data-stu-id="594a4-103">In a BizTalk Server environment where the BizTalk Server computer is separate from the SQL Server computer, each and every message processed by BizTalk Server requires communication over the network.</span></span> <span data-ttu-id="594a4-104">此通訊包括相當大的 BizTalk Server 電腦和 BizTalk MessageBox 資料庫、 BizTalk 管理資料庫、 BAM 資料庫中，與其他資料庫之間的流量。</span><span class="sxs-lookup"><span data-stu-id="594a4-104">This communication includes considerable traffic between the BizTalk Server computer and the BizTalk MessageBox database, the BizTalk Management database, the BAM databases, and other databases.</span></span> <span data-ttu-id="594a4-105">在高負載情況下，這類通訊會造成相當大的網路流量而成為瓶頸，特別是當未最佳化的網路設定、 安裝沒有足夠的網路介面卡，或沒有足夠的網路頻寬可以使用。</span><span class="sxs-lookup"><span data-stu-id="594a4-105">In high-load scenarios, this communication can result in considerable network traffic and can become a bottleneck, especially when network settings have not been optimized, not enough network interface cards are installed, or insufficient network bandwidth is available.</span></span>  
  
 <span data-ttu-id="594a4-106">本節提供改善網路效能的一般建議，並描述可以最佳化網路堆疊，以降低網路上的瓶頸的相符項目修改數個登錄項目。</span><span class="sxs-lookup"><span data-stu-id="594a4-106">This section provides some general recommendations for improving network performance and describes several registry entries that can be modified to optimize the network stack to mitigate the occurrence of bottlenecks on the network.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="594a4-107">本節中的建議事項的一些需要修改 Windows 登錄。</span><span class="sxs-lookup"><span data-stu-id="594a4-107">Some of the recommendations in this section require modifications to the Windows registry.</span></span> <span data-ttu-id="594a4-108">不正確使用登錄編輯程式可能會造成問題，需要重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="594a4-108">Incorrect use of Registry Editor may cause problems requiring you to reinstall your operating system.</span></span> <span data-ttu-id="594a4-109">您必須自行負擔使用「登錄編輯程式」的風險。</span><span class="sxs-lookup"><span data-stu-id="594a4-109">Use Registry Editor at your own risk.</span></span> <span data-ttu-id="594a4-110">如需如何備份、 還原和修改登錄的詳細資訊，請參閱 Microsoft 知識庫文章[256896，「 Windows 登錄資訊適用於進階使用者 」](http://go.microsoft.com/fwlink/?LinkId=62729) (http://go.microsoft.com/fwlink/?LinkId=62729)。</span><span class="sxs-lookup"><span data-stu-id="594a4-110">For more information about how to back up, restore, and modify the registry, see the Microsoft Knowledge Base article [256896, "Windows registry information for advanced users"](http://go.microsoft.com/fwlink/?LinkId=62729) (http://go.microsoft.com/fwlink/?LinkId=62729).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="594a4-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="594a4-111">In This Section</span></span>  
  
-   [<span data-ttu-id="594a4-112">改善網路效能的一般指導方針</span><span class="sxs-lookup"><span data-stu-id="594a4-112">General Guidelines for Improving Network Performance</span></span>](../technical-guides/general-guidelines-for-improving-network-performance.md)  
  
-   [<span data-ttu-id="594a4-113">您可以修改改善網路效能的設定</span><span class="sxs-lookup"><span data-stu-id="594a4-113">Settings that can be Modified to Improve Network Performance</span></span>](../technical-guides/settings-that-can-be-modified-to-improve-network-performance.md)  
  
## <a name="see-also"></a><span data-ttu-id="594a4-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="594a4-114">See Also</span></span>  
 [<span data-ttu-id="594a4-115">最佳化效能</span><span class="sxs-lookup"><span data-stu-id="594a4-115">Optimizing Performance</span></span>](../technical-guides/optimizing-performance.md)