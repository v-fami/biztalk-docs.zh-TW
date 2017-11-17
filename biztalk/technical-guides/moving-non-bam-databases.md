---
title: "移動非 BAM 資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e548e72-db0e-4f07-a07a-8d210425dfa5
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c836840fef8b49cb907e7ac039612c68c1f6fd6c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="moving-non-bam-databases"></a><span data-ttu-id="b6273-102">移動非 BAM 資料庫</span><span class="sxs-lookup"><span data-stu-id="b6273-102">Moving Non-BAM Databases</span></span>
<span data-ttu-id="b6273-103">您可以使用此程序將主要 BizTalk Server 資料庫移動到另一部伺服器。</span><span class="sxs-lookup"><span data-stu-id="b6273-103">You can use this procedure to move the primary BizTalk Server databases to another server.</span></span> <span data-ttu-id="b6273-104">這個相同的基本程序也可用來從本機 SQL Server 移動 BizTalk Server 資料庫，遠端的 SQL server 或 SQL Server 叢集。</span><span class="sxs-lookup"><span data-stu-id="b6273-104">This same basic procedure can also be used to move the BizTalk Server databases from a local SQL Server to a remote SQL Server or to a SQL Server cluster.</span></span> <span data-ttu-id="b6273-105">本章節描述如何移動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不相關的 BAM 資料庫。</span><span class="sxs-lookup"><span data-stu-id="b6273-105">This section describes how to move the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases that are not BAM related.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b6273-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="b6273-106">In This Section</span></span>  
 <span data-ttu-id="b6273-107">若要移動非 BAM 資料庫遵循本主題中的步驟[如何移動 BizTalk Server 資料庫](http://go.microsoft.com/fwlink/?LinkId=210646)(http://go.microsoft.com/fwlink/?LinkId=210646) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="b6273-107">To move the non BAM databases follow the steps in the topic [How to Move the BizTalk Server Databases](http://go.microsoft.com/fwlink/?LinkId=210646) (http://go.microsoft.com/fwlink/?LinkId=210646) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] help.</span></span>  
  
 <span data-ttu-id="b6273-108">本章節也包含描述移動特定之後必須遵循的程序主題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。</span><span class="sxs-lookup"><span data-stu-id="b6273-108">This section also contains a topic that describes procedures that must be followed after moving particular [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.</span></span> <span data-ttu-id="b6273-109">完成本主題適用於您的環境中的步驟。</span><span class="sxs-lookup"><span data-stu-id="b6273-109">Complete the steps in the topic as appropriate for your environment.</span></span>  
  
-   [<span data-ttu-id="b6273-110">如果未移動 MessageBox 資料庫移動 「 追蹤 」 資料庫時的考量</span><span class="sxs-lookup"><span data-stu-id="b6273-110">Considerations When Moving the Tracking Database if the MessageBox Database Is Not Being Moved</span></span>](../technical-guides/before-you-move-the-tracking-database-if-messagebox-database-is-not-moving.md)