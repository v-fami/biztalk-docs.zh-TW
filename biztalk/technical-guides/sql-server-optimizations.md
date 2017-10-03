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
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3783c09b1155202ac8fe5a964d16c24d33082c26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sql-server-optimizations"></a><span data-ttu-id="b81f6-102">SQL Server 最佳化</span><span class="sxs-lookup"><span data-stu-id="b81f6-102">SQL Server Optimizations</span></span>
<span data-ttu-id="b81f6-103">BizTalk Server 是極資料庫密集的應用程式可能需要建立的 SQL Server 中的多達 13 個資料庫。</span><span class="sxs-lookup"><span data-stu-id="b81f6-103">BizTalk Server is an extremely database intensive application that may require the creation of up to 13 databases in SQL Server.</span></span> <span data-ttu-id="b81f6-104">因為 BizTalk server 的主要設計目標之一是為了確保任何訊息都會遺失，BizTalk Server 會保存到磁碟的資料很棒的頻率和此外，這樣做，MSDTC 交易的內容中。</span><span class="sxs-lookup"><span data-stu-id="b81f6-104">Because one of the primary design goals of BizTalk Server is to ensure that no messages are lost, BizTalk Server persists data to disk with great frequency and furthermore, does so within the context of an MSDTC transaction.</span></span> <span data-ttu-id="b81f6-105">因此，資料庫效能極為重要的任何 BizTalk Server 解決方案的整體效能。</span><span class="sxs-lookup"><span data-stu-id="b81f6-105">Therefore, database performance is paramount to the overall performance of any BizTalk Server solution.</span></span>  
  
 <span data-ttu-id="b81f6-106">本章節描述一般的方法最大化的 SQL Server 效能，以及資料庫效能最大化 BizTalk Server 環境專用的方法。</span><span class="sxs-lookup"><span data-stu-id="b81f6-106">This section describes general methods for maximizing SQL Server performance as well as methods for maximizing database performance that are specific to a BizTalk Server environment.</span></span> <span data-ttu-id="b81f6-107">如需有關最佳化 BizTalk 資料庫效能，請參閱在 BizTalk 資料庫最佳化 TechNet 文章[http://go.microsoft.com/fwlink/?LinkId=118001](http://go.microsoft.com/fwlink/?LinkId=118001)。</span><span class="sxs-lookup"><span data-stu-id="b81f6-107">For additional information on optimizing BizTalk database performance, see the BizTalk Database Optimization TechNet article at [http://go.microsoft.com/fwlink/?LinkId=118001](http://go.microsoft.com/fwlink/?LinkId=118001).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b81f6-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="b81f6-108">In This Section</span></span>  
  
-   [<span data-ttu-id="b81f6-109">預先設定資料庫 Optimizations1</span><span class="sxs-lookup"><span data-stu-id="b81f6-109">Pre-Configuration Database Optimizations1</span></span>](../technical-guides/pre-configuration-database-optimizations1.md)  
  
-   [<span data-ttu-id="b81f6-110">組態後資料庫 Optimizations1</span><span class="sxs-lookup"><span data-stu-id="b81f6-110">Post-Configuration Database Optimizations1</span></span>](../technical-guides/post-configuration-database-optimizations1.md)  
  
-   [<span data-ttu-id="b81f6-111">Databases1 最佳化檔案群組</span><span class="sxs-lookup"><span data-stu-id="b81f6-111">Optimizing Filegroups for the Databases1</span></span>](../technical-guides/optimizing-filegroups-for-the-databases1.md)