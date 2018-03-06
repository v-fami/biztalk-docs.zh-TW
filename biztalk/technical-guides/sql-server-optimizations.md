---
title: "SQL Server 最佳化 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb735b54-595e-4dd0-9e4d-9a5e7a007a78
caps.latest.revision: 
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36317d99387fde1d7b5e1c56b45255129daedb25
ms.sourcegitcommit: 32f380810b90b70e5df7be72a6a14988a747868e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="sql-server-optimizations"></a><span data-ttu-id="1b157-102">SQL Server 最佳化</span><span class="sxs-lookup"><span data-stu-id="1b157-102">SQL Server Optimizations</span></span>
<span data-ttu-id="1b157-103">BizTalk Server 是極資料庫密集的應用程式可能需要建立的 SQL Server 中的多達 13 個資料庫。</span><span class="sxs-lookup"><span data-stu-id="1b157-103">BizTalk Server is an extremely database intensive application that may require the creation of up to 13 databases in SQL Server.</span></span> <span data-ttu-id="1b157-104">因為 BizTalk server 的主要設計目標之一是為了確保任何訊息都會遺失，BizTalk Server 會保存到磁碟的資料很棒的頻率和此外，這樣做，MSDTC 交易的內容中。</span><span class="sxs-lookup"><span data-stu-id="1b157-104">Because one of the primary design goals of BizTalk Server is to ensure that no messages are lost, BizTalk Server persists data to disk with great frequency and furthermore, does so within the context of an MSDTC transaction.</span></span> <span data-ttu-id="1b157-105">因此，資料庫效能極為重要的任何 BizTalk Server 解決方案的整體效能。</span><span class="sxs-lookup"><span data-stu-id="1b157-105">Therefore, database performance is paramount to the overall performance of any BizTalk Server solution.</span></span>  
  
<span data-ttu-id="1b157-106">本章節描述一般的方法最大化的 SQL Server 效能，以及資料庫效能最大化 BizTalk Server 環境專用的方法。</span><span class="sxs-lookup"><span data-stu-id="1b157-106">This section describes general methods for maximizing SQL Server performance as well as methods for maximizing database performance that are specific to a BizTalk Server environment.</span></span> <span data-ttu-id="1b157-107">下列連結也是很好的資源：</span><span class="sxs-lookup"><span data-stu-id="1b157-107">The following links are also good resources:</span></span> 

- [<span data-ttu-id="1b157-108">BizTalk Server： 安裝、 調整大小、 部署和維護解決方案的建議</span><span class="sxs-lookup"><span data-stu-id="1b157-108">BizTalk Server: Recommendations for Installing, Sizing, Deploying, and Maintaining a Solution</span></span>](https://social.technet.microsoft.com/wiki/contents/articles/666.biztalk-server-recommendations-for-installing-sizing-deploying-and-maintaining-a-solution.aspx)

- [<span data-ttu-id="1b157-109">BizTalk Server 效能最佳化指南</span><span class="sxs-lookup"><span data-stu-id="1b157-109">BizTalk Server Performance Optimization Guide</span></span>](biztalk-server-2013-performance-optimization-guide.md)

  
## <a name="next-steps"></a><span data-ttu-id="1b157-110">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="1b157-110">Next steps</span></span>
  
-   [<span data-ttu-id="1b157-111">預先設定資料庫最佳化</span><span class="sxs-lookup"><span data-stu-id="1b157-111">Pre-Configuration Database Optimizations</span></span>](../technical-guides/pre-configuration-database-optimizations1.md)  
  
-   [<span data-ttu-id="1b157-112">後置設定資料庫最佳化</span><span class="sxs-lookup"><span data-stu-id="1b157-112">Post-Configuration Database Optimizations</span></span>](../technical-guides/post-configuration-database-optimizations1.md)  
  
-   [<span data-ttu-id="1b157-113">最佳化資料庫的檔案群組</span><span class="sxs-lookup"><span data-stu-id="1b157-113">Optimizing Filegroups for the Databases</span></span>](../technical-guides/optimizing-filegroups-for-the-databases1.md)