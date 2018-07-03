---
title: 移動非 BAM 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9e548e72-db0e-4f07-a07a-8d210425dfa5
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b9038e443784ae0f2839c2656f62131e9a0fdfa
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011375"
---
# <a name="moving-non-bam-databases"></a><span data-ttu-id="c1517-102">移動非 BAM 資料庫</span><span class="sxs-lookup"><span data-stu-id="c1517-102">Moving Non-BAM Databases</span></span>
<span data-ttu-id="c1517-103">您可以使用此程序，將主要的 BizTalk Server 資料庫移到另一部伺服器。</span><span class="sxs-lookup"><span data-stu-id="c1517-103">You can use this procedure to move the primary BizTalk Server databases to another server.</span></span> <span data-ttu-id="c1517-104">這個相同的基本程序也可用來從本機的 SQL Server 移動 BizTalk Server 資料庫，到遠端的 SQL Server 或 SQL Server 叢集。</span><span class="sxs-lookup"><span data-stu-id="c1517-104">This same basic procedure can also be used to move the BizTalk Server databases from a local SQL Server to a remote SQL Server or to a SQL Server cluster.</span></span> <span data-ttu-id="c1517-105">本節說明如何移動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不相關的 BAM 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c1517-105">This section describes how to move the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases that are not BAM related.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1517-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="c1517-106">In This Section</span></span>  
 <span data-ttu-id="c1517-107">若要移動非 BAM 資料庫遵循本主題中的步驟[如何將 BizTalk Server 資料庫移](http://go.microsoft.com/fwlink/?LinkId=210646)(<http://go.microsoft.com/fwlink/?LinkId=210646>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="c1517-107">To move the non BAM databases follow the steps in the topic [How to Move the BizTalk Server Databases](http://go.microsoft.com/fwlink/?LinkId=210646) (<http://go.microsoft.com/fwlink/?LinkId=210646>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] help.</span></span>  
  
 <span data-ttu-id="c1517-108">本章節也包含描述必須遵循之後移動特定的程序主題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫。</span><span class="sxs-lookup"><span data-stu-id="c1517-108">This section also contains a topic that describes procedures that must be followed after moving particular [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases.</span></span> <span data-ttu-id="c1517-109">完成您的環境適用的主題中的步驟。</span><span class="sxs-lookup"><span data-stu-id="c1517-109">Complete the steps in the topic as appropriate for your environment.</span></span>  
  
-   [<span data-ttu-id="c1517-110">如果未移動 MessageBox 資料庫，但移動追蹤資料庫時的考量</span><span class="sxs-lookup"><span data-stu-id="c1517-110">Considerations When Moving the Tracking Database if the MessageBox Database Is Not Being Moved</span></span>](../technical-guides/before-you-move-the-tracking-database-if-messagebox-database-is-not-moving.md)